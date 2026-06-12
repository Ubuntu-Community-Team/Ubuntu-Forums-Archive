---
title: "skype...is there an ultimate solution?"
date: 2010-05-22
forum: Multimedia Software
---

### Post by abelito8 on 2010-05-22
Hi I am using Xubuntu 10.4 on an Acer Aspire One

I am very happy with it except for a concern with a number of users...I cannot talk through skype

My microphone works (I can use voice/sound record software and it will record it) but it does not work in skype


I have tried millions of things, read zillions of threads, but it does not help

I have the latest version of Alsa mixer (and anyway the mic works) and I have changed the skype settings...the only thing is that in options/sound devices I cannot choose any options for microphone and speakers, I have PulseAudio Server as default with no other options available

....

Really do not know what to do, I am keeping windows on the machine only in case I need to make an urgent call...but I would be glad to delete windows (which is a virus rather than an operating system) if only I could be sure I can use skype from linux

---

### Post by likemindead on 2010-05-27
Same problem here. On my wife's laptop, running Ubuntu 10.04, Skype is fine (as it was on my laptop before I decided to switch to Xubuntu and did a fresh install). Anyone have a fix? HALP!

P. S. -- I think the problem lies in the Xfce mixer. The GNOME one has options that allow me to change the settings I need to change. Is it possible to uninstall the Xfce one and use the GNOME one instead?

---

### Post by likemindead on 2010-05-27
I fixed it!

Just open the Mixer in Xubuntu, go down to Select Controls, add damn near everything, and put them all up to 80% or so. I'm not sure which one did the trick (there's so freaking many of 'em), but now IT WORKS! :D

---

### Post by abelito8 on 2010-05-29
Thank you, I also solved the issue but do not know how. I had to open alsa mixer (it seems I have three mixers here) and the problem is that the capture option moves down automatically...but if I keep the mixer open and I loud up every time then I can even use the in-built mic

....

mysteries of Linux

---

### Post by likemindead on 2010-10-28
This is as much a note to self as anything...

**Install all of the PulseAudio stuff!**

w00t!

---

