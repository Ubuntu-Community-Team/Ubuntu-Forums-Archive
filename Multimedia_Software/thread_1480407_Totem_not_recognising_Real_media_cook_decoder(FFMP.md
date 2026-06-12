---
title: "Totem not recognising Real media cook decoder(FFMPEG) Lucid"
date: 2010-05-11
forum: Multimedia Software
---

### Post by madubuntuer on 2010-05-11
Hi I'm having trouble with playing a sample rmvb file. I know for sure it has a G2 audio codec.

When I try loading it into totem it says the codec is missing but 
The gst-inspect command is telling me I do have it installed.

steven@dad-desktop:~$ gst-inspect-0.10 |grep cook
ffmpeg:  ffdec_cook: FFmpeg COOK decoder

Why does it bring up the search for codecs dialog then?

---

