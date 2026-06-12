---
title: "Best Video Encoding Compression?"
date: 2010-02-08
forum: Multimedia Software
---

### Post by beastrace91 on 2010-02-08
Anyone have any tips for reducing file size while encoding DVDs to .avi files? Currently my files are averaging around 700megs for 40mins of video - a bit on the high side. How can I get it down to around 350megs for that same time?

~Jeff

---

### Post by lovinglinux on 2010-02-08
Getting 350 Mb for the same time is not an issue, the real challenge is getting the same quality on 350 Mb.

What program are you using, which codecs, resolution and bitrates?

---

### Post by no2498 on 2010-02-08
lives and tragtor
i need to run mine in that order end up with a mov file
hope that helps

---

### Post by beastrace91 on 2010-02-08
I was using xivd with acidrip however I just installed handbrake and ripping them using x264 has reduced the file sizes by 40%ish

~Jeff

---

### Post by VertexPusher on 2010-02-09
x264 is currently the best video codec available for Linux, but using it with AVI is not a good idea because this combination is incompatible with most hardware-based playback devices. When DivX (the company) dropped their old codec in favor of H.264, they dropped AVI as well and replaced it with MKV (Matroska). Any "DivX Plus"-certified Blu-ray player or set-top box will be able to play back H.264 in MKV (with AAC audio) but not in AVI.

Rule of thumb:
[LIST]
[*]If you need **DivX** (version 5/6) compatibility, use **Xvid** and **MP3** in **AVI**.
[*]If you need **DivX Plus** (version 7) compatibility, use **x264** and **AAC** in **MKV**.
[*]If you need **Apple iPod/iPhone** compatibility, use **x264** and **AAC** in **MP4**.
[*]If you need **HTML5** compatibility, use **Theora** and **Vorbis** in **Ogg**.
[/LIST]

---

### Post by banoncom on 2010-02-09
Help!

Has anyone been having issues with crop detection using acidrip on ubuntu 9.10.

I have been using it on 9.04 with no problems at all, I have tried it on several systems with 9.10 and the crop detection will not work - comes back with the message "crop detection failed - is the DVD loaded?"
Yes! the DVD is loaded, I have tried it with DVD from the dvd drive and also mounted ISO's.
As I said I am currently using acidrip on 9.04 with no problems. I have found very very little info on the forums which makes me think it is not a common problem. - Am i missing something??

PS - it encodes the DVD to divx no problems just doesn't do the crop detection which is very handy

---

### Post by VertexPusher on 2010-02-09
> **banoncom said:**
> Has anyone been having issues with crop detection using acidrip on ubuntu 9.10.
AcidRip users are more likely to find your question if you post it in a separate thread with an appropriate title.

---

### Post by banoncom on 2010-02-09
Thanx.

Have done that.

Cheers.

---

### Post by beastrace91 on 2010-02-09
> **VertexPusher said:**
> x264 is currently the best video codec available for Linux, but using it with AVI is not a good idea because this combination is incompatible with most hardware-based playback devices. When DivX (the company) dropped their old codec in favor of H.264, they dropped AVI as well and replaced it with MKV (Matroska). Any "DivX Plus"-certified Blu-ray player or set-top box will be able to play back H.264 in MKV (with AAC audio) but not in AVI.

Rule of thumb:
[LIST]
[*]If you need **DivX** (version 5/6) compatibility, use **Xvid** and **MP3** in **AVI**.
[*]If you need **DivX Plus** (version 7) compatibility, use **x264** and **AAC** in **MKV**.
[*]If you need **Apple iPod/iPhone** compatibility, use **x264** and **AAC** in **MP4**.
[*]If you need **HTML5** compatibility, use **Theora** and **Vorbis** in **Ogg**.
[/LIST]

I'm aware, should have mentioned that I am ripping them as m4v files with x264

~Jeff

---

