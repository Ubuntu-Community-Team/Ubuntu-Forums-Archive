---
title: "Encoding/decoding raw PCM data"
date: 2008-06-26
forum: Multimedia Software
---

### Post by &amp;)ky#)^ on 2008-06-26
I'm currently trying to determine how PCM data is stored.  I can't find any in-depth information about it on the web.  Can someone help me?  Here's what I'm trying to determine.  How does the binary data in a raw PCM file or stream correlate to the sound that it represents?  I understand that the bit rate determines how much data there will be for a given length of time, but what is the data?  Please, if you can answer this question for me or direct me to the answer, I'd really appreciate it.

---

### Post by mcduck on 2008-06-26
The data is the amplitude of the sound signal.

So, for basic 16-bit 44,1Khz PCM file the content describes the amplitude of the signal as a 16-bit integer, 44100 times per second.

---

### Post by &amp;)ky#)^ on 2008-06-26
So, all the binary data is describing is the amplitude at different points in the sample?

---

### Post by mcduck on 2008-06-26
Yes. Although I don't know the exact details of the file format, but that's the basic idea in pulse code modulation.

edit: wikipedia has a nice graphical presentation of a 4-bit PCM: [http://en.wikipedia.org/wiki/Image:Pcm.svg]("http://en.wikipedia.org/wiki/Image:Pcm.svg")

To make things more complex there are actually many different variations of PCM like DPCM and ADPCM, and many diferent PCM standards for different purposes..

---

