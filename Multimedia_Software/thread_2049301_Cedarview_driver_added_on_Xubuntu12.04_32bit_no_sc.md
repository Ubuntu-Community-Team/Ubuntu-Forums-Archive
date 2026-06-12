---
title: "Cedarview driver added on Xubuntu12.04 32bit no screen"
date: 2012-08-28
forum: Multimedia Software
---

### Post by matthewh3 on 2012-08-28
Hi I added the Cedarview proprietary driver on Xubuntu 12.04 32bit and the screen just went blank and on reboot all I got was a command line.  I am using a N2800 with HDMI.  
Is there any news on this coming to Ubuntu 64bit.  Would I be better off using Meego due to that having a driver built in?

---

### Post by danman 2000 on 2012-09-03
I am in a similar situation to you but managed to get back to the x screen.  Thought my experience might be of interest.

**Short version: **If anyone has this problem, they might want to try logging in at the command prompt, and running 'startx'.  For me this gave 1024x800 resolution instead of 800x600, but was not a long term fix. I have removed the drivers until I know a better way (see below). 

**Long version: **I had just completed a fresh 32 bit Xubuntu installation onto my netbook (Atom N2600 processor), just realised that I was running in 800x600, and the 'Additional drivers' notification came up.  The 'Cedar Trail drm driver in DKMS format' proprietary driver was not activated.  I didn't know this was available just yet. :)  I activated it, and my screen went blank during the installation process.  I waited for a while but there was no HDD activity.  I held the power button in for a hard reset, and upon rebooting I was greeted with something along the lines of "Broken pipe, checking battery status".  :confused: 

I read on a forum that going to command line via Ctrl+Alt+F2, logging in, then running 'sudo apt-get install ubuntu-desktop' would help, then running 'startx'.  I tried this, and aborted the install half way through the download, after wanting to try the 'startx' command first.  Running 'startx' took me back to the desktop, and I had 1024x800 for the first time.  I was also greeted by a notification that stated I could install the Cedar trail 3D GMA500 driver.  I installed this and tried to reboot, but was told I was unauthorised to perform that action, and was taken to the command line where I rebooted using 'ctrl-alt-del'

This did not fix the blank screen at startup, but I was still able to access the GUI via 'startx'.  I removed both drivers, rebooted once more, and am back to 800x600. ](*,)

---

### Post by shokocham on 2012-09-20
I'm pretty sure the problem is with lightdm. Try to install gdm instead. As root, issue:
```
apt-get install gdm
```
During installation, when asked to choose the default manager, mark gdm and hit enter.

---

### Post by oller.mauser on 2013-08-23
I have the very same problem as described by danman (Atom N2600 processor, Xubuntu, Cedarview driver installation ended in black screen).

Is there any news? Did shokocham hint solve the issue?

---

### Post by texadactyl on 2013-09-06
[http://ubuntuforums.org/showthread.php?t=2166604]("http://ubuntuforums.org/showthread.php?t=2166604")

The issue seems to lie in hardware detection below the level of desktop software like Gnome, KDE, and XFCE.  While Cedar View support will probably never be optimum, there might be improved support in saucy (13.10) coming up.  

Try running a Live Desktop from a USB stick?

Good luck.

---

