---
title: "Distorted audio in Hardy"
date: 2008-06-22
forum: Multimedia Software
---

### Post by beleth on 2008-06-22
Just upgraded from Feisty last night/this morning. Wireless networking and custom resolution are working fine, but I noticed upon restart that the Ubuntu startup sound was heavily distorted. The same effect is present using xmms, totem, audacity, and streamed audio over firefox. As much as I do enjoy industrial remixes of my music, I'll not be entirely content with a "it's not a bug, it's a feature" explanation ;]

I'm still a relative neophyte, so while I pride myself with the ability to follow directions well enough, I'm not entirely sure where to start. Any help would be appreciated.

---

### Post by beleth on 2008-06-22
Apologies, found a relevant bug report with fix:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/222192](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/222192)

For anyone else who experiences this problem in alsa-driver:

> go to the command line and start up alsamixer
go to the PCM volume change it from 6xx to 100

---

