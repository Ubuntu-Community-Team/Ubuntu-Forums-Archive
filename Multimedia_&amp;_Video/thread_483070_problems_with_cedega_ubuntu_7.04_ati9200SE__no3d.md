---
title: "problems with cedega ubuntu 7.04 ati9200SE  no3d"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by andyc7454 on 2007-06-24
this is the secound time i'am trying to get a answer still no one can solve this
i'ts about 3d accelaration how do i enebel it on ubuntu 7.04 i have read that it is fully supported
but cannot get it supported on CEDEGA all checks i run say it is a ati card
but in CEDEGA it reads as a mesa driver hmm please help
and do not post replie if you do not know what cedega is please there must be some pro
who knows what i'am talking about ati raddon9200SE (not a mobiliy 9200SE)
open gl works fine and rendering is YES

---

### Post by Ziox on 2007-06-24
first of all, make sure that you are not running XGL.  Also, make sure that CEDEGA has support for OpenGL, or check all the options to make sure it is enabled.

fglrxinfo would be nice.

---

### Post by andyc7454 on 2007-06-24
the fglfrxinfo or what ever you mean is not iinstalled

---

### Post by andyc7454 on 2007-06-24
ok dir a frglyxinfo

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 6.5.2[/SIZE]

This is a ati 9200se agp

---

### Post by andyc7454 on 2007-06-24
display: :0.0 screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 6.5.2[/size]

ths is what cedega reads and flgyxinfo reads and cannot get 3d accelaration everything else works
fine  this is supossed to be a ATI 9200SE not mesa what ever that means
really need this issue sorted out it's the only thing bugging me at the moment
if sorted out i will stick to ubuntu
please only anwser if you no a cerlution rendering is yes and glxgears is about 3000fps:(

---

### Post by Ziox on 2007-06-24
there's your problem.  Your card isn't using its correct driver. You need to install the fglrx package.  Through the restricted driver manager.

---

### Post by andyc7454 on 2007-06-24
that still does not work it say that your driver does not need any restricted drivers

---

### Post by John.Michael.Kane on 2007-06-24
All you have posted is that your card is not working. You need to give more info.

What version of ubuntu?
What architecture 32 or 64 bit
What guide or guides did you try,if you tried any.

Did you try one of these guides. 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)


Note: If your frustrated step back from the machine take a break, and come back to the problem later.

---

### Post by andyc7454 on 2007-06-24
[SIZE="5"]It is ubuntu 7.04 i386
32 64 have no idea
its a amd sempron 2300[/SIZE]

---

### Post by andyc7454 on 2007-07-08
this forum is really  bad you ask a question and don't get a answer

---

