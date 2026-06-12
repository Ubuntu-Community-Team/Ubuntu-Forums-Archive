---
title: "recovered .3gp file not playing"
date: 2009-12-27
forum: Multimedia Software
---

### Post by longtom on 2009-12-27
Hi,

I recovered a .3gp file from a mini sd card.  The size looks fine, however, I am not able to play it in VLC or any other video player.

I can play "unrecovered" 3gp files.  Is there a way I could attempt to repair this file to be able to at least play part of that file:

Error message in Mobile Media Converter:

```

>> Result: 
FFmpeg version SVN-r19534, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libfaac --enable-nonfree --enable-version3 --disable-ffserver
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.36. 0 / 52.36. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Aug  7 2009 21:55:17, gcc: 4.3.3
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x8a27430]moov atom not found
/home/cango/Desktop/f832.3gp: Error while opening file
----------------------------

```

Any suggestions welcome

---

### Post by andrew.46 on 2009-12-27
Hi longtom,

Can you post this file somewhere?

Andrew

---

### Post by longtom on 2009-12-27
> **andrew.46 said:**
> Hi longtom,

Can you post this file somewhere?

Andrew

Hi Andrew,

it is 536mb....with a slow dsl with cap I am afraid I can't.

---

### Post by andrew.46 on 2009-12-28
Hi longtom,

> **longtom said:**
> it is 536mb....with a slow dsl with cap I am afraid I can't.

Hmmm... that is a pity, perhaps carve a piece off it:

```
dd if=*[COLOR="Red"]yourfile.3gp[/COLOR]* of=smallfile.3gp bs=1024k count=5
```

Andrew

---

### Post by longtom on 2009-12-28
> **andrew.46 said:**
> Hi longtom,



Hmmm... that is a pity, perhaps carve a piece off it:

```
dd if=*[COLOR="Red"]yourfile.3gp[/COLOR]* of=smallfile.3gp bs=1024k count=5
```

Andrew

 Done that and sent to your e-mail address which I found on your website.  Thank you for looking at it.

---

### Post by andrew.46 on 2009-12-28
Hi longtom,

> **longtom said:**
> Done that and sent to your e-mail address which I found on your website.  Thank you for looking at it.

The file arrived safe and well but in a bit of bad news it is unplayable with any media player at my disposal and neither could I convert it. I double checked that dd works safely to trim such files and it certainly does. Unfortunately I suspect that the file is irretrievably corrupt but I would be glad to be proven wrong.

Andrew

---

### Post by longtom on 2009-12-29
> **andrew.46 said:**
> Hi longtom,



The file arrived safe and well but in a bit of bad news it is unplayable with any media player at my disposal and neither could I convert it. I double checked that dd works safely to trim such files and it certainly does. Unfortunately I suspect that the file is irretrievably corrupt but I would be glad to be proven wrong.

Andrew

Thank you very much for all your troubles, this is most appreciated.

---

