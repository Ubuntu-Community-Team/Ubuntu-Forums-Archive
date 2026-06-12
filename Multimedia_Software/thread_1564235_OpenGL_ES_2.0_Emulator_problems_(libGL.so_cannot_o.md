---
title: "OpenGL ES 2.0 Emulator problems (libGL.so: cannot open shared object file: No such f)"
date: 2010-08-30
forum: Multimedia Software
---

### Post by kstueve on 2010-08-30
I am trying to run a simple cube OpenGL ES demo.

I am using the user guide for the OpenGL ES 2.0 Emulator at [http://www.malideveloper.com/files/DUI0511C_opengl_es_2_0_emulator_ug.pdf](http://www.malideveloper.com/files/DUI0511C_opengl_es_2_0_emulator_ug.pdf)

When I get to step 5 in section 3.3 and type ./cube I get the following error:
libGL.so: cannot open shared object file: No such file or directory

I have an emachines netbook with an Intel Atom processor.

Perhaps this question would better be suited for an OpenGL forum, but since I am such an Ubuntu newbie, I thought this might be more of an Ubuntu question than an OpenGL question.

:confused:

---

### Post by xxilus on 2010-08-30
did you install the OpenGL Libraries?

try this
```

sudo apt-get clean all
sudo apt-get update
sudo apt-get install freeglut3-dev

```

---

### Post by kstueve on 2010-08-30
:KSThank you very much. :D  I don't get that error anymore.  Now I get the following:

WARNING: Application calling GLX 1.3 function "glXCreateWindow" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXQueryDrawable" when GLX 1.3 is not supported!  This is an application bug!
glGetError() = 1280 (0x00000500) at line 355
:confused:
The program window pops up for a fraction of a second, but then disappears.

---

### Post by xxilus on 2010-08-30
the important first step is to just get some OpenGL code compiling.
Start with a basic openGL example code, get "Hello World" working.
then try OpenGL ES code.

---

