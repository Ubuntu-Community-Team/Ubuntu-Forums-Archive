---
title: "Anyone know of a working 3g2 to avi converter?"
date: 2009-08-14
forum: Multimedia Software
---

### Post by david_lynch on 2009-08-14
I've been searching for a conversion utility to convert 3g2 video files (from a phone camera) to something more universally viewable e.g. avi.

I've tried a couple of products that didn't work (only support 3gp files, not 3g2) and I found one that partially works (t@bencode) but it converts video only, without sound.

Does anyone know of a complete solution for ubuntu?

---

### Post by andrew.46 on 2009-08-15
Hi david_lynch,

> **david_lynch said:**
> I've been searching for a conversion utility to convert 3g2 video files (from a phone camera) to something more universally viewable e.g. avi.

FFmpeg will convert these files but it really depends what codecs are in the 3g2 container. Usually there will be h263 video but for sound there will be a choice of aac or amr sound.

Could you install a copy of FFmpeg according to this guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and interrogate one of your files as follows:

```
ffmpeg -i **[COLOR="Red"]myfile.3g2[/COLOR]**
```

If the audio comes back as aac it will be easy to convert, if it comes back as amr it will not be so easy :-).

Andrew

---

