---
title: "Changing Screen resolution after installing in safe graphics mode"
date: 2009-02-09
forum: Multimedia Software
---

### Post by jith87 on 2009-02-09
hi,
   i ve installed Ubuntu8.10 in safe graphics mode on my PC with conf:
Graphics card: intel 82845G
motherboard: intel Pentium4-1.80GHz
the problem is i am not able to alter the screen resolution. there is only one resolution 400x600... My monitor is a 17inch Samsung SyncMaster 753s. its 1024x768 85 KHz.
I tried downloading the latest drivers from intel... but no use i am not able to install them... i tried editing the xorg.conf file also.. but when i reboot it says "Ubuntu is running under low graphics mode" and it reverts back to the normal installation GUI(with 1024x768 ) but once i log in the screen goes brown with the mose pointer alone and nothing else...then i ended up reinstalling....
I am a novice and trying to get into the professional world of Linux. pl help me out...
thanx in advance...

---

### Post by overdrank on 2009-02-09
Hi and welcome, you may try booting into recovery mode, which is usually the second choice from the grub. Then you will be given 4 choices and select xfix mode to correct the graphics issues. 
After xfix is complete you should be given the same choices again and you can continue to boot normally. Hopefully this will help your issue.

---

### Post by jith87 on 2009-02-10
now it reverted to normal installation problem.... when i install normally (not in safe graphics mode) i get the login screen in 1024x768 pixels but once i login the screen remains brown in colour and even the wallpaper is not being displayed.. the panels not being displayed ofcourse.....but i am able to move the mouse pointer alone.... i browsed through some forums and found that Ubunutu8.10 does not support VGA845 graphics card... but can be installed only in safe gr mode.....Many of my friends also have the same problem...

---

### Post by overdrank on 2009-02-10
Yea I have seen threads on the intel graphics and Intrepid. You may try and use the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` by using the ctrl, alt, F1 and then login and use that command above. Then you use the ctrl, alt, F7 and hopefully this will bring you to the desktop.

---

### Post by jith87 on 2009-02-10
I got my problem fixed....
referred this post... they too had the same problem as me...
[http://ubuntuforums.org/showthread.php?t=984296](http://ubuntuforums.org/showthread.php?t=984296)
thanks a lot for your help....

---

