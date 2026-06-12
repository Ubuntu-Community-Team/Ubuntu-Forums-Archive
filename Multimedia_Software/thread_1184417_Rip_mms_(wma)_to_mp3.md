---
title: "Rip mms:// (wma) to mp3"
date: 2009-06-11
forum: Multimedia Software
---

### Post by thyone on 2009-06-11
I would like to rip a mms://-stream to mp3, _without_ having to convert it after it has been saved? I'm want to save a stream for, let's say, 12 hours, and then remove parts out of it with Audacity. This program needs MP3, so I want to save the stream to mp3 directly, without having to convert it.

Does anyone have any clue on which program to use? I've been looking on the internet for the past few days, but no (good) results, only people telling to use MPlayer and then convert it (but that's not what I want).

Thank you!

---

### Post by andrew.46 on 2009-06-11
Hi thyone,

> **thyone said:**
> I would like to rip a mms://-stream to mp3, _without_ having to convert it after it has been saved? I'm want to save a stream for, let's say, 12 hours, and then remove parts out of it with Audacity. This program needs MP3, so I want to save the stream to mp3 directly, without having to convert it.

Can you give the address of the stream, I would be interested in seeing what I can come up with.

Andrew

---

### Post by thyone on 2009-06-11
mms://livemedia.omroep.nl/radio1-bb (Dutch "Radio 1")

---

### Post by whoop on 2009-06-11
vlc media player
vlc-->media-->convert-save-->network

---

### Post by andrew.46 on 2009-06-11
Hi thyrone,

As whoop has suggested one very easy way is to use an appropriately configured vlc. I added your stream in and vlc quite neatly spat out a nice clean mp3 at the other end :-). I attach a screenshot showing the appropriate settings screen. This is vlc 1.0 rc3 so your settings may look a little different.

All the best,

Andrew

---

### Post by Mariane on 2009-07-06
Doesn't work for me, my version does not have a "media" menu (VLC media player 0.8.6e Janus) 

mms://vod-dun.u-strasbg.fr/vod/2009/0128_egc/egc_kodratoff.wmv

Any idea, please? 

Mariane

---

### Post by andrew.46 on 2009-07-07
Hi Marianne,

> **Mariane said:**
> Doesn't work for me, my version does not have a "media" menu (VLC media player 0.8.6e Janus) 

mms://vod-dun.u-strasbg.fr/vod/2009/0128_egc/egc_kodratoff.wmv


Unfortunately I don't know enough about the older versions of vlc, but this stream saved well enough with MPlayer:

```
 mplayer mms://vod-dun.u-strasbg.fr/vod/2009/0128_egc/egc_kodratoff.wmv -dumpstream -dumpfile output.wmv
```

All the best,

Andrew

---

