---
title: "Internal speakers not disengaging with headphones"
date: 2011-07-01
forum: Multimedia Software
---

### Post by wnick88 on 2011-07-01
First post here and I'm still learning what I'm doing, so please bear with me.

I'm running Ubuntu 11.04 64bit on a HP Pavillion DV7 with factory hardware. Sound continues to play through my internal speakers even when headphones are plugged into either of the headphone ports. I'm 100% that this is a software issue, as this doesn't happen on the Windows 7 boot.

I tried to find the answer to this within the comprehensive guide stickied on the multimedia part of this forum, but if I'm honest it just confused me.

As I'm a complete Ubuntu novice, and I've already completely destroyed one Ubuntu install with bad coding, does anyone have any clue what I need to do here? I think the librarians are becoming annoyed with me.

Thanks.

---

### Post by wnick88 on 2011-07-01
Problem (sort of) solved. Worked out how to disengage main speakers whilst keeping headphones active and vice-versa, but still not found a way to make the main speakers automatically disengage when headphones are inserted.

---

### Post by SomeGayDude on 2011-07-16
1) Open a Terminal="Applications->Accessories->Terminal"

2) Open this file using root.
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

3) Add this line after the last line of the file
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

4) Reboot your laptop and it should work.

Let me know if you have any other problems. I think this is the only issue your laptop will have on a new intall.

---

