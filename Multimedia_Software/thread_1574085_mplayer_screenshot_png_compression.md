---
title: "mplayer screenshot png compression"
date: 2010-09-13
forum: Multimedia Software
---

### Post by krosswindz on 2010-09-13
I use mplayer to play my media files. Occasionally I want to take screenshots of media I am playing. I use the -vf screenshot option to take screenshots which generates shotxxxx.png. The issue is that all those png are not compressed and usually large. When dealing with Hi-Def media they are extremely large, each is 4-5 MB in size at the least. Is there a way I can set the option for compression of png images. If I use imagemagick the same files get compressed to like 1.5MB of png file.

---

### Post by andrew.46 on 2010-09-14
Hi krosswindz,

I suspect that using *-vf screenshot* you will be unable to select the compression ratio of the output png files. In the source this is set in /libmpcodecs/vf_screenshot.c at 0 which I believe is no compression. Certainly would be a good addition to an MPlayer wish-list though, *-vo png *allows selection of compression ratio through a *z=* option and it would make sense to have the same available for the screenshot filter.

Andrew

---

### Post by krosswindz on 2010-09-16
Thanks for the reply andrew, yes it definitely would be good wishlist item for mplayer.

---

### Post by krosswindz on 2010-09-29
Filed an enhancement bug with mplayerhq, [http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1805](http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1805)

---

### Post by andrew.46 on 2010-09-29
Hi krosswindz,

> **krosswindz said:**
> Filed an enhancement bug with mplayerhq, [http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1805](http://bugzilla.mplayerhq.hu/show_bug.cgi?id=1805)

Good on you, I have added myself to the CC list.

Andrew

---

