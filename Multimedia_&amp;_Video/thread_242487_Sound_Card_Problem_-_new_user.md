---
title: "Sound Card Problem - new user"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by itsdkw on 2006-08-23
Hello,
   I have recently installed the latest ubuntu release 6.06. I have installed this on a system that was previously running windows 98 without problem.

   As far as I can tell all is ok except for the sound. Linux appears not to have detected the sound card. When the system boots the BIOS reports the presence of a card that it lists as an OPL3sax when it lists the plug and play devices. This card did work under windows 98.:confused:


I have tried the steps detailed here;
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) 

but fail at step 2 as my card is not detected or listed in the output from "lspci -v".

Any ideas? 

Thanks

---

### Post by Culito on 2006-08-23
Well, you could try this:

Start by typing lsmod.  Look for the snd-opl3-sa2 driver.  If it's not there, try
sudo modprobe snd-opl3-sa2
See if that does anything.  You might look here for reference:

[http://www.alsa-project.org/](http://www.alsa-project.org/)

Good luck.  I've been fighting mine for a week now.

---

### Post by itsdkw on 2006-08-24
Hi Culito and thanks. Tried your suggestion without any luck. Will keep digging!

---

