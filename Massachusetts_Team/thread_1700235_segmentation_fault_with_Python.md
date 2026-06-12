---
title: "segmentation fault with Python"
date: 2011-03-04
forum: Massachusetts Team
---

### Post by kayzersuzeh on 2011-03-04
Hi, i am working on a project on C langage but i needed to know how long every step of my program is taking in milliseconds, i didn't manage to have such precision with C langage that's why i tried to embed Python code in C, anyway my code is successfully compiled but i can't execute it because of a segmentation fault and according to the gdb that's because of some function in libpython2.6.so.1.0, first i noticed that i forgot to put Py_Initialize and Py_Finalize i put them and the programm started execution and bug for the same reason, but today even with Py_Initialize and Py_Finalize i still can't execute my piece of code
can anyone help me pleaaaaaaaaaaase

---

