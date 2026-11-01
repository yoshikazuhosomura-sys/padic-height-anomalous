# p-adic heights at anomalous primes

Papers and Lean 4 formalisation by **Yoshikazu Hosomura**.

## Papers

| Directory | Title | Status |
|---|---|---|
| `papers/paper1-integrality` | *The p-adic height pairing at anomalous primes and points of order p over Q_p* | preprint (arXiv submission in preparation) |
| `papers/paper2-digits` | *The height matrix modulo p and the p-adic digits of the height at split anomalous primes* | companion preprint |

Main result of paper 1: for an elliptic curve E/Q and a prime p ≥ 5 of good ordinary reduction with #E(F_p) = p, p ∤ ∏c_ℓ, and E(Q)/tors → E(F_p) onto, **every entry of the cyclotomic p-adic height matrix is p-integral if and only if E(Q_p) has a point of order p**; in rank one the non-split value of v_p(Reg_p) is −1 exactly.

## Lean

Each paper has its own Lean project; files shared by both papers are duplicated.

| Directory | Modules | Contents |
|---|---|---|
| `lean/paper1-integrality` | 11 | `PadicHeightValuation{,2,…,10,22}.lean` |
| `lean/paper2-digits` | 25 | `PadicHeightValuation{2,3,8,10,11,…,29}.lean`, `PadicHeightValuationCanonical.lean`, `AnomalousEulerFactor.lean` |

- Lean 4 `v4.33.1`, Mathlib `0df444a3` (pinned in `lake-manifest.json`).
- Every module depends on `import Mathlib` only; modules do not import each other. No `sorry`, no `native_decide`.
- `axioms.txt` in each project is the `#print axioms` output of its modules; every line is a subset of `propext`, `Classical.choice`, `Quot.sound`.
- `lean/SHA256SUMS` lists the checksums of all sources.

Build one project:

```
cd lean/paper1-integrality
lake exe cache get
LEAN_NUM_THREADS=1 lake build
```

Plan for 16 GB of RAM.

**What Lean checks.** The arithmetic layer: Fermat quotients, determinant and bilinear algebra, weight and residue counts, congruences. The geometric and p-adic analytic inputs (p-adic sigma function, division polynomials, Vélu's formulas, formal groups, the Tate curve) are not in Mathlib and enter the Lean statements as hypotheses. Each paper has an appendix listing the correspondence between statements and Lean declarations.

## History

These papers are a revised version, split in two, of a draft the author published under the pen name *Kiichi* on the website [computo ergo sum](https://computoergosum.com/principia/papers/index.html) (draft v15, 2026-10-08), archived in the repository [principia](https://github.com/yoshikazuhosomura-sys/principia).

## Use of AI

The author carried out this research with the assistance of Claude Code (Anthropic). The constructions, proofs, computations and the Lean formalisation were developed with the AI system under the author's direction; independent sessions of the system were used to re-check the Lean development and the computations. The author reviewed the arguments, checked the Lean development and its axiom logs, and takes full responsibility for the content.

## License

Apache License 2.0 — see `LICENSE`.
