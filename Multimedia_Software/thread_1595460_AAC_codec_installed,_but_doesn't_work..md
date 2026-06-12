---
title: "AAC codec installed, but doesn't work."
date: 2010-10-13
forum: Multimedia Software
---

### Post by Ric95 on 2010-10-13
I'm running xubuntu 10.04 and I've installed media codecs as per the " Comprehensive Multimedia & Video Howto " thread. I also have faac, libfaac0, faad, and libfaad2 installed. 
But when viewing some videos or trying to transcode to anything with the aac codec I get the "no AAC" error.. 
How can I fix this?

---

### Post by FakeOutdoorsman on 2010-10-13
What are you using to transcode?  You need to manually enable AAC encoding with FFmpeg for 10.04.  See Option C in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Ric95 on 2010-10-13
Well that was obvious enough. 
I was sure I had medibuntu installed, but I re-ran option C and now it works. 
Thanks Fakeoutdoorsman. ( btw, cool name. funny.)

---

