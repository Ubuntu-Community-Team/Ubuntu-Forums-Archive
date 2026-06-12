---
title: "amarok and xine can't play ogg vorbis audio"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by v-gudmk on 2006-07-29
I can't play my .ogg files in amarok.  Amarok uses the xine sound system engine.  Amarok doesn't give me any useful error messages.

So I tried to play the file in gxine and I get this:

libvorbis: this bitstream does not contain vorbis audio data.

xmss has no problems playing the same file.

I have gxine 0.5.1 (0.5.1-0ubuntu15; Ubuntu), and libvorbis0a 1.1.2-0ubuntu2.

Any ideas?

---

### Post by Lord Illidan on 2006-07-29
Are you sure it is an .ogg file? Amarok and xine should play ogg vorbis right off...

Try playing it with totem.

---

### Post by v-gudmk on 2006-07-29
My .ogg files are in fact really encoded with ogg vorbis:

file <somefile>.ogg
gives this output:

Ogg data, Vorbis audio, stereo, 44100 Hz, ~0 bps, created by: Xiphophorus libVorbis I (1.0 beta 1 or beta 2).

I think I'm running into the same problem that [this guy]("http://ubuntuforums.org/showthread.php?t=204396") describes.

I encoded my files years ago.  

I tried converting one of my mp3 files with mp32ogg.  The result is:
Ogg data, Vorbis audio, stereo, 44100 Hz, ~160000 bps, created by: Xiph.O
rg libVorbis I.

This file plays in xine.

So it looks like I'll have to find a way to re-encode my files in a newer version of the encoding.  Which pretty much sucks.

---

### Post by v-gudmk on 2006-07-30
So I decided to re-encode all my .ogg files.
Using the attached script, I did this:

find . -name \*.ogg -exec ogg2ogg "{}" \;

Now I can play my files with xine and amarok.

---

