---
title: "xorg.conf edit for external monitor use-not dual"
date: 2009-05-05
forum: Multimedia Software
---

### Post by themis on 2009-05-05
Hello,

I have a toshiba portege m200, with NVidia GeForce FX Go 5200.
I have installed 'nvidia-settings'.
I just got a new screen, and want to use it, not double monitor use.
I am on dual boot with Windows, where the new monitor works fine(Fn key). 
The Fn key doesn't work in Ubuntu.

When I try to save xorg.conf file at Nvidia configuration tool, it won't permit to write to the file.
So I copy the created xorg.conf to /etc/X11/xorg.conf manually and boot with it.

When I disable laptops monitor, it does disable the screen(good sign),
**but** when I enable the new monitor , it just shows me the nvidia logo at startup and enables the laptops monitor.


I've already started a thread in Absolute Beginner talk, 
but the thread's topic has changed, so here I am.
my other thread is [http://ubuntuforums.org/showthread.php?t=1148426&page=2](http://ubuntuforums.org/showthread.php?t=1148426&page=2)
and at post #12 the 3 xorg.conf files I've tried are shown.

Please help!!

---

### Post by themis on 2009-05-05
anyone?

I am in a really bad situation!
PLeaase!!!

---

### Post by bigbudz on 2009-05-31
try typing 'sudo nvidia-settings' in the terminal without the ''. You should be able to save your changes to /etc/X11/xorg.conf now. 

Before you do anything backup. 
Type 'cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup'

Hope that helps. 

If your laptop is your default display I don't think you should or be able to disable your default and have the secondary up.

---

### Post by themis on 2009-05-31
Hi bigbudz,

I fixed it!
I just had to change the Bios display option from
default to RGB+Analog(I think)..

Thanks anyway for checking and replying!
:)

---

