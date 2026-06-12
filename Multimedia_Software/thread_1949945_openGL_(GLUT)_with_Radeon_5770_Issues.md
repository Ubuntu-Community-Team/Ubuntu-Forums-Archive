---
title: "openGL (GLUT) with Radeon 5770 Issues"
date: 2012-03-31
forum: Multimedia Software
---

### Post by ajbelis23 on 2012-03-31
I went to AMD and got their drivers for the 5770 and installed the driver for it. I am using Ubuntu 12.04. The drivers work fine; however I am currently in a computer graphics course and tried to make a project and get this error. 

```
g++ CPE471_Lab1.cpp GLSL_helper.cpp -DGL_GLEXT_PROTOTYPES -lglut -lGL -lGLU
CPE471_Lab1.cpp:15:21: fatal error: GL/glut.h: No such file or directory
compilation terminated.
In file included from GLSL_helper.cpp:10:0:
GLSL_helper.h:16:21: fatal error: GL/glut.h: No such file or directory
compilation terminated.
make: *** [all] Error 1

```

Not really sure where to go from here.
Thanks in advance.

---

### Post by BicyclerBoy on 2012-03-31
Very likely

sudo apt-get install libglut3 libglut3-dev

will fix or get you to the next missing dependency..

---

### Post by ajbelis23 on 2012-04-01
I get this error when trying to install those packages.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libglut3
E: Unable to locate package libglut3-dev
```

---

### Post by rob1101 on 2012-04-01
Try these packages instead. 

```
sudo apt-get install freeglut3 freeglut3-dev
```

---

### Post by ajbelis23 on 2012-04-02
You are the man! Thanks buddy.

Oh how do you mark this as solved?

---

### Post by Amndeep7 on 2012-05-03
First of all, just wanted to confirm that the solution provided by rob1101 does work, i.e. installing the freeglut3 and freeglut3-dev libraries.  Also, the way you mark a thread as solved is to click on the "Thread Tools" button near the top of the thread and then click "Mark this thread as closed."

---

