---
title: "MKV - requirements"
date: 2010-06-05
forum: Mythbuntu
---

### Post by Chewiesw on 2010-06-05
I can’t play HD (H264) MKV files on my setup. It either doesn’t start or judders and then stops completely. Granted I have quite an old rig ( P4 2.8, 768Mb ram, old 64mb nvidia graphic card) and I am using svideo out to and sd tv. I realise the limitations of svideo (480) but surely the play back should be stable. I have tried the default player which is currently setup as VLC , configured to  FFmeg filter "skip-filter for H264 to all". I have also tried to play these files outside of myth with both VLC and Xine.  I have also had no luck using the internal player option in myth. On my windows rig I was able to use the Matroska codec to resolve a similar problem and play these files. Any cheap solutions? I would love a new TV, Myth box but that ain’t gonna happen.

---

### Post by ian dobson on 2010-06-05
Hi,

Sounds as if your system is too slow for h264 playback. See if you can pickup a NVidia graphic card that supports VDPAU.

Regards
Ian Dobson

---

### Post by Chewiesw on 2010-06-05
Ok VDPAU - My mobo only has a AGP slot, so I need to know what model Nvidia cards support VDPAU, I have had a quick google and see that some conflicting info, but basically only from geforce series 8X and up. Is that right?

I can get my hands on a 7600gt that is in my budget. Will vdpau work with this card?

---

### Post by nickrout on 2010-06-05
no  you need 8xxx 9xxx or 2xx series cards. and you won't find an agp one.

---

