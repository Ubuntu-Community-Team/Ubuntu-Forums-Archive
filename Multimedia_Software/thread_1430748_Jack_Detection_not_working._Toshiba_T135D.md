---
title: "Jack Detection not working. Toshiba T135D"
date: 2010-03-15
forum: Multimedia Software
---

### Post by secondstage on 2010-03-15
I bought a Toshiba T135D-S1324 two days ago, and the only thing I can't get to work is for the internal speakers to automatically mute when headphones are plugged in. (Ubuntu 9.10 for AMD64 by the way.)

I have tried to add "options snd-hda-intel model=laptop probe_mask=1" to /etc/modprobe.d/alsa-base.conf but that didn't work. 

The jack detection box is not available under sound preferences. Alsamixer only shows PCM and Master. 

"sudo cat /proc/asound/card0/codec#* | grep Codec" shows "Codec: Conexant ID 5066"

Any ideas?

---

### Post by chkneater on 2010-03-15
In alsamixer, make sure that "all" devices are listed and not just playback.  You can change it with the tab button I believe.  That should list a few more devices along with headphones and line in.  Also check the volume control box that is in the system tray, it may be muted in there somewhere.

---

### Post by secondstage on 2010-03-16
Hitting tab in alsamixer presented the microphone inputs (1 integrated and 1 mic jack). No luck.

---

### Post by trgreerca on 2010-05-27
Here is the solution:

Edit /etc/modprobe.conf/alsa-base.conf and add this line to the bottom of the file:

options snd-hda-intel model="olpc-xo-1_5"

Source: [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/549289](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/549289)

---

### Post by secondstage on 2010-05-27
/etc/modprobe.conf/alsa-base.conf should be /etc/modprobe.d/alsa-base.conf

And it works! Thanks trgreerca for getting that posted here.

---

### Post by cliffskoog on 2010-07-07
Bingo. This worked for me too. AMD T135D-1320. I think this thread should be marked 'SOLVED'.

Thanks trgreerca

---

