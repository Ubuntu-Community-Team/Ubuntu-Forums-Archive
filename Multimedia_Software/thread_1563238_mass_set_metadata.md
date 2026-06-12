---
title: "mass set metadata"
date: 2010-08-28
forum: Multimedia Software
---

### Post by mikmikmikmik on 2010-08-28
i have ripped an audio-book and then converted all the files to wav with sox, and none of them have metadata! i would be fine with this except that the only reason i converted them is so that i can play them on my mp3 player, which doesn't support ogg but does support wav and sox doesn't support mp3, so, i converted them all to wav. however, the mp3 player is going through them in alphabetical order, which means: chapter 1 then chapter 10. i know that if they all simply had track numbers in the metadata then it would do it right. each file is named like: "Disc 1 - 11 - chaptername 5" and i want the metadata to be accordingly for each: artist: stepenie meyer, album:twilight - chaptername ,track number:5 baisicly i want it to write new metadata according to parts of the filename
 
any ideas?
 
Ps: ive looked at jamu, it doesn't seem like the right thing, but i might be wrong

---

### Post by ron999 on 2010-08-28
I don't think that wav files have metadata.:(

---

### Post by andrew.46 on 2010-08-30
Hi mik,

> **mikmikmikmik said:**
> ... and sox doesn't support mp3 ...

It may be of very little assistance to your main question but you may be interested to know that sox *does* in fact support mp3. The following shows the conversion of an ogg vorbis file to mp3 using sox:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]sox -V3 --show-progress test.ogg test.mp3[/COLOR]**
sox: SoX v14.3.0
sox INFO formats: detected file format type `vorbis'

**[COLOR="Red"]Input File     : 'test.ogg'[/COLOR]**
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:06:05.24 = 16107264 samples = 27393.3 CDDA sectors
File Size      : 4.94M
Bit Rate       : 108k
Sample Encoding: Vorbis
Comment        : 'encoder=Lavc52.87.0'


**[COLOR="Red"]Output File    : 'test.mp3'[/COLOR]**
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:06:05.24 = 16107264 samples = 27393.3 CDDA sectors
Sample Encoding: MPEG audio (layer I, II or III)
Comment        : 'encoder=Lavc52.87.0'

sox INFO sox: effects chain: input      44100Hz 2 channels
sox INFO sox: effects chain: output     44100Hz 2 channels
In:100%  00:06:05.24 [00:00:00.00] Out:16.1M [      |      ]        Clip:0    
Done.

```

The ability to transcode to mp3 has been removed by Debian and Ubuntu packagers due to licensing issues.

Andrew

---

