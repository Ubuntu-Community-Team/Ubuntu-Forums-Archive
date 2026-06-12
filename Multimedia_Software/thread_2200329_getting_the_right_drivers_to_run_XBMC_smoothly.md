---
title: "getting the right drivers to run XBMC smoothly"
date: 2014-01-18
forum: Multimedia Software
---

### Post by terces86 on 2014-01-18
Hello everyone,

I built my own little HTPC with a "A4-4000 APU" on a "FM2-A75IA-E53" mainboard (has a AMD-A75 chipset). I only now found out that AMDs driver support seems to have gotten a lot worse over the last years. My biggest problems however come from XBMC dropping the support for Xvba.

I "think" that I have to get vdpau to work, but I do not know how.

What I tried so far:
I installed the 13.10 ubuntu (desktop) and tried the fglrx proprietary driver, but even though I get normal 3D acceleration (glxgears gave me fps of ~3000), the menu of XBMC was very laggy. Reactions to keyboard and mouse inputs were delayed and the more layers there were (for example when you try to add new network folders), the worse it got. Using a different skin made the main menu usable, but with some layers it was still unusable. Weirdest thing: switching from full screen to window mode **completely** solved this! I have no idea why. My only lead in that direction is [this]("http://askubuntu.com/questions/287723/how-do-i-replace-quit-unity-in-ubuntu-13-04"). But I tried using other distributions without Unity (installed the XFCE desktop), but still had the exact same problem. Also starting the session in XBMC gives me the same problems.
I was willing to follow [this how-to]("http://forum.xbmc.org/showthread.php?tid=174854") to get XBMC to completely run on OSS (open source software) by using vdpau, but sadly I seem to be incapable of getting my system to boot the mini.iso from a USB-Stick (I have no CD-Drive).

I only want my little HTPC to run smoothly (really...if it has to decode videos with the CPU, so be it), and be able to run a few services in the background, such as an ftp-server. That's also the reason I decided to use ubuntu as a base and not some already customized distro. Maybe I was wrong there?


If you have any solution to my problem, I'd greatly appreciate the help. I am still quite new to linux, but I know how to use google and my brain, so I can find my way, once I know where to go.

---

### Post by Yellow Pasque on 2014-01-18
Purge the proprietary drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx)
Add oibaf's PPA: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)
Reboot

---

