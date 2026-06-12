---
title: "No sound on speakers only headphones work - Solution (ACL268 in LG 510 Notebook)"
date: 2009-01-08
forum: Multimedia Software
---

### Post by KindDerNacht on 2009-01-08
To get the speakers work you need to add the following line to '/etc/modprobe.d/alsa-base':

options snd-hda-intel model=dell

Reboot and you'll be able to turn up your speaker volume.


For all with a similar problem, this is how i got it to work:

-Check your Chip: 'cat /proc/asound/card0/codec#* | grep Codec'
-Search for it in Alsa-Config-Doc: 'zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz'
-Find your model or try out the different model-values

Good luck ;)

---

