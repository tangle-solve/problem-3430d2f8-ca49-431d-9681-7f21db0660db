<!-- solve-problem:3430d2f8-ca49-431d-9681-7f21db0660db -->
# FPT versus W[1]

A [Tangle Solve problem](https://solve.tangle.tools/problems/3430d2f8-ca49-431d-9681-7f21db0660db).

## What is the problem?

The question is whether **FPT = W[1]** in parameterized complexity theory, instantiated (equivalently, by the W-hierarchy structure) as: does the **k-Clique** problem — given a graph G and integer k, decide whether G contains a clique of size k — admit an algorithm running in f(k) · n^O(1) time, where n = |V(G)|, k is the parameter, and f is an arbitrary computable function?

**Formal setting:** A parameterized problem L ⊆ Σ* × ℕ is **fixed-parameter tractable (FPT)** if it is decidable in f(k)·|x|^c time for some computable f and constant c. k-Clique is W[1]-complete under fpt-reductions. The W-hierarchy (W[1] ⊆ W[2] ⊆ … ⊆ XP) classifies problems believed to be strictly above FPT. The conjecture is **FPT ⊊ W[1]**, i.e., k-Clique is *not* in FPT.

**Assumptions:** The standard model is a deterministic Turing machine. Since ETH (the Exponential Time Hypothesis) already implies k-Clique has no f(k)·n^o(k) algorithm (Chen et al.), a proof of FPT ≠ W[1] requires only the failure of some fixed polynomial exponent — a weaker consequence of ETH. Note this is a complexity-theoretic separation question, so any unconditional proof must overcome the known barrier that even P ≠ NP is unproved; FPT ≠ W[1] does *not* imply P ≠ NP, but is not known to follow from it either. The two conjectures are formally incomparable, which is why this problem is interesting.

**Precise target:** Prove k-Clique ∉ FPT unconditionally, or exhibit an f(k)·n^O(1) algorithm (which would collapse W[1] to FPT and falsify ETH).

## Why does it matter?

FPT ≠ W[1] is the parameterized analogue of P ≠ NP: thousands of W[1]-hardness results (e.g., for k-Step Hamiltonian Path, Set Packing, many database and model-checking problems) are meaningless as evidence of intractability without it. A proof would supply the first unconditional lower bound against a nontrivial algorithmic class, with techniques likely to transfer to P vs NP-style separations. Practically, the answer determines whether massive-search motif detection in networks (parameterized by motif size) can ever be done with the combinatorial explosion isolated in the parameter.

## What's already known?

- **Hardness side:** k-Clique is W[1]-complete (Downey–Fellows). Under ETH, no n^o(k) algorithm exists (Chen, Huang, Kannan, S. 2005, JACM — verify exact venue). Under the Strong PLN / k-clique hypotheses, even n^(εk) bounds are conjectured, but all are conditional.
- **Algorithmic side:** k-Clique is solvable in n^(0.792k + o(k)) via fast matrix multiplication (Nesetril–Poljak; improvements by Eisenbrand–Vempala via rectangular multiplication). It trivially lies in XP (n^k). It has no polynomial kernel unless NP ⊆ coNP/poly (kernelization lower-bound machinery of Bodlaender–Downey–Fellows–Hermelin; Fortnow–Santhanam), but kernel lower bounds say nothing about FPT membership.
- **Structural results:** W[1] has complete problems (model checking first-order logic on graphs); FPT = W[1] would imply ETH fails. But no unconditional technique (diagonalization, circuit lower bounds, relativization barriers) currently separates these classes; the problem relativizes with oracles both ways (verify), so relativizing techniques cannot settle it.

## What would count as solving it?

1. **Separation (expected resolution):** A proof that no computable f and constant c exist such that k-Clique is decidable in f(k)·n^c time on a standard machine. Referee criterion: a rigorous, unconditional theorem; no unproved hardness assumption may be used.
2. **Collapse (unexpected):** An explicit algorithm for k-Clique running in f(k)·n^O(1) — this alone suffices, since k-Clique is W[1]-complete and FPT is closed under fpt-reductions.
3. **Partial credit variants:** unconditional lower bounds such as k-Clique ∉ DTIME(n^(log log n)^c) for some c > 0, or any nontrivial time hierarchy within parameterized classes, would be major progress.

## How to start

1. Read **Cygan et al., *Parameterized Algorithms* (2015), Chapter 13–15** for W[1]-hardness machinery and Chapters on ETH-based lower bounds — this gives the precise definitions and the chain ETH ⇒ no n^o(k) ⇒ (would imply) FPT ≠ W[1].
2. Read **Downey–Fellows (1999; 2nd ed. 2013), chapters on the W-hierarchy** for the original definitions and completeness of Clique via tiling/model-checking reductions.
3. Study known barrier results: does FPT vs W[1] relativize? Check whether algebraization/natural-proof-style barriers apply (this is underexplored — a genuine gap and a possible entry point).
4. Natural approach: try to prove a weak unconditional lower bound for a W[1]-complete problem (e.g., time hierarchy theorems restricted to parameterized running times f(k)·n^c, sharpening Fortnow's work on parameterized time hierarchies). Main obstacle: every current separation technique fails to reach even P vs NP.

## Key references

- R. G. Downey, M. R. Fellows, *Parameterized Complexity*, Springer, 1999. DOI: 10.1007/978-1-4612-0515-9. — Foundational monograph defining FPT, the W-hierarchy, and proving k-Clique W[1]-complete.
- M. Cygan, F. V. Fomin, Ł. Kowalik, D. Lokshtanov, D. Marx, M. Pilipczuk, M. Pilipczuk, S. Saurabh, *Parameterized Algorithms*, Springer, 2015. DOI: 10.1007/978-3-319-21275-3. — Modern textbook covering fpt-reductions, kernelization lower bounds, and ETH-based running-time lower bounds for Clique and related problems.
- J. Chen, X. Huang, I. A. Kanj, G. Xia, "On the computational hardness based on linear exponential time hypothesis," (verify exact citation) — Proves that ETH implies k-Clique has no f(k)·n^o(k) algorithm, the strongest known conditional lower bound.
- H. L. Bodlaender, R. G. Downey, M. R. Fellows, H. L. Bodlaender et al. on kernelization infeasibility (Fortnow–Santhanam 2008 as core) — Establishes no polynomial kernels for W[1]-hard problems under NP ⊆ coNP/poly; orthogonal to but often confused with FPT membership.

## Warnings

- **Do not conflate kernelization lower bounds with FPT lower bounds**: "no polynomial kernel unless NP ⊆ coNP/poly" says nothing about whether an f(k)·n^O(1) algorithm exists — a problem can be FPT yet have no polynomial kernel.
- **ETH implications only go one way**: ETH ⇒ FPT ≠ W[1]; proving the separation unconditionally is strictly harder and cannot assume ETH.
- The census phrasing "prove or refute" is genuine: logically, an FPT algorithm for Clique is possible if ETH is false; don't assume the separation is true, though it is the universal working conjecture.
- Time-hierarchy results exist within parameterized classes (e.g., Fortnow's parameterized hierarchy work, verify) but provably cannot separate W[1] from FPT directly; know why before attempting them.
- Relativization: check whether FPT = W[1] relative to some oracles — if so, relativizing proofs are dead on arrival.

---
*`ALGO-000092` · unverified*

## Acceptance guidance

1. **Separation (expected resolution):** A proof that no computable f and constant c exist such that k-Clique is decidable in f(k)·n^c time on a standard machine. Referee criterion: a rigorous, unconditional theorem; no unproved hardness assumption may be used.
2. **Collapse (unexpected):** An explicit algorithm for k-Clique running in f(k)·n^O(1) — this alone suffices, since k-Clique is W[1]-complete and FPT is closed under fpt-reductions.
3. **Partial credit variants:** unconditional lower bounds such as k-Clique ∉ DTIME(n^(log log n)^c) for some c > 0, or any nontrivial time hierarchy within parameterized classes, would be major progress.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/3430d2f8-ca49-431d-9681-7f21db0660db?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000092.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000092)
