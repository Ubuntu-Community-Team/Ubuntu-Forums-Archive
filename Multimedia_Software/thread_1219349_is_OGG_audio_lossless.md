---
title: "is OGG audio lossless?"
date: 2009-07-21
forum: Multimedia Software
---

### Post by raymondvillain on 2009-07-21
I am in the process of ripping the audio track from a DVD.  Using transcode.

I thought I would like the sound track to be in the FLAC format.  But all the examples for transcode show the use of the ogg format.

Are *.ogg files lossless?  That is, if the audio track was made with a 16 bit Analog to Digital converter, are all 16 bits encoded in the ogg format?  Or is there some sort of algorithm used to provide high fidelity sound but the result is not actually "lossless"?

I googled ogg and got gobs of pages with tons of jargon but no clear explanation of the underlying math.

---

### Post by az on 2009-07-21
> **raymondvillain said:**
> I am in the process of ripping the audio track from a DVD.  Using transcode.

I thought I would like the sound track to be in the FLAC format.  But all the examples for transcode show the use of the ogg format.

Are *.ogg files lossless?  That is, if the audio track was made with a 16 bit Analog to Digital converter, are all 16 bits encoded in the ogg format?  Or is there some sort of algorithm used to provide high fidelity sound but the result is not actually "lossless"?

I googled ogg and got gobs of pages with tons of jargon but no clear explanation of the underlying math.

It's lossy and slightly more efficient than mp3.

Edit:

Ogg is a container for a variety of codecs.  Typically, an "ogg" file refers to ogg-vorbis, a lossy audio codec.  But an ogg file may contain an audio stream compressed with FLAC (lossless).

[http://en.wikipedia.org/wiki/Ogg](http://en.wikipedia.org/wiki/Ogg)

---

### Post by raymondvillain on 2009-07-21
Thank you, az.

I will pursue FLAC with transcode.

Edit:  I think my question is well answered so I'm marking this solved.

---

