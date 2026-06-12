---
title: "geforce 6200 video card installation trouble"
date: 2011-04-03
forum: Mythbuntu
---

### Post by rudy1094 on 2011-04-03
Hi,

I'm another noob trying to install mythbuntu 10.10. Here's the system I'm trying to install mythbuntu on:
Dell Dimension 2350
160GB Hard drive
1 GB RAM
TV Tuner Card: DIVCO Fusion HDTV 5 RT Gold
Video Card: Geforce 6200

My video card has been presenting problems for me. Initially I had problems booting to the live CD. I was getting a "busybox v1.15.3... (initramfs) unable to find a medium containing a live file system". I got past this by changing my BIOS setting, so that it booted using the onboard video rather than the geforce 6200. 

When I finally installed the OS, I was given the option to use opensource video drivers or nvidia drivers. I tried using the nvidia driver and when I did the installing process would struggle. The installation process would finish, but during reboot the system would hang. I would get a black screen with a cursor in the upper left of the screen. I went through the installation process a number of times and each time I installed with the nvidia driver the installation process would hang on reboot.

So at this time I have mythbuntu 10.10 installed with the opensource video drivers. It's using the integrated intel video card rather than the geforce 6200 video card. How do I install the geforce 6200 video card? Do I need the nvidia driver?

Given I'm new to mythbuntu, I appreciate any suggestions you have that may make installing and using mythbuntu easier. Also any help getting my video card to work is appreciated.

Thanks.

---

### Post by novellahub on 2011-04-04
Install using the open source driver.  Then after your first successful boot, then install the Nvidia driver from the menu:

System->Administration->Hardware Drivers

---

### Post by itlarson on 2011-04-04
I think you need to set the bios to use the 6200 instead of the motherboard graphics.  If you aren't getting output from the card before you install the closed source drivers, installing them won't help.  And if you are applying the Nvidia drivers to the Intel motherboard graphics, this might cause a crash.  I have a similar vintage Nvidia card which actually has a power connector on the card itself.  I know from experience that the card won't work without it connected, so check if your card has one, and plug a cable from the power supply into it if it does.  Once you have the card working with the open drivers, you can install the closed ones as the previous post suggests.

---

### Post by rudy1094 on 2011-04-05
When I tried using the System->Administration->Hardware Drivers process it messed something up and wouldn't allow the system to boot, so I had to reinstall the OS. Sorry for the vague description, it was a couple of days ago when I tried that approach.

I double checked the video card and there's no power connector on it. There's a sound connector that I can connect to the motherboard, but no power connector. When I changed the BIOS to use the video card instead of the onboard video card the computer wouldn't boot. I got the Mythbuntu splash screen with the color changing dots, but it never booted. 

I'm not sure what to do.

---

### Post by utar on 2011-04-05
Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=1592110](http://ubuntuforums.org/showthread.php?t=1592110)

---

### Post by rudy1094 on 2011-04-05
Thanks, I'll try that this evening.

---

### Post by rudy1094 on 2011-04-09
This was the solution to my problem.
[http://ubuntuforums.org/showthread.php?t=1695212&highlight=dimension+2350](http://ubuntuforums.org/showthread.php?t=1695212&highlight=dimension+2350)

---

