---
title: "Music player or method to send audio DIRECTLY to digital out, bit perfect"
date: 2010-01-16
forum: Multimedia Software
---

### Post by linuxwalker on 2010-01-16
My soundcard has both coaxiable cable and fiber optic SPDIF-outs. I just bought my first external digital-anaolog-converter because I wanted more audiophile sound along with the new speakers that I bought..my first step up from computer speakers to real speakers.

My DAC has indicator lights showing the incoming sample rate. And usually it is 44.1khz. But I wonder why that is when the file I play is sometimes higher, like a 96khz FLAC file I have.

I also use foobar2000 (through WINE) and there, with the PPHS resampler set to 96khz or 192khz, the DAC always shows an incoming rate of 44.1khz.

So somewhere after the song is decoded, ubuntu is downsampling it back to 44.1khz it looks like.


I've realized the foobar2000 thing is probably influenced by WINE itself, as that is another level of complexity the audio has to go through before it goes out to the soundcard.

But even not using foobar2000 and playing mp3s in Totem, it still always outputs at 44.1khz, even with 96khz music files.


Is there a player for ubuntu designed for bit-perfect output and no messing with the sound data? Is there a way to tell ubuntu not to touch that PCM stream?

---

