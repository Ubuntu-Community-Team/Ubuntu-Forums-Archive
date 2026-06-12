---
title: "E-MU 0404 PCI not recognised"
date: 2011-04-05
forum: Multimedia Software
---

### Post by arcticia on 2011-04-05
Hi!

I took my first step into the world of Ubuntu, and installed Ubuntu Studio 10.10.
Problem is that ALSA does not recognise my E-MU 0404 PCI soundcard. Details: [http://www.alsa-project.org/db/?f=a341b48819cbb104224a7358b48e5b8a55181da1](http://www.alsa-project.org/db/?f=a341b48819cbb104224a7358b48e5b8a55181da1)

If I try to start alsamixer, it won't work. (file or folder does not exist)

I checked the revision of my souncard, it's [1102:0008] - according to some posts this version should be OK?

I went through first steps in "Comprehensive Sound Problems Solutions" - removing and reinstalling ALSA, but that did not help.

Any ideas? Is the next phase to try to recompile ALSA driver or is there anything else I could try?

Thanks.

---

### Post by arcticia on 2011-04-11
I moved on with the sound solutions guide - got the alsa sources through apt-get and recompiled it. Still nothing.
  
lspci finds the soundcard but ```
aplay -l
``` gives empty device list - no soundcards listed.

This is an old WinXP desktop and I still have windows on another partition - in windows my soundcard works just fine.

I tried also with Ubuntu 10.04.2 live CD, but it does not recognise my soundcard either.

Can anyone help me?

---

