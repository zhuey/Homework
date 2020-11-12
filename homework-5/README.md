# Homework-5

Homework 5 is due by 11:59 pm on Tuesday, 24 November, 2020.  It has two components to be submitted (both via GitHub pull requests):

1. A short coding example where you calculate species mass fluxes between two locations for several given state vectors.

2. Project: Derive and implement conservation of charge to model charge transfer for at least one electrode/electrolyte interface in your system (if you want to do both, that is certainly fine with me :) )

## 1. Written Assignment
You will submit a written report (as a typed pdf uploaded to Canvas) to answer the following questions/derivations:

### 1.1 Relating thermodynamics and Kinetics
In class, we discussed that there are two approaches the determining the equilibrium state for a chemical reaction - chemical kinetic equilibrim and thermodynamic equilibrium.  The kinetic equilibrium is found by setting the rate of progress equal to zero, while the thermodynamic condition is found by setting the Gibbs energy of reaction to zero. 

Obviously, the two approaches must produce the same result, and are linked to one another by the fact that both equations involve the product of species activities, raised to their stoichiometric coefficients.

Derive an expression that relates the ratio of the forward and reverse kinetic rate constants: `(k_fwd/k_rev)` to the standard-state Gibbs energy of reaction `dG^o_rxn`.  As a starting point, use the following two equations:

![](figures/deltaG_reaction.png)

![](figures/reaction_rop.png)

where the activity can be written as

![](figures/activity.png)

and the activity concentration as

![](figures/activity_conc.png)

_Pay close attention to your units!_  Your answer should look something like:

![](figures/equilibrium.png)

where the product is over all `m` phases participating in the reaction, and `k,m` are all the species `k` in the phase `m`.

### 1.2 Relating mass action kinetics and the Bulter-Volmer Form
In class, we have noted that one can model charge-transer kinetics using elementary mass-action kinetics:

![](figures/i_elementary.png)

where the forward rate constant is

![](figures/k_fwd_elementary.png)

and the reverse rate constant is 

![](figures/k_rev_elementary.png)

where `k^*` refers to the thermally-activated rate coefficient (i.e. without considering electric potential effects, such as from Arrhenius rate coefficients).

Alternatively, one could use Butler-Volmer kinetics to model a charge-transer reaction:

![](figures/i_BV.png)

Please demonstrate that these two forms are equivalent, by deriving an equation for the exchange current density `i_o`:

![](figures/i_o.png)

The first step is to use the definition of `eta`:

![](figures/eta.png)

and of `delta Phi_eq`:

![](figures/deltaPhi_eq.png)

and substitute these into your equation.  Your answer to 1.1 might come in useful, as well.

Note that you can either start with the mass-action kinetics and try to derive Butler-Volmer, or the other way around.  Or set `i_Far` equal to `i_BV` and see where that leads you...

### 1.3 Semester-long project Identification
See the semester-long project description.  Identify and describe the system that you will model.  What is the device?  What are the components made of?  What type of process will you be modeling (a particular experiment, a mode of operation/application)?  And finally, what is the question you will attempt to answer (e.g. "I want to understand the effect of microstructure on XXX" or "I want to identify the optimum pressure for running YYY'').  As described in the project assignment, provide at least one reference from the literature to demonstrate why the application is important, or preferably why the parameter you choose is important. 

Lastly, if you are working with a partner, please list their name.

## 2. Project Progress: Conservation of Charge and Charge Transfer

At a minimum, you must submit a pull request to your project repo that includes (i) a Jupyter notebook showing the derivation of your conservation of charge equation(s), and a model file (edit and rename the `_model.py` template) that implements this into a model code that I can run.

Details:
- Describe the model domain and state variables, then derive the conservation equations in a Jupyter notebook.  Implement the conservation equations to calculate a steady-state voltage difference, for a fixed external current (i_ext), and assuming that all species concentrations and all other state variables remain fixed.  
- Take your implementation from the Jupyter notebook and implement it as a python module that can be run independently.
- See my `Code-Examples` repo for [Battery SPM](https://github.com/Echem-Systems-Engineering-Fall2020/Code-Examples/tree/main/BatterySPM) and [PEMFC](https://github.com/Echem-Systems-Engineering-Fall2020/Code-Examples/tree/main/pemfc) examples, to get you started. You will eventually need to justify any parameter values (ideally via literature citations), but for now you are fine to stick with "this number worked" as your justification.  Note that while "steady state" may not be the eventual goal for your project, it is still okay to start here.
- Note that I have a particular way that I like to modularize my models (main `_model.py` file, with separate `_init.py`, `_function.py` files, etc.).  While there are obviously reasons I like this approach, you are by no means bound by it.  The only requirement is that the main file that is run ends with `_model.py`.  If you want to cram every line of code into this file, and think you can do so in a sensible way that your instructor can understand, then by all means, be my guest :).
- Both the Jupyter file and your python implementation will be submitted as a pull request to your project repo on the Echem [Projects page](https://github.com/Echem-Systems-Engineering-Fall2020/Projects).

