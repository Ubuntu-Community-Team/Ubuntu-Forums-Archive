---
title: "Issues with mplayer and .flv files"
date: 2009-11-14
forum: Multimedia Software
---

### Post by brandon88tube on 2009-11-14
For some reason I can't seem to get mplayer to play any .flv files. Can anyone out there help?

---

### Post by HappyFeet on 2009-11-14
Do you have flash installed? What codecs have you installed? Have you tried vlc player?

---

### Post by brandon88tube on 2009-11-14
Yes, I have flash installed and I am asking about mplayer. On the codec side of things whatever came with mplayer is what I have. I don't know off the top of my head what other ones are installed, though it shouldn't really matter with mplayer as it should be able to play them anyways.

---

### Post by HappyFeet on 2009-11-14
You may need to install the gstreamer bad and ugly codecs.

---

### Post by brandon88tube on 2009-11-14
I'm curious as to how that would help. Isn't that for programs like Totem(gstreamer version) that use gstreamer?

---

### Post by andrew.46 on 2009-11-15
Hi brandon,

> **brandon88tube said:**
> For some reason I can't seem to get mplayer to play any .flv files. Can anyone out there help?

Can you play one of these files from a terminal as follows:

```
mplayer -v **[COLOR="Red"]myfile.flv[/COLOR]**
```

and post the command + full terminal output here?

Andrew

---

