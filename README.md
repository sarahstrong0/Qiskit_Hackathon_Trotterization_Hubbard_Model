# Hubbard Model Quantum Simulation Using Trotterization

## Team Members

- Peter Shanahan
  - Masters Student (Master of Quantum Science and Technology)
  - Undergraduate major: Physics
  - QIS: 3

- Sarah Strong
  - Masters student (Master of Quantum Science and Technology)
  - Undergraduate Major: Physics/Computer Science
  - QIS: 3

- Emma Hughes
  - Masters student (Master of Quantum Science and Technology)
  - Undergraduate major: Physics
  - QIS: 3

## Project Selection

We chose the advanced quantum simulation project. Whilst we don’t have any prior Qiskit experience and are only 4 weeks into the UCLA Master of Quantum Science Program, we wanted to challenge ourselves to learn as much as we could about the field we’re going into. We chose to simulate the Hubbard model. With all of us having physics backgrounds, we decided this project best suited our strengths, being able to use our physics knowledge to gain a good intuition of the physical system we were simulating.

## Project Overview

### The Hamiltonian for a Hubbard Model is defined as:
$$
H = -\sum_{ij\sigma} t_{ij} c_{i\sigma}^{\dagger} c_{j\sigma} + U \sum_{i} n_{i\uparrow} n_{i\downarrow}
$$
- t = hopping energy (kinetic)
- u = coulomb repulsion (potential)
- ij = site numbers next to each other
- sigma = spin index
- c, c† = creation and annihilation operators

### Creating a Hubbard Model in Qiskit:

We defined a simple 2-site line lattice and used the Qiskit `FermiHubbbardModel` class to define the Hamiltonian for this lattice. We used the Jordan-Wigner transformation to map this fermionic Hamiltonian to a qubit Hamiltonian. In this qubit representation, each lattice site has 2 qubits to represent its electron occupation for each spin.

### Time Evolution using Trotterization:

Since the kinetic and potential terms of the Hamiltonian do not commute, Trotterization was used to approximate the time evolution operator. By discretizing time into small steps N, we can write the time evolution operator as a product of exponential operators of each small step in time.

We used the `SuzukiTrotter` with `TrotterQRTE` built into Qiskit to perform our calculations to a higher order and then evolved the Hamiltonian over time.

### Results:

The results of this time evolution gave us the evolved state circuit from which we extracted the Statevector. We also looked at the observables to see how the energy of the system evolved over time. We explored how varying the Coulomb Repulsion (U) and Hopping Energy (t) affects these results.

#### Effects of Varying the Coulomb Repulsion Term:

With varying Coulomb repulsion, we observed energy fluctuations depending on the electrons' lattice site occupancy. Increasing repulsion showed quicker fluctuations and a higher average energy.

#### Effects of Varying the Hopping Energy Term:

By varying the hopping term coefficient `t` at constant on-site energy term `U`, we noted more frequent energy oscillations as the electron hopping rate increased, indicating that the negative hopping energy overcomes the positive energy of two electrons occupying the same lattice site.

## Documentation Used

- [Qiskit Hubbard Model](https://qiskit.org/ecosystem/nature/locale/bn_BN/stubs/qiskit_nature.second_q.hamiltonians.FermiHubbardModel.html)
- [Qiskit Trotterization Documentation](https://qiskit.org/ecosystem/algorithms/tutorials/13_trotterQRTE.html)
- [Qiskit Lattice Models Documentation](https://qiskit.org/ecosystem/nature/tutorials/10_lattice_models.html)
