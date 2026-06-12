---
title: "Missing /dev/audio file"
date: 2011-03-30
forum: Multimedia Software
---

### Post by rfb13 on 2011-03-30
I'm trying to run a program on Maverick Meerkat but I keep getting the following error:  "xcwcp: cannot set up soundcard sound
/dev/audio: No such file or directory".  

I searched my file system, and there is indeed no such file or directory called /dev/audio.  

Thus my question(s):  Where is this file?  If I don't have it, how do I get it or create it?  

Thanks for any help.

Randy - K8HRO

---

### Post by andrewkk on 2011-07-24
Also looking for the answer to this question.

---

### Post by vale4674 on 2011-11-30
Same here. Audio is so strange on Linux. I use VLC for recording and sometimes I can record, sometimes I can't.

---

### Post by MoreOrLess on 2011-11-30
/dev/audio is the legacy OSS device, which hasn't been supported in Ubuntu since 10.04. You should set VLC to use ALSA or pulseaudio to record. VLC's autodetect may only work randomly.

---

