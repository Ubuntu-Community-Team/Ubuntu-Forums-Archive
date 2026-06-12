---
title: "mencoder stalling"
date: 2008-02-28
forum: Multimedia Production
---

### Post by ThndrChckn on 2008-02-28
when i use mencoder to rip a dvd i have it seems to just stall not do anything,

this is what it does when i run mencoder dvd:// -oac mp3lame -ovc xvid -xvidencopts pass=1 -o /dev/null

Compiled with runtime CPU detection.
There are 17 titles on this DVD.
There are 37 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (mono) language: fr aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 1 language: en
subtitle ( sid ): 3 language: fr
number of subtitles on disk: 2
success: format: 2  data: 0x22F55800 - 0x77f1c000


It sounds form the dvd burner that its being accessed but i let it sit over night and it did nothing. just still sitting there im at a loss as to what to do. As far as i know im running the right command to do a double pass as a dvd. But the first command seems to do nothing.

---

### Post by eye208 on 2008-02-29
> **ThndrChckn said:**
> mencoder dvd://
Try specifying a particular title to rip, e.g.
```
mencoder dvd://1 ...
```
If that doesn't work either, you may want to use a separate program for ripping, e.g. vobcopy (from the universe repository).

[http://packages.ubuntu.com/gutsy/vobcopy](http://packages.ubuntu.com/gutsy/vobcopy)

This will copy the DVD contents to your hard disc, optionally using libdvdcss to decrypt them if required. Then you can pass the .vob files to mencoder for transcoding.

---

### Post by hyperair on 2008-02-29
Try testing it with Mplayer before encoding. That usually exposes errors for me. For example:
```
mplayer dvd://
```

or as eye208 said, 
```
mplayer dvd://1
```

---

### Post by ThndrChckn on 2008-03-01
Even after doing mplayer dvd://1 it ends at the same thing, also mencoder dvd://1 doesnt do anything either just stops at the same spot.

---

### Post by eye208 on 2008-03-01
OK, what about plan B?

---

