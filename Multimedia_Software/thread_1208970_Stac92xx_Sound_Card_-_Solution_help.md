---
title: "Stac92xx Sound Card - Solution help"
date: 2009-07-09
forum: Multimedia Software
---

### Post by OliverBarker on 2009-07-09
My Compaq Mini has a stac92xx sound card, luckily I managed to find a solution by a person who had a similar problem yet as  much as it pains me to say it, I'm still a n00b when it comes to this sort of thing and I don't know how to implement the solution he used. The link to it is below, I'd appreciate any help you can offer as to use it and get sound!

[http://ubuntuforums.org/showpost.php?p=6310299&postcount=2](http://ubuntuforums.org/showpost.php?p=6310299&postcount=2)

---

### Post by Yellow Pasque on 2009-07-09
Ubuntu Jaunty/9.04 already has ALSA 1.0.18, so no need to compile it from source.

Just:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Paste this line (at the end of the file IIRC)
```
options snd-hda-intel model=ref
```

Sound should work on your next reboot.

---

