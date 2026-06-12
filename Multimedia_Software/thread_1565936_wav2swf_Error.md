---
title: "wav2swf Error"
date: 2010-09-01
forum: Multimedia Software
---

### Post by Solomoriah on 2010-09-01
I installed the wav2swf command on a Jaunty system, and tried to convert a wav file to swf with it (duh).  This is what I get:

root@XXXXX:/var/www/blocked# wav2swf -o alert1.swf alert1.wav
Error: no mp3 soundstream support compiled in.

Here's what the file command has to say about the wav file:

alert1.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 8 bit, mono 11025 Hz

So, not an MP3.  What gives?

---

### Post by garyedwardjohnston on 2010-09-01
[http://manpages.ubuntu.com/manpages/hardy/man1/wav2swf.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/wav2swf.1.html)

---

### Post by Solomoriah on 2010-09-01
Yes, I READ the man page.  I'm not stupid enough to post here without first RTFM.  But it doesn't describe this error, nor include any information related to the problem.

---

### Post by garyedwardjohnston on 2010-09-02
how about this

[http://www.swftools.org/](http://www.swftools.org/)

---

### Post by Solomoriah on 2010-09-02
Yeah, I figured it out.  The Ubuntu package wasn't compiled with libmp3lame support, so it can't work.  Silly.  I downloaded the source and built it directly, and it works fine.

---

