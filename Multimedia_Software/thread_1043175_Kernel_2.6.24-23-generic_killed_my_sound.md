---
title: "Kernel 2.6.24-23-generic killed my sound"
date: 2009-01-18
forum: Multimedia Software
---

### Post by pappo on 2009-01-18
I lost all multimedia playback when I did the latest recommended upgrade to the 2.6.24.23 kernel.  I couldn't figure it out for a while, but when I went back to my previous kernel ( 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux ) all the sound came back.

I haven't seen much on the forums about this, but then I only looked in the multimedia section.

---

### Post by Stochastic on 2009-01-19
Moved to Multimedia & Video

---

### Post by Neobuntu on 2009-01-19
Killed my sound too. ...and my nvidia driver. Only for geeks at this point.

---

### Post by tv0571 on 2009-01-26
Can you guys tell me how to upgrade/downgrade my kernel?  After I upgraded to Intrepid, I lost my sound card(s) (Nvidia and Aureal Vortex).  I suspect my kernel: 2.6.25-2-386 isn't working with Alsa.  Recompiling from latest Alsa doesn't make it through the Make step.

---

### Post by pappo on 2009-01-26
tv0571

The system normally keeps your current kernel and the previous one.
What I did was install startupmanager ( apt-get install startupmanager) first. Once you get startupmanager installed just run it:

    sudo startupmanager

You will see a GUI that has a dropdown menu for "Default operating system" and you can just select the previous one.  Then just do a normal restart.

In my case my 2.6.24-23 caused my loss of sound so I just told startupmanager to use 2.6.4.22 and "VOILA" my multimedia all returned.

Good luck

---

### Post by ovoskeuiks on 2009-04-16
You are probably just missing the required modules
run this
dpkg -l |grep linux
and look for linux-ubuntu-modules and linux-restriced-modules you'll probably find that you have the ones for the old kernel and not the new kernel

---

