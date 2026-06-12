---
title: "Back to low graphics mode"
date: 2008-05-05
forum: Multimedia Software
---

### Post by HalloweenB on 2008-05-05
I'm currently running Fiesty 7.04 on my old Dell machine with an NVIDIA GeForce FX 5500.  For over a year, everything worked flawlessly.  Now, all of a sudden when I boot up, the highest screen resolution I can select is 800x600. Nothing has really changed, except I downloaded the Hardy ISO to install on a separate machine I am building (low graphics there too, but the subject for another post).  Why the Dell went back to low graphics mode is beyond me.

I've looked at many posts related to downloading the drivers from the NVIDIA site, installing using tty, exiting X, etc.  However,

Q:  The fact that the higher graphics settings worked previously means newer drivers are not needed?

Q:  Any hints on which files to check Nvidia settings?

thanks

---

### Post by chewearn on 2008-05-05
Have you enabled nvidia restricted driver?  Go to:
System > Administration > Hardware Drivers
and enable checkbox for nvidia.

---

### Post by HalloweenB on 2008-05-05
Using

System > Admin > Restricted Drivers Manager

gives the message "your hardware does not need any restricted drivers"

Also, I started a tty and used vi to look at the xorg.conf file (I tried to manually edit and change the driver from "nv" to "nvidia" and mis-typed it).  D'oh.

The display text at the top suggested the following command for recompiling if there are any problems:

sudo dpkg-reconfigure -phigh xserver-xorg

It ran, allowed me to select a driver (nv), and also select a screen resolution.  I chose 1168 X 964 (one of the settings just below 1200).

Now Ubuntu boots and I'm able to select 1024 X 768 from System > Preferences > Screen Resolution, which is an improvement at least.

---

### Post by chewearn on 2008-05-05
Oh, I misread your first post.  You are on Feisty.  Have you been using nvidia restricted driver all these while?  If not, nv should be the correct one.

---

### Post by HalloweenB on 2008-05-09
Okay, I got the NVIDIA drivers to work on the old Dell 4550 using the FX5500 graphics card. I'm listing the general procedure by memory from my work PC today. Explicit details are well documented in the forums here.  I can provide more details when I'm on my home PC during evenings GMT -7:00.

1.  Upgraded to Gutsy using the package manager.  Still, the highest setting I could use was 800x600 using Preferences > Screen Resolution.

2.  Downloaded the driver below from NVIDIA: ([http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html))

NVIDIA-Linux-x86-169.12.pkg1.run

3.  Use the well-documented procedure for installing the driver, involving closing X (gdm stop command), running the driver with sh, and restarting X. No additional Linux modules had to be installed, and I let the driver compile whatever kernel it needed to execute. The instructions on the NVIDIA site are pretty good.

4.  After restarting X (gdm start), what screwed up this system was going into the Admin > Restricted Drivers > Enabling, then rebooting.  It turns out I had to disable the restricted drivers.

5.  Exited X again, and ran the following:

sudo dpkg-reconfigure -phigh xserver-xorg

Selected the highest resolution the monitor was capable of, (1280 x 1024), then selected okay.

ran nvidia-xconfig

6.  Restarted X, and the higher graphics settings were available in Preferences > Screen Resolution

---

