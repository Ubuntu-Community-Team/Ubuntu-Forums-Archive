---
title: "IMA4 converter?"
date: 2009-07-25
forum: Multimedia Software
---

### Post by mfleming on 2009-07-25
Hi,

I am looking for a converter for audio in Apple IMA4 data format, with a file format of CAF. I would like to convert it to AU, AIFF, or WAV. So far the only program I have found that can do this is afconvert, which is part of OS X, but I would like to do the conversion in Ubuntu. 

Thanks,

Matthew Fleming

---

### Post by andrew.46 on 2009-07-26
Hi mfleming,

> **mfleming said:**
> I am looking for a converter for audio in Apple IMA4 data format, with a file format of CAF. I would like to convert it to AU, AIFF, or WAV. So far the only program I have found that can do this is afconvert, which is part of OS X, but I would like to do the conversion in Ubuntu. 

I have not tested this but it looks as if SoX can handle this format:

```

andrew@skamandros~$ sox | grep 'AUDIO FILE FORMATS'
Failed: Not enough input filenames specified

AUDIO FILE FORMATS: 8svx aif aifc **[COLOR="Red"]aiff[/COLOR]** aiffc al amb **[COLOR="Red"]au[/COLOR]** avr 
**[COLOR="Red"]caf[/COLOR]** cdda cdr cvs cvsd dat dvms f4 f8 fap 
flac fssd gsm hcom htk ima ircam la lpc lpc10 lu mat mat4 mat5 maud 
mp2 mp3 nist ogg paf prc pvf raw s1 s2 s3 s4 sb sd2 sds sf sl smp 
snd sndfile sndr sndt sou sox sph sw txw u1 u2 u3 u4 ub ul uw vms
 voc vorbis vox w64 **[COLOR="Red"]wav[/COLOR]** wavpcm wv wve xa xi

```

All the best,

Andrew

---

### Post by neilobremski on 2011-03-17
Unfortunately, this doesn't work for CAF containing IMA4, as I've been finding. My friend has an iPad with some application that only generates these frustrating CAF's that (peering in with a hex editor) contain IMA4 audio streams. The CAF container itself is supported by GStreamer / FFMPEG, Audacity, SOX, etc. but this particular codec is not.

```
neilo@sleeepnow:~/Music$ sox closing_losing_theme.caf test.wav
sox FAIL formats: can't open input file `closing_losing_theme.caf': Supported file format but unsupported encoding.

```

When opening in Audacity the extra error info (when clicking help) incorrectly reports "wma-proprietary". And FFMPEG simply says it doesn't know WTF the file is.

Grr. Argh.

---

### Post by andrew.46 on 2011-03-17
> **neilobremski said:**
> Unfortunately, this doesn't work for CAF containing IMA4, as I've been finding.

Can you post a sample somewhere?

Andrew

---

