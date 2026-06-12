---
title: "Intel HDA Volume Low"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by wikki on 2007-03-20
I've got an Intel HDA onboard sound card and the volume is extremely low.  When I crank the volume on my speakers up all the way it's just barely at listening level.  I have checked the gnome volume menus and the volumes are all turned all the way up.  Any ideas?

---

### Post by toddwbucy on 2007-03-22
I have the same problem.  Volume real low after fresh feisty install.  my laptop has a realtec alc861.  Incidentally, I had great sound under dapper and edgy, this only happens when I am running feisty.  

thanks in advance of any help
Todd

---

### Post by yaleman on 2008-01-04
Just in case someone else comes looking for the solution to this problem like I did tonight :)

from: [https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/7175](https://answers.launchpad.net/ubuntu/+source/gnome-media/+question/7175)

> 
Try adding this to your /etc/modprobe.d/options (or alsa-base) file:

options snd-hda-intel model=XXX

Replace XXX with one of the quoted values in the list below (remove the quotes)

"3stack" - 3-jack
"3stack-dig" - 3-jack with SPDIF I/O
"6stack-dig" - 6-jack with SPDIF I/O
"auto" - auto-config reading BIOS (default)


I used the 3stack one for my Toshiba Satellite laptop with Intel hda audio and it worked perfectly. :)

---

