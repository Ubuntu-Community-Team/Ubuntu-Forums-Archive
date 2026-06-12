---
title: "DVD playback fails after about 30 minutes"
date: 2014-10-15
forum: Multimedia Software
---

### Post by oooh on 2014-10-15
vlc 2.0.8
lubuntu 12.10
all restricted extras and addons installed 
libdvdcss2 libdvdread4 libdvdnav4 installed 
sudo /usr/share/doc/libdvdread4/install-css.sh executed

dvd starts playing ok, displaying the following in the terminal: 

```
[0xb5400618] main input error: ES_OUT_RESET_PCR called
[0xb5400618] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
[mpeg2video @ 0xb15ef6e0] allocate dummy last picture for field based first keyframe
[0xb5400618] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0xb5400618] main input error: ES_OUT_RESET_PCR called

```

then at fail i get this, and vlc boms out

```
[0xb15f6970] dvdread demux error: read failed for -1/3 blocks at 0xb60d4

```

with the corresponding pop out:

```

Playback failure:
DVDRead could not read 2/4 blocks at 0x9e172.
```

i have tried the following:
- jitter correction to 0
- increased cache to 1.5s
- enabled hw accel
- kaffeine: similar issue, but different output

any pointers? maybe a dvdread issue not vlc ? how to debug ?

i have spent too long googling ...  :roll:

---

### Post by Impavidus on 2014-10-15
Maybe the dvd is dirty or damaged. Have you tried a different dvd?

Further, Lubuntu 12.10 is unsupported. It's better to use a supported release, which would be 14.04 LTS.

---

### Post by oooh on 2014-10-15
I wiill try another dvd

iwanted to change one thing at a time, so i will trty upgrading if that does not work 

ta!

---

### Post by VMC on 2014-10-16
I had something similar to this, and surprisingly after I cleaned the laser lens, it worked perfectly.

---

### Post by oooh on 2014-10-16
Now tested another DVD, which works, 50% failure ratio


Thanks! 
Will try others and try this suspicious one elsewhere

---

### Post by oooh on 2014-10-16
Now tested. A third DVD, which works fine

33% failure ratio

All points at the DVD

Will check it elsewhere, and upgrading to 13,10 anyway

---

### Post by Vladlenin5000 on 2014-10-16
> **oooh said:**
> upgrading to 13,10 anyway

No, you should upgrade to 14.04.

---

### Post by Impavidus on 2014-10-16
If you go from 12.10 to 14.04, the best way is reinstalling. Much better than multiple release upgrades via unsupported releases.

As for that dvd, if it's just dirty you can clean it. That often works. If it's really damaged you may be able to skip across the bad point (play until half a minute before the bad point, make a 2 minute jump or so), but there is no real solution other than getting a fresh copy.

---

