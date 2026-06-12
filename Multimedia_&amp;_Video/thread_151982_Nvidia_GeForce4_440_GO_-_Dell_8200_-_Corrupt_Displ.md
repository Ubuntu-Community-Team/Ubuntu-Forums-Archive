---
title: "Nvidia GeForce4 440 GO - Dell 8200 - Corrupt Display"
date: 2006-03-28
forum: Multimedia &amp; Video
---

### Post by ilvg2k on 2006-03-28
I am running Breezy Badger (Downloaded an installed within the past week) on a Dell Inspiron 8200 with a Nvidia GeForce4 440 GO. (1600x1200 capable). 

My problem is when I enable the Nvidia drivers the screen is corruped when X starts. I have included a link to a thread which has the same issue except I did not use Automatrix.

Prior to the Ubuntu install, I was running SuSe 9.1 with older (not sure the exact version) Nvidia drivers and acceleration was enabled and working properly. 
     Note: After getting frustrated, I reinstalled the lastest version of SuSe and the same problem happened with the Nvidia drivers.
 
The following is the _only_ thread I have seen on this issue. The guy fixed it by setting the drivers to nv which just turns off video acceleration but corrects the corrupt screen problem. 
The screenshot that he included is the exact problem I have. 
[http://ubuntuforums.org/showthread.php?t=108777](http://ubuntuforums.org/showthread.php?t=108777)

Here is a link to my xorg.conf and xorg.log files.
[http://people.msoe.edu/~curtisje/linux/](http://people.msoe.edu/~curtisje/linux/)

So am I stuck with putting up the screen and have the accelerated video, or run the nv drivers and have shitty video but a correct display? Thank you for your time.

---

### Post by flusheDData on 2007-03-27
I own an Inspiron 8200 with the Nvidia card too.
Try this driver.
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/NVIDIA-Linux-x86-1.0-8776-pkg1.run)
It the newest one that worked for me
the 96xx do not worked at all (black screen or Xserver error).

---

