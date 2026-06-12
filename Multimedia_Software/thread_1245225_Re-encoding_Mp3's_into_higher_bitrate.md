---
title: "Re-encoding Mp3's into higher bitrate"
date: 2009-08-20
forum: Multimedia Software
---

### Post by arky on 2009-08-20
My Creative MuVo2 doesn't seems to play mp3 with 16 kbps, can anyone suggest the command to re-encoding it to higher bitrate with mencoder or other program.

---

### Post by Major_Kong on 2009-08-20
> **arky said:**
> My Creative MuVo2 doesn't seems to play mp3 with 16 kbps, can anyone suggest the command to re-encoding it to higher bitrate with mencoder or other program.

You could just install Sound Converter.

But if you want to do it from the command line, install lame, and then:

lame -b 32 input.mp3 output.mp3

---

### Post by HavocXphere on 2009-08-20
Chances are that the problem is not the bitrate but rather the bitrate "type". i.e CBR, VBR etc

---

### Post by cascade9 on 2009-08-20
16 kbs? o.O  You mean 160k, I hope. 

BTW, transcoding from mp3-> mp3 is never a good idea, only do it IF you cant find the original CD you ripped it from (or cant find it where ever you get your music from)

---

### Post by arky on 2009-08-20
Thanks, lame does the encoding.

---

