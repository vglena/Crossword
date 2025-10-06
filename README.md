# 🧩 Crossword AI Solver

This project implements a **Constraint Satisfaction Problem (CSP)** solver to generate complete crossword puzzles using **backtracking search** with **arc consistency (AC-3)** and **variable/value heuristics**.

---

## 📖 Overview

The program uses two main Python files:

- **`crossword.py`** – Defines the crossword puzzle structure and variables.  
  - `Variable`: Represents a single variable in the puzzle (position, direction, length).  
  - `Crossword`: Represents the puzzle itself (height, width, structure, vocabulary, variables, overlaps).  
  - Supports neighbor detection and overlap mapping between variables.

- **`generate.py`** – Implements the AI to solve the crossword puzzle.  
  - `CrosswordCreator`: Contains methods to enforce constraints, select variables, order values, and backtrack to a solution.  
  - Functions to implement:
    - `enforce_node_consistency()`
    - `revise(x, y)`
    - `ac3(arcs=None)`
    - `assignment_complete(assignment)`
    - `consistent(assignment)`
    - `order_domain_values(var, assignment)`
    - `select_unassigned_variable(assignment)`
    - `backtrack(assignment)`

The solver works by:

1. Enforcing **node consistency** to satisfy unary constraints (length of words).  
2. Using **AC-3** to enforce **arc consistency** for binary constraints (overlaps).  
3. Applying **backtracking search** to assign words to variables while satisfying all constraints.  
4. Using heuristics:
   - Minimum Remaining Values (MRV)  
   - Degree heuristic  
   - Least Constraining Value (LCV)

---

## 🧩 File Structure

```text
crossword-ai/
│
├── crossword.py         # Puzzle definitions and variable classes
├── generate.py          # AI logic to solve crossword puzzles
├── data/                # Puzzle structure and word files
│   ├── structure0.txt
│   ├── words0.txt
│   └── ...
├── requirements.txt     # Dependencies
├── LICENSE              # MIT License
└── README.md            # Documentation (this file)
```
## ▶️ Usage

1. Clone the repository:
```python
git clone https://github.com/yourusername/crossword-ai.git
cd crossword-ai
```
2. Install dependencies:
```python
pip install -r requirements.txt
```
- Required for image output (optional): `Pillow`
3. Run the solver:
```python
python generate.py data/structure0.txt data/words0.txt
```
- Generates a solved crossword puzzle printed in the terminal or saved as an image.

## 🧩 Dependencies / Requirements
- Python 3.8 or higher
- Pillow (optional, for saving images)
Example `requirements.txt`:
```python
Pillow>=9.0.0
```
## 💡 Notes
- `CrosswordCreator` uses CSP techniques to efficiently generate solutions.
- Node consistency ensures words fit the variable length.
- Arc consistency ensures no conflicts on overlapping cells.
- Heuristics improve search efficiency:
  - MRV: Choose variable with fewest remaining valid words.
  - Degree: Break ties by selecting variable with most neighbors.
  - LCV: Choose word that eliminates the fewest options for neighbors.

## 🏁 Credits
Inspired by CS50 AI Crossword Project for constraint satisfaction and AI-based puzzle solving.
Educational purpose: demonstrates CSP techniques, backtracking search, and heuristics.

## 📄 License
```text
MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM,
DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
``
