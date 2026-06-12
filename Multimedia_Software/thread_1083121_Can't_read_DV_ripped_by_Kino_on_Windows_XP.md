---
title: "Can't read DV ripped by Kino on Windows XP"
date: 2009-02-28
forum: Multimedia Software
---

### Post by rgrimard on 2009-02-28
I ripped a bunch of miniDVs to DV files using Kino.  They are stored on a shared drive at home.  I can't read the dv files from my Windows XP box.  I tried a few codec packs with no luck.  Any ideas?

This is what ubuntu outputs for the file spec on one dv file:
Duration: 00:00:14.3, start: 0.000000, bitrate: 28771 kb/s
Stream #0.0: Video: dvvideo, yuv411p, 720x480, 28771 kb/s, 29.97 fps(r)
Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, 1024 kb/s
Stream #0.2: Audio: pcm_s16le, 32000 Hz, stereo, 1024 kb/s

---

### Post by amauk on 2009-02-28
Use VLC on windows

window media player does not support DV streams
(you can hack them into AVI files, but there's downsides to doing that)

VLC's the way to go

---

### Post by rgrimard on 2009-02-28
> **amauk said:**
> Use VLC on windows

window media player does not support DV streams
(you can hack them into AVI files, but there's downsides to doing that)

VLC's the way to go

Does anyone know of a way to convert them to DV avi to allow Windows Movie Maker and other software to decode?

---

### Post by amauk on 2009-02-28
```
ffmpeg -i ./dv_file.dv ./dv_file.avi
```should work ok

---

### Post by rgrimard on 2009-02-28
> **amauk said:**
> ```
ffmpeg -i ./dv_file.dv ./dv_file.avi
```should work ok

You mentioned "issues" with converting.  Is there any difference between using ffmpeg to convert to dv avi and using say Windows Movie Maker to rip directly from tape?

---

### Post by rgrimard on 2009-02-28
> **amauk said:**
> ```
ffmpeg -i ./dv_file.dv ./dv_file.avi
```should work ok

That didn't work.  It created an avi that was 40x smaller than the original dv.  Windows Media Player could not read it.

---

### Post by rgrimard on 2009-02-28
> **rgrimard said:**
> That didn't work.  It created an avi that was 40x smaller than the original dv.  Windows Media Player could not read it.

Let me start over with my issue.  I have some DV files which were ripped via Kino on Ubuntu.  I have DV files which were ripped with Windows Movie Maker on Windows XP.  Both are playable on their respective OS.  I'd like to be able to play the Kino-ripped DVs on my Windows XP box.  Windows Movie Maker rips the miniDVs to DV-AVI.  The size of the rips are roughly the same for a full miniDV so I'm assuming the DV-avi is not missing any data (lossless and uncompressed).

My question:  Is there a way to convert the DVs ripped from Kino to DV-AVI?  

The ffmpeg convert created an avi file 40x smaller than the DV file.  I tried winff and it allows you to create DV from DV.  The result was not playable in Windows Media Player.  I also used winff to create an avi and again it was 40x smaller than the DV file.

---

