---
title: "Cannot Login"
date: 2009-08-05
forum: Multimedia Software
---

### Post by dwlaselle on 2009-08-05
System: JJ Dell Optiplex 280 Intel Pentium 4 3.0 G ATI Radeon 9200

Had Jaunty installed and working, but was trying to improve some of the graphics (ran jerky even with 4 G RAM).  So I tried to install a package (don't remember which one) from synaptic.

Since then, I cannot log into X.  I can get to recovery mode, but that is it.  After I get the Ubuntu Splash and "One Status Bar To Rule Them All", my screen goes haywire.  Message #3 a [http://ubuntuforums.org/showthread.php?t=1224249&highlight=Login+Screen+Messed](http://ubuntuforums.org/showthread.php?t=1224249&highlight=Login+Screen+Messed) has a picture that is very similar.

I cannot drop out of the video with an Ctrl-Alt-F2... it will show me the boot sequence, but then does not give me the terminal login, it goes back to the warped screen.

Things I have tried (tried with monitor plugged into ATI card, plugged into onboard video with ATI disabled, and into onboard video with ATI removed):

Have tried on different monitor, 
Removed 2 G of ram.
Xfix (both from recovery menu & root shell
Recovery mode "Repair broken packages"
Update grub bootloader
dkpg reconfigure xserver-xorg
apt-get install ubuntu-desktop --reinstall
entered "VESA" into xorg.conf
had xorg.conf completely blank
ran a couple of Xfailsafe scripts, but thos emay not have run properly

Any help would be appreciated, as I really don't want to perform a fresh install unless I absolutely have to.  If a log file would be helpful, please let me know which one.

---

### Post by dwlaselle on 2009-08-06
FYI for anybody with the same problem:

Removed the fglrx driver for xorg using apt-get, and that solved the problem.

---

### Post by DigitalBrowser on 2009-12-11
> **dwlaselle said:**
> FYI for anybody with the same problem:
 
Removed the fglrx driver for xorg using apt-get, and that solved the problem.
 
I am having a similar problem. Can you please post the exact command that you used to fix the problem?
 
Thanks.

---

