---
title: "ffmpeg configuration: --enable-libmp3lame by default?"
date: 2009-03-20
forum: Multimedia Software
---

### Post by men28 on 2009-03-20
Hi!

About two hours ago I have installed ffmpeg from Ubuntu Hardy Heron repository. I didn't compile the program. 

I noticed there is --enable-libmp3lame in configuration string. It is enabled by default.

I don't understand it. mp3 is a proprietary file format and Linux didn't like it and this option was disabled by default.

Was something changed about mp3 format or this was just a mistake?

---

### Post by FakeOutdoorsman on 2009-03-20
Do you have the Medibuntu repository enabled?  Hardy's FFmpeg from the Medubuntu repository has "--enable-libmp3lame", but FFmpeg from the Ubuntu repository does not last I checked.

---

### Post by men28 on 2009-03-21
Yes! I have medibuntu repository enabled.
This was a cause.

Thank you!

---

### Post by tchab2 on 2009-12-10
How can I update default settings

---

