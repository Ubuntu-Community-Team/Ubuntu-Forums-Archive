---
title: "recordmydesktop and compiz"
date: 2007-08-19
forum: Multimedia Production
---

### Post by Chymera on 2007-08-19
I have finally found how to record my desktop, but now im experiencing problems with the video quality.  The ogg's have black recktangles, about 700x600px appearing randomly on individual frames (only happens when using compiz 3d effects though). Went over the advanced options... still nothing...
Sound dosnt work either, but i don't need it anyway.

Intel Core2Quad 2.4GHz, 1GB ddr2 RAM, Nvidia GeForce7300

---

### Post by eye208 on 2007-08-20
Have you enabled "full shots at every frame"?

---

### Post by Chymera on 2007-08-20
it is auto enabled when using a composite manager, but i enabled it anyway

---

### Post by Chymera on 2007-08-22
anyone ?

---

### Post by iovar on 2007-08-22
This problem exists because the XShm/XGetImage mechanism, used
for obtaining the screenshots, is a very suboptimal solution, when it 
comes to 3d windows.

Playing with recordMyDesktop's options and changing the capture area to
something smaller can reduce the problem but it won't go away. 

The only way that I know, to fix this, is by running your compiz window 
manager in indirect rendering mode.

---

### Post by eye208 on 2007-08-22
> **iovar said:**
> This problem exists because the XShm/XGetImage mechanism, used
for obtaining the screenshots, is a very suboptimal solution, when it 
comes to 3d windows.
Yet it works very well for me when capturing machinima clips from a Second Life viewer window.

Maybe there's a video driver issue involved here?

---

### Post by iovar on 2007-08-22
> **eye208 said:**
> Yet it works very well for me when capturing machinima clips from a Second Life viewer window.

Maybe there's a video driver issue involved here?

What I know is that this behavior happens persistently on nvidia cards
with the closed driver, which as far as I understand, is Chymera's case.

The problem starts when you are requesting from the Xserver an image,
that never went through it at the first place. Some driver/card combinations
might work as expected but this kind of operation is probably out of spec.

At least that's what I think, since I haven't been able to find any
documentation on this matter.

The bottom line though, is that turning compiz to indirect rendering mode
will solve the problem.

---

### Post by Chymera on 2007-08-22
What does indirect rendering mode mean? how do i change it? will it have any side-effects?

---

### Post by iovar on 2007-08-22
> **Chymera said:**
> What does indirect rendering mode mean? 

Indirect rendering means that all the openGL commands go through
the XServer instead of being sent directly to the graphics card.
It's part of the glx specification.


> how do i change it?

This relates to how compiz is started on your machine. Generally, what is
required, is to find the startup script where compiz is called and append
the --indirect-rendering option.

>  will it have any side-effects?

Indirect-rendering is usually slower due to the requirement for a round trip
to the Xserver. In many cases though, the result might be barely noticeable.

---

### Post by Chymera on 2007-08-23
how do i find that startup script?
i have my machine run compiz --replace & on startup in order to run compiz...

---

### Post by iovar on 2007-08-23
wherever it is that you see the compiz --replace &  command, change it to
compiz --replace --indirect-rendering &

---

### Post by Chymera on 2007-08-24
i start compiz from a terminal window with that command, and entering the command you mentioned in a terminal seems to change something indeed, but does not impact the result of capture

---

### Post by iovar on 2007-08-24
If that doesn't fix it then it may be a different issue than the one I
thought it was. Sorry, I don't know what else to suggest.

---

