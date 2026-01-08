# Decision Trees — FAANG-Level Hands-On

**Goal:** Understand decision trees deeply (Gini/entropy, split selection, overfitting, pruning) and be able to explain and debug tree behavior like a FAANG ML engineer.

**Outcome:** Students can:
- compute impurity and information gain,
- implement a 1-level decision stump from scratch,
- train a sklearn DecisionTree as a sanity check,
- diagnose overfitting and data leakage risks.

---

# How to Start

1. **Fork** this repository.  
2. Open `tree_student_lab.ipynb` in **Google Colab**.  
3. Complete all **TODO** sections.  
4. **Restart runtime → Run All** cells.  
5. Push changes and submit a **Pull Request**.  

⚠️ **Do NOT edit notebooks directly on GitHub.**

---

## Lab Rules (FAANG Style)

- ✅ Be explicit about split criterion and tie-breaking
- ✅ Track train vs validation performance (overfitting)
- ✅ Prefer reproducible experiments (fixed random seed)
- ✅ Explain why a split was chosen

---

# Out of Scope

- Full tree implementation with recursion (we do a decision stump + sklearn)
- Gradient boosting (covered Day 3)

---

# Notebook Rules

- Do **NOT** rename the notebook  
- Do **NOT** delete TODOs  
- Do **NOT** hardcode outputs  
- Notebook must run **top-to-bottom**  

---

# Dataset

### Default (no download required)
- Synthetic binary classification data (with non-linear boundary)

### Optional (real dataset)
- UCI Breast Cancer Wisconsin (binary classification)

**Why real dataset later?**

- Week 4 is where we start mixing sklearn + real datasets, but we keep a synthetic fallback so notebooks always run.

---

## Section 1 — Impurity (Gini / Entropy)

### Task 1.1: Implement Gini impurity

**Checkpoint Questions:**

- Why is Gini 0 for pure nodes?
- How does class imbalance affect impurity?

---

### Task 1.2: Implement entropy

**Interview Angle:**

- Why can entropy be numerically unstable without eps?

---

## Section 2 — Best Split for a Decision Stump

### Task 2.1: Compute information gain for a threshold split

- For each feature and candidate threshold, compute weighted impurity

**FAANG Gotcha:**

- Candidate thresholds must be derived from sorted unique feature values (avoid meaningless thresholds)

---

### Task 2.2: Train a 1-level stump from scratch

- Choose (feature, threshold) that maximizes gain

**Checkpoint Questions:**

- Why do deep trees overfit?
- What is the bias–variance behavior of trees?

---

## Section 3 — sklearn Tree + Sanity Check

### Task 3.1: Train DecisionTreeClassifier

- Compare stump vs full tree
- Control `max_depth`, `min_samples_leaf`

**Interview Angle:**

- How do you prevent overfitting in trees?

---

## Section 4 — Failure Modes

### Task 4.1: Leakage-by-feature

- Create a “leaky” feature and observe inflated accuracy

**FAANG Gotcha:**

- Trees will happily learn leakage because they can memorize.

---

## Submission Expectations

- Completed notebook
- Short written answers to checkpoint questions
- Show train/val metrics for at least 3 tree settings

---

## FAANG Interview Evaluation Rubric

| Skill                         | Evaluated |
|------------------------------|-----------|
| Impurity intuition            | ✅        |
| Split reasoning               | ✅        |
| Overfitting awareness         | ✅        |
| Leakage detection             | ✅        |
| Code correctness              | ✅        |

---

## Stretch Problems (Optional)

- Implement a depth-2 tree (recursive split)
- Add cost-complexity pruning discussion (`ccp_alpha`)
- Compare Gini vs entropy on the same dataset
