---
title: "No sound with 630a"
date: 2011-07-31
forum: Multimedia Software
---

### Post by nr9699 on 2011-07-31
Hi guys.
I am new to Ubuntu, I just installed 11.04 yesterday. For a while. everything was running fine. Then the sound decided to die on me. I don't know what happened to it. The headset I was using died at the same time, but it still doesn't work when I use ear buds. I have a motherboard that uses nVidia 630a/7025 chip set and a Realtek 889 audio driver. I dual boot with XP, and the sound works fine in XP for me. I have been trying for a while to get it to start up. alsamixer says that the headset isn't muted.

Any help is appreciated! Thanks in advance.

---

### Post by nr9699 on 2011-08-03
bump

---

### Post by .... on 2011-08-04
Run alsa-info script: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by nr9699 on 2011-08-05
I ran that, and I'm not sure if I did it exactly right...
Anyways, heres what I got when I ran it from the terminal:


ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)


I get this, then the option to upload to alsa-project.org.
If I select yes, then it starts uploading, flashes something really quick, then dies.
Any ideas where I'm supposed to be going with this?

---

