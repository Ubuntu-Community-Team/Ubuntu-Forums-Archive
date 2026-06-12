---
title: "capture card keeps switching devices"
date: 2008-10-10
forum: Mythbuntu
---

### Post by sgtstadanko on 2008-10-10
hey,
is there a module option to force the video card (pvr-150) to stay the same.  Randomly on reboots it is swapping between /dev/video0 and /dev/video1

---

### Post by Boppy3125 on 2008-10-10
I found this MythTV thread helpful in solving this same problem:

[http://www.mythtv.org/pipermail/mythtv-users/2007-June/183927.html](http://www.mythtv.org/pipermail/mythtv-users/2007-June/183927.html)

Good luck.

---

### Post by Boppy3125 on 2008-10-10
Longer answer, I had a similar problem with a PVR150 and a Dvico card.  By adding an option line to your ivtv module in /etc/modprobe.conf options ivtv ivtv_first_minor=1 it forces the PVR up to /dev/video1.  At least that way you don't have to keep going in and changing after almost every reboot.

---

### Post by KillerKiwi on 2008-10-10
You need to create a udev rule, this will make a symlink that is always pointed to the correct device

see here for a script to create a udev rule for you

ie sudo python udev-rules.py /dev/video0 /dev/video_pvr150

[http://ubuntuforums.org/showthread.php?t=753434](http://ubuntuforums.org/showthread.php?t=753434)

Note this is also an issue if you have a webcam on the machine, as well as multiple cards

---

