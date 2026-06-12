---
title: "glxgears alternative for benchmarking 3d"
date: 2009-03-28
forum: Multimedia Software
---

### Post by biji on 2009-03-28
Many people said glxgears is really bad for benchmarking, how about change it to glblur? command line is simple:

/usr/lib/xscreensaver/glblur -window -fps

I got 18 fps with compiz running.. my vga is X3100 intel.. how about you?
and 32.5 fps with Failsafe Terminal Only session :D

---

### Post by akoblentz on 2009-03-29
I get 82-85 fps.
I've got a 2.66ghz Core2Duo and an NVidia 8800GTS with 320mb of ram

---

### Post by Taus on 2009-03-29
i get 82-85 too

8800gtx 512 mb ram
2.6 quad core Intel

---

### Post by cotcot on 2009-03-29
50-60 with a 7300GS

---

### Post by OutOfReach on 2009-03-29
Around 77 FPS on an NVidia GeForce 8600 GT w/ 256 MB memory on an Intel Core i7 machine. Running KDE4 w/ compositing (yay for transparent taskbars :P).

---

### Post by wolfe on 2009-03-29
90-95
amd 940 @3.8
gtx 295,


I was expecting more, I find phoronix better for benchmarking; but it was neat learning this, didn't know it existed.

---

### Post by rjl6591 on 2009-03-29
50 fps on 2.66 Core 2 Duo, 2GB RAM, Intel G965 X3000

---

### Post by biji on 2009-04-03
here is result using Jaunty :
compiz running, dualcore 64bit, Intel X3100, UXA enabled
32-34 fps :D

---

### Post by johnnyis42 on 2010-07-25
59 FPS.

I feel strange being the only ATI person here since I finally got fed up with my issues using my 9600 GT with lucid and pulled it yesterday... I was trying to find out where glxgears was hiding in lucid and stumbled on this thread.

ATI HD 3300 with restricted fglrx (dual monitors)

AMD Phenom(tm) II X4 940
8GB DDR2 800
lucid 64bit (edit) no compiz

---

### Post by Yellow Pasque on 2010-07-25
glxgears is in mesa-utils, but you probably want to run:
```
fgl_glxgears
```

---

### Post by linux18 on 2010-07-25
75 fps full screen 
compiz, kde , virtualbox, 58% max cpu frequency, blah blah blah excuses

---

