---
title: "Burning an iso audio image with a .inst header"
date: 2010-06-01
forum: Multimedia Software
---

### Post by phoenix12345 on 2010-06-01
I've bought Earthworm Jim 1&2 from gog.com thinking that i could play it on my old Pentium 2 computer running DOS.

The problem is the game requires it's soundtrack CD, which is suplied by GOG in the form an ISO image with a .inst file that acts as some kind of header(just like a cue file is to a bin image). It contains details about the tracks. But i have no ideea how to burn it. Brasero will burn it, but it's unreadable. K3B doesn't seem to like it.

DOSBox has no problem mounting this type of image, and the game works fine after i've mounted the image.

So the question is, how should i burn this type of file(ISO Audio Image with .inst header)?

I'll also post the contents of the .inst file
```
FILE "EWJ1.gog" BINARY
  TRACK 01 MODE1/2352
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    INDEX 01 00:02:21
  TRACK 03 AUDIO
    INDEX 01 05:19:37
  TRACK 04 AUDIO
    INDEX 01 10:57:09
  TRACK 05 AUDIO
    INDEX 01 17:27:21
  TRACK 06 AUDIO
    INDEX 01 24:38:13
  TRACK 07 AUDIO
    INDEX 01 29:48:64
  TRACK 08 AUDIO
    INDEX 01 33:31:56
  TRACK 09 AUDIO
    INDEX 01 34:30:27
  TRACK 10 AUDIO
    INDEX 01 41:27:24
  TRACK 11 AUDIO
    INDEX 01 44:41:33
  TRACK 12 AUDIO
    INDEX 01 48:12:26
  TRACK 13 AUDIO
    INDEX 01 53:48:57
  TRACK 14 AUDIO
    INDEX 01 54:03:16
  TRACK 15 AUDIO
    INDEX 01 61:19:22
  TRACK 16 AUDIO
    INDEX 01 61:26:71
  TRACK 17 AUDIO
    INDEX 01 62:47:22
```

---

### Post by phoenix12345 on 2010-06-01
It turns out the .inst file was actually a CUE file in disguise, and the other file was a BIN file, not ISO. All i've done is change the extension and K3B reads it.

---

### Post by pricetech on 2010-06-01
Cool.  Don't forget to mark your thread as solved.  Maybe someone will profit from your discovery.

---

