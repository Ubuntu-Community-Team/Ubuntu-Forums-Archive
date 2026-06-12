---
title: "How to enable nvidia-current driver"
date: 2010-09-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yumi on 2010-09-15
Have nvidia-current installed, recognises graphics card and correct resolution. But the "additional Drivers" Dialog says "This driver is activated but not currently in use". 

Quick question: How to I set Maverick to use this driver? Dialog "System - Administration - Hardware Drivers" not available.

Everything worked until todays update. Now the resolution is to small and I try to avoid to edit xorg.conf manually at first.

Michael

---

### Post by VinDSL on 2010-09-15
> **Yumi said:**
> Quick question: How to I set Maverick to use this driver?

Everything worked until todays update.[...]Well...

Today's Update (15-Sep-2010) broke my nVidia driver too.

LoL!  I was actually happy to be stuck @ Plymouth again.  Things have been going too smoothly!  :D

The problem is, I'm getting used to fixing these video snafus.  Sooo, 5 minutes later, I was back up n' running.

What I did was, (re)install the *NVIDIA-Linux-x86-256.53.run* file.

I've been running *260.19.04 beta* for the past few days.  It's been running fine, but I noticed that today's updates were not finding some of the nVidia .so files.  I'm assuming that's what screwed the pooch.

Anyway, re-installing the certified drivers (256.53) took care of the situation for me.  ;)

---

### Post by dino99 on 2010-09-15
might be a xorg.conf conflict

sudo rm -f /etc/X11/xorg.conf

then reboot

*** no problem using packages from: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Yumi on 2010-09-15
Reinstalling did not help, the nvidia settings are ok anyway. And the command returned me to a really low resolution.

It is just that I can not get the system to use the nvidia driver. Before I had a dialog under hardware drivers, but this is not there. Maybe I have to edit xorg.conf

---

### Post by VinDSL on 2010-09-15
> **Yumi said:**
> Reinstalling did not help, the nvidia settings are ok anyway.[...]Thanks for reminding me!  

I checked my nVidia settings, and my DVC was on '0' (I run it at '7.0') and my refresh rate was 75Hz (I run 60Hz).

When you reinstalled the drivers, did you use a .run file?

---

### Post by Yumi on 2010-09-15
no, just marked for reinstallation in synaptic

---

### Post by Yumi on 2010-09-15
OK, managed it. Had to start nvidia-settings as administrator from the terminal "sudo nvidia-settings". Then it let me save the correct settings to the xorg.conf file.

---

### Post by VinDSL on 2010-09-15
~Cool

What I do is, diddle around in *nVidia X Server Settings*, then *Save to X Configuration File*.

Of course, a user doesn't have permission to save the changes to  *xorg.conf*.

Soooo, I *Show preview*, copy the contents, then paste and save them to *xorg.conf* by editing via Nautilus, in admin mode.

Same thing... but I go about it a different way.

Isn't Linux fun?!?!?   ;)

---

### Post by cariboo on 2010-09-15
I did a reinstall the other day, when I adjusted the resolution to 1280X1024, then clicked the save button, a password dialog box popped, this is on a default install, Nvidia drivers were installed using Additional Drivers. The video card in this case is an 8400GS connected to an LG 17" crt.

---

