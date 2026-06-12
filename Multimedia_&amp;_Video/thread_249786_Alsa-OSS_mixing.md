---
title: "Alsa-OSS mixing?"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by andars on 2006-09-03
I got sound mixing to work going through my SPDIF (HW:0,2).  I wanted /dev/dsp to also go through my SPDIF so I edited /etc/modprobe.d/alsa-base and added the line "options snd-pcm-oss dsp_map=2".  It works except it won't   use software mixing.  E.g. if I set Audacity to use /dev/dsp, it won't work untill I disable the KDE sound system.  I need to get alsa-oss to use the dmixer and I'm not sure how to go about this.

---

