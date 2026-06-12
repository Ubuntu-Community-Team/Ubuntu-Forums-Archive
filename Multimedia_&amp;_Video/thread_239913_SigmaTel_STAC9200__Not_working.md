---
title: "SigmaTel STAC9200  Not working"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by DukeW on 2006-08-20
Have a Dell inspiron 1300 notebook with an integrated SigmaTel STAC9200! Though when booted one sound is heard, but the OS refuses to open the volume control, or plat any other soind!
# modprobe snd-intel8x0
#
No error is given but still no sound!
ALSO NOTE:
secret@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
while it wors just right after su root

---

### Post by &#12465;&#12452;&#12488; on 2006-09-09
Isn't it supposed to be using snd-hda-intel?

---

