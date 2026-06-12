---
title: "nvidia; stuck at 800x600"
date: 2008-06-01
forum: Multimedia Software
---

### Post by posaune on 2008-06-01
Hi,

When I had Ubuntu 7.10, it would happily talk to the nvidia proprietary driver, give me a screen resolution of 1280 x 1024 and allow all the Compiz effects to run no problem.

When I upgraded to Ubuntu 8.04, I could no longer see nvidia under Hardware Drivers and the screen shrank to 800x600. After a lot of re-installing drivers and general guessing, I got a reasonable resolution display back but turning on Compiz to "full" would cause all sorts of hangs and problems.

Having just booted up the PC (after making no prior config changes); I was told that Ubuntu was running in an emergency low resolution (800x600x61 Hz) and I'm once again without a decent driver.

What is the official / easy / straightforward way of getting Ubuntu to talk nicely to my display card and monitor?

Thanks.

---

### Post by posaune on 2008-06-01
Now when I reboot, I get stuck in a screen mode my monitor can't properly display.

How do I get a working display back?

Thanks.

---

### Post by posaune on 2008-06-01
I know nobody will actually bother replying with a sensible answer, any more that I got when I asked (politely) about a (still-unresolved) printing problem.

It just seems to me that Linux / Ubuntu is full of bugs, is unreliable and is generally frustrating.

So I plan to recover my files, and bin Ubuntu. It's just been too much trouble.

So long.

---

### Post by twright on 2008-06-01
hi
you can probably fix the resolution by rebooting, pressing esc to get the grub menu, selecting recovery mode then selecting fix x (you can also use the command sudo init 1 to get to recovery mode)

then you should be able to set up your drivers normally

---

### Post by ubuntu-freak on 2008-06-01
What's the point in making threats? If Gutsy worked fine, why would you go back to Windows? Many more small and not so small bugs will be fixed in 8.04.1.
 
Perhaps your NVIDIA driver doesn't work well with the new Xorg, or perhaps you would benifit from a fresh install of Hardy, then not try to install the NVIDIA drivers until the system has installed all available updates. If that doesn't work, install the driver with Envy.
 
To force a correct resolution, execute this command:
 
**sudo xrandr -s 1280x1024**
 
If that doesn't work, bring up a list of supported resolutions:
 
**sudo xrardr -q**
 
Set the highest resolution available, then try setting 1280x1024 again.
 
Nathan

---

### Post by superbiskit on 2008-06-01
> **posaune said:**
> Hi,
When I upgraded to Ubuntu 8.04, I could no longer see nvidia under Hardware Drivers and the screen shrank to 800x600.

I'm sure it won't make you feel better that you are not at all alone :(

Two things to check: FIRST, make sure all the kernel (linux-xxxx) packages are the same revision.  It sounds strange - and I think it's a bug - but sometimes linux-restricted-modules doesn't get updated in synch.  Also, check linux-ubuntu-modules. And be sure any nvidia-glx stuff also matches (not sure how that is done).

SECOND, I have found that sometimes the xserver setup doesn't get the correct horizontal and vertical frequencies and therefore disqualifies a 1024x768 mode as not being feasible with the frequencies it has.  Check the FineManual that came with your monitor. See the sticky thread about "How I made it work" at the top of this forum.

---

### Post by Xiong Chiamiov on 2008-06-01
There is a problem with the nvidia drivers in the repos and the kernel that comes with Hardy.  Try [this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").

> **posaune said:**
> I know nobody will actually bother replying with a sensible answer, any more that I got when I asked (politely) about a (still-unresolved) printing problem.

It just seems to me that Linux / Ubuntu is full of bugs, is unreliable and is generally frustrating.

So I plan to recover my files, and bin Ubuntu. It's just been too much trouble.

So long.

[Read section 3a]("http://linux.oneandoneis2.org/LNW.htm").

---

### Post by Dark-Penguin on 2008-06-01
I have a Dell Latitude C840 laptop and when I upgraded to 8.04 it seems to work fine. I actually would like to know how to reduce my resolution. When I'm at a high resolution my Firefox displays a black screen. Does any one know know to bring up the resolution area so that I can change it? When I try to go through (System - Preferences) it tells me "The XServer does not support the XRandR extension"

The only way to get my firefox to work correctly it to reboot.

HELP ME!!!!!

---

### Post by ubuntu-freak on 2008-06-01
> **Dark-Penguin said:**
> I have a Dell Latitude C840 laptop and when I upgraded to 8.04 it seems to work fine. I actually would like to know how to reduce my resolution. When I'm at a high resolution my Firefox displays a black screen. Does any one know know to bring up the resolution area so that I can change it? When I try to go through (System - Preferences) it tells me "The XServer does not support the XRandR extension"

The only way to get my firefox to work correctly it to reboot.

HELP ME!!!!!

 
Must be a problem with your upgrade. My commands above didn't work? You could try Alt F2 and "gksudo displayconfig-gtk" I guess.
 
Nathan

---

### Post by Dark-Penguin on 2008-06-02
> **reassuringlyoffensive said:**
> Must be a problem with your upgrade. My commands above didn't work? You could try Alt F2 and "gksudo displayconfig-gtk" I guess.
 
Nathan

Thanks. that helped. I was able to lower my res from 1600x1200 to something more manageable.

---

