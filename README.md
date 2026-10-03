# HIFE — Hierarchical Integrated Flow Electrode

### **Designing the flow environment around the chemistry**

> **Don't just choose the chemistry. Design the environment in which the chemistry works.**

---

## 🧭 Navigation

* [HIFE](#-hife)
* [Concept](#-concept)
* [Figure 2](#-figure-2)
* [Model](#-model)
* [Monte Carlo & Sensitivity](#-monte-carlo--sensitivity)
* [Results & Scope](#-results--scope)
* [Limitations](#-limitations)
* [Why Iron Flow?](#-why-iron-flow)
* [Next Steps](#-next-steps)
* [Reproducibility](#-reproducibility)
* [Project Files](#-project-files)

---

# 🔬 HIFE

**HIFE — Hierarchical Integrated Flow Electrode** is a proposed electrode architecture for aqueous iron-based redox-flow batteries.

The concept integrates multiple transport scales:

```text
Large flow channels
        ↓
Porous electrode regions
        ↓
Microscopic pathways
        ↓
Reaction surfaces
        ↓
Iron deposition
        ↓
Evolving structure
```

The central hypothesis is:

> **Electrode architecture can be designed together with flow, reaction, and evolving deposition.**

HIFE is currently a **computational and analytical research concept**, not an experimentally validated device.

---

# 💡 Concept

The current screening geometry uses:

* **3 mm porous land**
* **1 mm × 1 mm square flow channel**
* **3 mm nominal hydraulic/electrode path**
* **100 cm² cell area**

```text
┌───────────────────────────┐
│       POROUS LAND         │
│           3 mm            │
├───────────────────────────┤
│       1 mm × 1 mm         │
│       FLOW CHANNEL        │
└───────────────────────────┘
```

The objective is to investigate whether dedicated flow pathways can improve transport through porous reactive regions.

---

# 📐 Figure 2

### **Hydraulic Design-Space Screening**

![HIFE Figure 2 — Hydraulic Design-Space Screening](HIFE_Figure2_Hydraulic_MonteCarlo.png)

**Figure 2.** First-order computational screening of the proposed HIFE architecture.

| Panel | Purpose                 |
| ----- | ----------------------- |
| **A** | Design assumptions      |
| **B** | Monte Carlo uncertainty |
| **C** | Architecture comparison |
| **D** | Parameter sensitivity   |

> **Evidence status: model-based design-space evidence only.**

The figure is not experimental validation, CFD, measured permeability, or validated electrochemical performance.

---

# 🧮 Model

## Porous Region

The porous electrode is represented using a Darcy-type relationship:

**Pressure drop**

**ΔP = μLv / k**

**Permeability**

**k = d_f² ε³ / [180(1 − ε)²]**

where:

* ΔP = pressure drop
* μ = dynamic viscosity
* L = flow-path length
* v = superficial velocity
* k = permeability
* d_f = characteristic fiber diameter
* ε = porosity

The permeability relationship is a first-order Carman–Kozeny-type approximation.

---

## Square Channel

For the **1 mm × 1 mm square channel**:

**Pressure drop**

**ΔP_channel = f_D (L / D_h) (ρv² / 2)**

**Reynolds number**

**Re_Dh = ρvD_h / μ**

**Laminar square-channel relation**

**f_D Re_Dh = 56.91**

where:

* f_D = Darcy friction factor
* D_h = hydraulic diameter
* ρ = fluid density
* μ = dynamic viscosity

The value **56.91** is specific to the square-channel relation used in this screening model.

---

## Combined Architecture

The porous land and channel are represented as simplified parallel hydraulic paths.

**Effective resistance**

**R_eff = 1 / [1/R_land + 1/R_channel]**

This is a **first-order hydraulic surrogate**, not CFD.

---

# 🎲 Monte Carlo & Sensitivity

| Parameter            |  Value / Range |
| -------------------- | -------------: |
| Viscosity            | 1.5 mPa·s ±10% |
| Density              |     1000 kg/m³ |
| Porosity             |      0.88–0.92 |
| Fiber diameter       |     10 µm ±10% |
| Electrode thickness  |      3 mm ±10% |
| Screening velocity   |       0.01 m/s |
| Baseline Monte Carlo |         20,000 |
| Channel Monte Carlo  |          4,000 |
| Sensitivity samples  |          3,000 |
| Random seed          |              7 |

Sensitivity is evaluated using Pearson correlation with **log10(ΔP)**.

---

# 📊 Results & Scope

Figure 2 explores:

* hydraulic uncertainty,
* relative architecture response,
* parameter sensitivity, and
* design variables for future testing.

Panel C compares the porous baseline with the simplified channel-assisted architecture.

The curves are **independently normalized to their own medians**, so Panel C represents **relative response shape**, not absolute pump-power savings.

The current work establishes a **computational design-space baseline**.

It does not establish:

* battery efficiency,
* electrochemical performance,
* durability,
* economic performance, or
* commercial feasibility.

---

# ⚠️ Limitations

The present model does not explicitly include:

* measured electrode permeability
* compression
* entrance effects
* gas-phase behavior
* clogging
* concentration gradients
* detailed electrochemical kinetics
* transient iron morphology
* precipitation dynamics
* temperature effects
* detailed pore geometry
* stack-level flow distribution
* CFD
* experimental validation

> **Figure 2 defines a testable engineering hypothesis; experiments are required to determine whether the predicted behavior occurs in practice.**

---

# 🔋 Why Iron Flow?

Iron-based flow chemistry provides the electrochemical platform for this architectural study.

HIFE does **not** claim that iron flow batteries universally outperform lithium-ion or vanadium systems.

The research question is narrower:

> **If an aqueous iron-flow system is selected for stationary or long-duration storage, can hierarchical electrode architecture improve its transport environment?**

---

# 🧭 Next Steps

```text
Hydraulic screening
        ↓
Geometry refinement
        ↓
Experimental permeability
        ↓
Electrochemical coupling
        ↓
CFD / multiphysics
        ↓
Prototype validation
```

Future work can progressively introduce:

* realistic channel and land geometry
* measured transport properties
* spatial flow distribution
* reaction kinetics
* concentration effects
* iron deposition behavior
* evolving permeability
* higher-fidelity modeling

---

# 🔬 Reproducibility

Primary MATLAB source:

```text
HIFE_Figure2_Hydraulic_MonteCarlo.m
```

Random-number seed:

```matlab
SEED = 7;
rng(SEED,'twister');
```

Generated outputs:

```text
HIFE_Figure2_Hydraulic_MonteCarlo.png
HIFE_Figure2_Hydraulic_MonteCarlo.pdf
```

The PNG is used for GitHub and presentation display.

The PDF provides a vector version for technical documentation.

---

# 📁 Project Files

```text
HIFE/
├── README.md
├── HIFE_Figure2_Hydraulic_MonteCarlo.m
├── HIFE_Figure2_Hydraulic_MonteCarlo.png
└── HIFE_Figure2_Hydraulic_MonteCarlo.pdf
```

---

# 🎯 Core Question

> **What if we stop treating an electrode as simply a piece of porous material and start designing it as a transportation network for liquid, ions, electrons, reactions, and evolving deposits?**

### **HIFE**

**Guide the flow.**
**Expose the reaction.**
**Anticipate the deposition.**
**Design the electrode as a system.**

> **The chemistry stores the energy.
> The architecture shapes the environment.
> The model explores the design space.
> The experiment decides what is real.**

---

## 👤 Author

**Umar Tabbsum**

*HIFE — Hierarchical Integrated Flow Electrode*
*Analytical / Computational Hydraulic Design-Space Screening*
*October 2026*
