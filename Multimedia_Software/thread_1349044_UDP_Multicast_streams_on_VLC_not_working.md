---
title: "UDP Multicast streams on VLC not working"
date: 2009-12-07
forum: Multimedia Software
---

### Post by BoobsLover on 2009-12-07
I'm trying to get IPTV channels on VLC.The problem is just few channels actually works,while most crash after few seconds when i start getting green boxes.
And i get this kinds of errors:

```
 libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 15)
> libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 6)
> libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 8)
> libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 4)
Segmentation fault
```

Few channels have all the video scrambled and then crash also.

In the setting,i set the cache from the default 300 up to 2000 ,i finally manager get some channels working.Ironically,the few channels that works flawless are adult ,normally crypted channels  :mrgreen: 
I think this might be a codec issue,since the channels are H264 with mpga audio track,but i'm not sure

Strangely on the newest version of VLC all channels are scrambled and not working.So i'm usig 0.86e version
Running on Ubuntu 8.04 x64

---

