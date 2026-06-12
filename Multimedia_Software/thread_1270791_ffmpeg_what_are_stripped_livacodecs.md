---
title: "ffmpeg: what are stripped livacodecs ?"
date: 2009-09-20
forum: Multimedia Software
---

### Post by onespeedbiker on 2009-09-20
I loaded up ffmpeg from your Multimedia Sticky and it seems to be working (I still have some issues with some videos where the widescreen plays like a full screen, but cuts off the ends). Anyway my question is what is the difference between livacodec-unstripped-52 and   livacodec52. I have some stripped and some unstripped libs on my computer. When I tried to install the unstripped version, Software sources says I have to uninstall the (stripped?) version. What's this all about?

---

### Post by andrew.46 on 2009-09-20
Hi onespeedbiker,

This is comprehensively explained here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

But the basics are that Ubuntu removes some codecs from libavcodec and calls this a 'stripped' version while a more complete version is called 'unstripped'. But FakeOutdoorsman explains it a lot better :)

Andrew

---

### Post by onespeedbiker on 2009-09-20
> **andrew.46 said:**
> Hi onespeedbiker,

This is comprehensively explained here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

But the basics are that Ubuntu removes some codecs from libavcodec and calls this a 'stripped' version while a more complete version is called 'unstripped'. But FakeOutdoorsman explains it a lot better :)

Andrew Thanks Andrew; now I know!

---

