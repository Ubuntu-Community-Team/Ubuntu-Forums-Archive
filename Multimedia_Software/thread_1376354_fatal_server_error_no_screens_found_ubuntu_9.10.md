---
title: "fatal server error no screens found ubuntu 9.10"
date: 2010-01-09
forum: Multimedia Software
---

### Post by avatardvr@gmail.com on 2010-01-09
Here again.  I've installed 9.10 on a work station with success.  I've got an nvidia quadro fx 3000 and its supported under nvidia legacy driver apparently.  So I've tried to install the driver with no success.  Xorg.0.log reports a fatal server error no screens found.  I get a flashing console login when I boot with "nvidia" device driver in xorg.conf, it boots fine with "nv".  No matter what I try I cant get it to boot with nvidia drivers.  Also, on a side note, after initially installing nvidia driver thru hardware in gnome, I no longer have a grub loader option to select recovery or anything else.  Upon boot it displays "grub" briefly then continues to boot to gui.  I've set the delay to 20 seconds with no results.  Any help on the graphics problem would be hugely appreciated.  I can live with the grub problem, or I may try re-installing grub after I solve this graphics issue.

EDIT
Resolved the issue of the display, now on to the grub menu.

---

### Post by kingdogbert on 2010-01-20
How did you solve your problem? I'm dealing with the same thing and can't make any progress (<a href="http://ubuntuforums.org/showthread.php?t=1386175">my thread here</a>). Thank you

---

### Post by avatardvr@gmail.com on 2010-01-20
its really quite embarrassing and probably not going to help you much but I neglected to plug the power supply into the video card itself.  Past issues with an Nvidia 8600GT OC were solved by editing /etc/xorg.conf file and changing the driver to nvidia.  I think it was nv instead of nvidia but that was a while ago.  Sorry I cant be of more help.  Good luck

---

### Post by kingdogbert on 2010-01-20
Hehe, only a little embarrassing, but I understand why you didn't post that solution earlier :)

Anyways, I've already tried changing the "driver" line to no effect, so that won't help. Thanks anyways for the quick response.

---

