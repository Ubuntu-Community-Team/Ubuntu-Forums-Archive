---
title: "How to install gtkpod 2 on 10.04 ?"
date: 2011-04-16
forum: Multimedia Software
---

### Post by aiphes on 2011-04-16
hi

i've all files, but i've an error when i try to compile ..so 


[HTML]checking for make-g++... no
checking for make-c++... no
checking for make-gpp... no
checking for make-aCC... no
checking for make-CC... no
checking for make-cxx... no
checking for make-cc++... no
checking for make-cl.exe... no
checking for make-FCC... no
checking for make-KCC... no
checking for make-RCC... no
checking for make-xlC_r... no
checking for make-xlC...[/HTML]  

then :
[HTML]$ make
make: *** Pas de cibles spécifiées et aucun makefile n'a été trouvé. Arrêt.[/HTML]

whats wrong ?

thanks

---

### Post by SabreWolfy on 2011-06-11
I downloaded the latest gtkPod from [http://www.gtkpod.org](http://www.gtkpod.org) (2.0.1) and tried to compile it under Ubuntu 10.04. ./configure reported errors and I installed these packages:

intltool libgtk2.0-dev libgpod-dev

However, then ./configure reported errors with libanjuta and this is where I gave up and deleted gtkPod and purged the packages I'd installed. gtkPod uses Anjuta as it's [windowing]("http://www.gtkpod.org/wiki/2.0.0") system (?) and anjuta is not in the repos. I'm not about to install an entire IDE to compile a program. The version of gtkPod in the 10.04 repos is very old (0.99.14) which is not even mentioned on the gtkPod website.

---

