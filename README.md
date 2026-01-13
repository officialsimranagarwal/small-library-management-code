# Small Library Management System 📚

![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![Persistence](https://img.shields.io/badge/Data-Binary_Serialization-blue?style=for-the-badge)
![System](https://img.shields.io/badge/Architecture-Modular-green?style=for-the-badge)

## 📖 Overview

A robust **C++ Console Application** that manages library transactions. It implements a relational data model using classes and binary file handling to simulate a real-world library's book issue/return cycle with fine calculation.

## 🏗️ Class Architecture

### `class book`
Represents the inventory assets.
-   **Attributes**: `bno` (ID), `bname` (Title), `aname` (Author).
-   **Methods**: Encapsulates CRUD operations (`create_book`, `show_book`, `modify_book`) ensuring data encapsulation.

### `class student`
Represents the library patrons.
-   **Attributes**: `admno` (Admission ID), `token` (Issue flag).
-   **Logic**: The `token` integer acts as a semaphore; `1` implies a book is checked out, blocking further issues until return.

## 💾 Data Persistence

The system uses flat-file database concepts:
-   **Files**: `book.dat` and `student.dat`.
-   **Serialization**: Objects are written directly to disk using `write((char*)&obj, sizeof(obj))`.
-   **Random Access**: Specific records are retrieved using `read()` in a while loop, checking against IDs.

## ⚙️ Business Logic

1.  **Book Issue**:
    -   Validates Student Existence AND Book Existence.
    -   Checks constraint: `if (st.rettoken() == 0)` (Student has no active dues).
    -   Updates Student's `stbno` (Student Book Number) link.
2.  **Book Deposit & Fine**:
    -   Calculates active duration.
    -   **Fine Formula**: $Fine = (Days - 15) \times 1$ (if Days > 15).

## 🚀 Execution

1.  Compile:
    ```bash
    g++ code.cpp -o library_system
    ```
2.  Run:
    ```bash
    ./library_system
    ```

## 🤝 Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## 👤 Author

**Simran Agarwal**
-   [Profile](https://github.com/officialsimranagarwal)
-   [LinkedIn](https://linkedin.com/in/simran-agarwal-54751b191)

---
*Generated with ❤️ by Simran Agarwal*