### Post by brandon88tube on 2009-11-15
Here is the long output telling me the codec isn't supported.
```
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]Unsupported video codec (7)
[flv @ 0x883ec08]skipping flv packet: type 97, size 7627016, flags 0
[flv @ 0x883ec08]skipping flv packet: type 137, size 12446070, flags 0
stream_seek: WARNING! Can't seek to 0x1324ABA !
[flv @ 0x883ec08]skipping flv packet: type 139, size 11395659, flags 0
stream_seek: WARNING! Can't seek to 0x122C393 !
[flv @ 0x883ec08]skipping flv packet: type 5, size 8935901, flags 0
stream_seek: WARNING! Can't seek to 0xFDBB29 !
[flv @ 0x883ec08]skipping flv packet: type 152, size 11746121, flags 0
stream_seek: WARNING! Can't seek to 0x1291C99 !
[flv @ 0x883ec08]skipping flv packet: type 115, size 9013217, flags 0
stream_seek: WARNING! Can't seek to 0xFFE935 !
[flv @ 0x883ec08]skipping flv packet: type 199, size 129517, flags 0
[flv @ 0x883ec08]skipping flv packet: type 124, size 6262444, flags 0
stream_seek: WARNING! Can't seek to 0xD86A00 !
[flv @ 0x883ec08]skipping flv packet: type 6, size 7021854, flags 0
stream_seek: WARNING! Can't seek to 0xE48076 !
[flv @ 0x883ec08]skipping flv packet: type 197, size 9089807, flags 0
stream_seek: WARNING! Can't seek to 0x1048E6B !
[flv @ 0x883ec08]skipping flv packet: type 2, size 16473037, flags 0
stream_seek: WARNING! Can't seek to 0x175B72D !
[flv @ 0x883ec08]skipping flv packet: type 56, size 14269208, flags 0
stream_seek: WARNING! Can't seek to 0x154967C !
[flv @ 0x883ec08]skipping flv packet: type 208, size 14606121, flags 0
stream_seek: WARNING! Can't seek to 0x15A3A91 !
[flv @ 0x883ec08]skipping flv packet: type 200, size 10011181, flags 0
stream_seek: WARNING! Can't seek to 0x1149D99 !
[flv @ 0x883ec08]skipping flv packet: type 29, size 12491160, flags 0
stream_seek: WARNING! Can't seek to 0x13AF508 !
[flv @ 0x883ec08]skipping flv packet: type 63, size 9353352, flags 0
stream_seek: WARNING! Can't seek to 0x10B93FC !
[flv @ 0x883ec08]skipping flv packet: type 235, size 5757889, flags 0
stream_seek: WARNING! Can't seek to 0xD53739 !
[flv @ 0x883ec08]skipping flv packet: type 43, size 3911543, flags 0
stream_seek: WARNING! Can't seek to 0xB98AF3 !
[flv @ 0x883ec08]skipping flv packet: type 1, size 1509632, flags 0
[flv @ 0x883ec08]skipping flv packet: type 161, size 16031501, flags 0
stream_seek: WARNING! Can't seek to 0x18A039C !
[flv @ 0x883ec08]skipping flv packet: type 161, size 13428814, flags 0
stream_seek: WARNING! Can't seek to 0x162CCE1 !
[flv @ 0x883ec08]skipping flv packet: type 0, size 6949064, flags 0
stream_seek: WARNING! Can't seek to 0x1006D5F !
[flv @ 0x883ec08]skipping flv packet: type 22, size 6306696, flags 0
stream_seek: WARNING! Can't seek to 0xF72023 !
[flv @ 0x883ec08]skipping flv packet: type 245, size 13626543, flags 0
stream_seek: WARNING! Can't seek to 0x167514E !
[flv @ 0x883ec08]skipping flv packet: type 26, size 13684364, flags 0
stream_seek: WARNING! Can't seek to 0x168B32F !
[flv @ 0x883ec08]skipping flv packet: type 50, size 9472535, flags 0
stream_seek: WARNING! Can't seek to 0x128EEBE !
[flv @ 0x883ec08]skipping flv packet: type 123, size 8734339, flags 0
stream_seek: WARNING! Can't seek to 0x11E2B2E !
[flv @ 0x883ec08]skipping flv packet: type 194, size 5008169, flags 0
stream_seek: WARNING! Can't seek to 0xE5CFD8 !
[flv @ 0x883ec08]skipping flv packet: type 242, size 7597028, flags 0
stream_seek: WARNING! Can't seek to 0x10DD097 !
[flv @ 0x883ec08]skipping flv packet: type 102, size 11385378, flags 0
stream_seek: WARNING! Can't seek to 0x1481ED9 !
[flv @ 0x883ec08]skipping flv packet: type 166, size 1911959, flags 0
stream_seek: WARNING! Can't seek to 0xB81152 !
[flv @ 0x883ec08]skipping flv packet: type 175, size 2186501, flags 0
stream_seek: WARNING! Can't seek to 0xBCC1C4 !
[flv @ 0x883ec08]skipping flv packet: type 148, size 5825462, flags 0
stream_seek: WARNING! Can't seek to 0xF4C879 !
[flv @ 0x883ec08]skipping flv packet: type 245, size 5938959, flags 0
stream_seek: WARNING! Can't seek to 0xF703D6 !
[flv @ 0x883ec08]skipping flv packet: type 165, size 9929070, flags 0
stream_seek: WARNING! Can't seek to 0x1346639 !
[flv @ 0x883ec08]skipping flv packet: type 17, size 7235584, flags 0
stream_seek: WARNING! Can't seek to 0x10BCCCF !
[flv @ 0x883ec08]skipping flv packet: type 50, size 12291203, flags 0
stream_seek: WARNING! Can't seek to 0x1597156 !
[flv @ 0x883ec08]skipping flv packet: type 79, size 8240431, flags 0
stream_seek: WARNING! Can't seek to 0x11C2206 !
[flv @ 0x883ec08]skipping flv packet: type 177, size 2108436, flags 0
stream_seek: WARNING! Can't seek to 0xBF10EF !
[flv @ 0x883ec08]skipping flv packet: type 110, size 5812042, flags 0
stream_seek: WARNING! Can't seek to 0xF81429 !
[flv @ 0x883ec08]skipping flv packet: type 96, size 4610216, flags 0
stream_seek: WARNING! Can't seek to 0xE63D8B !
[flv @ 0x883ec08]skipping flv packet: type 53, size 9916745, flags 0
stream_seek: WARNING! Can't seek to 0x137B630 !
[flv @ 0x883ec08]skipping flv packet: type 37, size 2643257, flags 0
stream_seek: WARNING! Can't seek to 0xC93A33 !
[flv @ 0x883ec08]skipping flv packet: type 149, size 7115472, flags 0
stream_seek: WARNING! Can't seek to 0x10DF7BF !
[flv @ 0x883ec08]skipping flv packet: type 125, size 1564080, flags 0
stream_seek: WARNING! Can't seek to 0xB9C2A3 !
[flv @ 0x883ec08]skipping flv packet: type 70, size 455854, flags 0
[flv @ 0x883ec08]skipping flv packet: type 27, size 5825051, flags 0
stream_seek: WARNING! Can't seek to 0x1023BCF !
[flv @ 0x883ec08]skipping flv packet: type 64, size 16087570, flags 0
stream_seek: WARNING! Can't seek to 0x19F53CA !
[flv @ 0x883ec08]skipping flv packet: type 247, size 2097681, flags 0
stream_seek: WARNING! Can't seek to 0xCA5BCD !
[flv @ 0x883ec08]skipping flv packet: type 117, size 4546821, flags 0
stream_seek: WARNING! Can't seek to 0xF03AC5 !
[flv @ 0x883ec08]skipping flv packet: type 142, size 2922306, flags 0
stream_seek: WARNING! Can't seek to 0xD7F106 !
[flv @ 0x883ec08]skipping flv packet: type 255, size 16642306, flags 0
stream_seek: WARNING! Can't seek to 0x1A9CACA !
[flv @ 0x883ec08]skipping flv packet: type 78, size 2473658, flags 0
stream_seek: WARNING! Can't seek to 0xD21886 !
[flv @ 0x883ec08]skipping flv packet: type 34, size 1872124, flags 0
stream_seek: WARNING! Can't seek to 0xC96ACC !
stream_seek: WARNING! Can't seek to 0xACE6F2 !
==> Found video stream: 0
[lavf] Video stream found, -vid 0
======= VIDEO Format ======
  biSize 40
  biWidth 0
  biHeight 0
  biPlanes 0
  biBitCount 0
  biCompression 7=''
  biSizeImage 0
===========================
==> Found audio stream: 1
[lavf] Audio stream found, -aid 1
======= WAVE Format =======
Format Tag: 10 (0xA)
Channels: 2
Samplerate: 44100
avg byte/sec: 0
Block align: 1
bits/sample: 16
cbSize: 0
==========================================================================
LAVF: 1 audio and 1 video streams found
LAVF: build 3345920
VIDEO:  []  0x0  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x7  size:0x0  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/brandon/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 2046x2046
==========================================================================
Cannot find codec matching selected -vo and video format 0x7.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
======= WAVE Format =======
Format Tag: 10 (0xA)
Channels: 2
Samplerate: 44100
avg byte/sec: 0
Block align: 1
bits/sample: 16
cbSize: 0
==========================================================================
======= WAVE Format =======
Format Tag: 1 (0x1)
Channels: 2
Samplerate: 44100
avg byte/sec: 176400
Block align: 4
bits/sample: 16
cbSize: 0
==========================================================================
Win32 LoadLibrary failed to load: wmspdmod.dll, /usr/lib/win32/wmspdmod.dll, /usr/local/lib/win32/wmspdmod.dll
IMediaObject ERROR: 0x88e67c9  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmspdmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dshow] Win32/DirectShow decoders
Win32 LoadLibrary failed to load: wmavds32.ax, /usr/lib/win32/wmavds32.ax, /usr/local/lib/win32/wmavds32.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=wmavds32.ax, r=0xa6561ba)
ERROR: Could not open required DirectShow codec wmavds32.ax.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0xA.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Freeing 0 unused audio chunks.
Video: no video
Freeing 0 unused video chunks.

vo: uninit ...

Exiting... (End of file)

```

