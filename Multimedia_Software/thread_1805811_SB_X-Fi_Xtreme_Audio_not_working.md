---
title: "SB X-Fi Xtreme Audio not working"
date: 2011-07-16
forum: Multimedia Software
---

### Post by MtnDew on 2011-07-16
I'm trying to get output from my speakers, listed in "Sound Preferences" as SB X-Fi Xtreme Audio CA0110-IBG Analog Stereo.   [quote=uname -a] Linux Ubuntu-Aphex 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux [/quote]  [quote=aplay -l] **** List of PLAYBACK Hardware Devices **** card 0: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]   Subdevices: 0/1   Subdevice #0: subdevice #0 card 0: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]   Subdevices: 1/1   Subdevice #0: subdevice #0 card 1: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]   Subdevices: 1/1   Subdevice #0: subdevice #0 [/quote]  [quote=cat /proc/asound/version] Advanced Linux Sound Architecture Driver Version 1.0.21. [/quote]  [quote=head -n 1 /proc/asound/card*/codec#*] Codec: Creative CA0110-IBG [/quote]

I saw [this post ]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")but I don't know where to put that information.

---

