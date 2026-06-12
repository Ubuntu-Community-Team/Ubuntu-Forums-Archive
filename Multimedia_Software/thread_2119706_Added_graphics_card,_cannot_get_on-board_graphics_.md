---
title: "Added graphics card, cannot get on-board graphics to drive second monitor"
date: 2013-02-24
forum: Multimedia Software
---

### Post by pg1993 on 2013-02-24
I am trying to set up dual monitors on my 12.04 desktop.  I have added a GeForce 210 card, and enabled both it and the on-board VGA in the BIOS, with the GeForce 210 set as the primary display.  The main display is a Dell running at 1280x1024, and the secondary display is an old Samsung (potentially) running at 1024x768.
Is what I am trying to do even possible (running two screens with different resolutions from effectively separate graphics cards)?
I know the second screen can display stuff, as the boot splash screen appears on it.
I tried installing the Nvidia drivers (various versions) but had such awful problems that I thought I was going to have to do a complete reinstall - the screen went blank on startup and shutdown, and in fact wouldn't shut down at all - I had to hold down the power button.  At no point when running the Nvidia drivers was the second screen detected.
So I am now running on just the default drivers.
The system seems to know about the hardware:

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

Any advice would be welcome, or even a definitive statement that what I am doing just can't be done.  I have searched the forums and can see that there have been a lot of issues with dual monitors and Nvidia drivers, but I couldn't find a solution.

---

### Post by QIII on 2013-02-24
*Moved to **Multimedia & Video***

---