---

### Post by andrew.46 on 2009-11-16
Hi brandon88tube,

I guess there are at least 2 possibilities. The first would be that the flv is corrupt which is quite possible as some youtube downloaders (is this where the file came from?) have been mangling the files more than a little in recent times. The other possibility is a problem with MPlayer itself. The easiest way to get a new well made package of MPlayer is to use the PPA of rvm:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

So my best advice would be to test your flvs with rvm's package.

All the best,

Andrew

---

### Post by brandon88tube on 2009-11-16
I know its not the flv as I'm grabbing the file directly myself. No programs involved. I think it might be mplayer so I'm going to try what you suggested and see how things go.

---

### Post by andrew.46 on 2009-11-17
Hi brandon,

> **brandon88tube said:**
> I know its not the flv as I'm grabbing the file directly myself. No programs involved. I think it might be mplayer so I'm going to try what you suggested and see how things go.

Is it possible to post this difficult flv anywhere? I would be interested to have a look at it.

Andrew

---

### Post by brandon88tube on 2009-11-17
Its not a single flv file, but every single flv file I throw at it. Also, how would I go about installing this from the tar file of their latest snapshot?

---

### Post by andrew.46 on 2009-11-17
Hi brandon,

> **brandon88tube said:**
> Its not a single flv file, but every single flv file I throw at it. Also, how would I go about installing this from the tar file of their latest snapshot?

Well, rvm's PPA is the easiest way to get a recent well built copy of MPlayer running. To get the *very latest* you can build your own:


Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

I assume you are running Karmic? But it still might be worthwhile trying rvm's PPA before putting a reasonable amount of time and effort into building your own.

Andrew

---

### Post by brandon88tube on 2009-11-17
Nah, 9.10 was giving me issues with my wireless that I couldn't seem to work out so I stuck with 9.04, which my wireless works fine in.

---

### Post by mc4man on 2009-11-17
> Wrong thread truly

---

### Post by andrew.46 on 2009-11-17
Hi Brandon,

> **brandon88tube said:**
> Nah, 9.10 was giving me issues with my wireless that I couldn't seem to work out so I stuck with 9.04, which my wireless works fine in.

In that case:

HowTo: Install the very latest MPlayer under Jaunty Jackalope
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

@mc4man: Wrong thread :).

Andrew

---

### Post by brandon88tube on 2009-11-18
Thanks for trying to help me out with this even though I haven't really had any time to try getting this to work. Will update when I get the time.

---

