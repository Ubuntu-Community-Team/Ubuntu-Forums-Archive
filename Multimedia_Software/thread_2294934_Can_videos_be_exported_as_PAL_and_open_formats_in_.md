---
title: "Can videos be exported as PAL and open formats in Lives video editor?"
date: 2015-09-14
forum: Multimedia Software
---

### Post by Rytron on 2015-09-14
Hi to all at UF.

I exported a video in Lives to its non-open lossless format and then converted to an open format (VP8 and Vorbis) in Handbrake. I used MediaInfo and noticed it said (NTSC). I want PAL (or for it not to say 'NTSC' at least) as I am in Europe. Lives not Handbrake added the NTSC part seemingly.

Thanks.

---

### Post by salsaman2 on 2015-09-14
Hi, main developer of LiVES here. LiVES can encode to over 50 different formats, both open and proprietary. In answer to your question, the difference between PAL and NTSC really only exists for proprietary formats (h264 or mpeg). For open formats (e.g. ogg/theora/vorbis) there is no distinction between PAL and NTSC. 

LiVES offers 2 fully lossless formats, one of these is ffv1 which is part of ffmpeg, the other is lossless dirac (dirac/vorbis/mkv). Neither of these are proprietary, nor do they differ between PAL and NTSC.

I don't understand your comment because LiVES does not have a non-open lossless format.

---

### Post by Rytron on 2015-09-15
> **salsaman2 said:**
> Hi, main developer of LiVES here. LiVES can encode to over 50 different formats, both open and proprietary. In answer to your question, the difference between PAL and NTSC really only exists for proprietary formats (h264 or mpeg). For open formats (e.g. ogg/theora/vorbis) there is no distinction between PAL and NTSC. 

LiVES offers 2 fully lossless formats, one of these is ffv1 which is part of ffmpeg, the other is lossless dirac (dirac/vorbis/mkv). Neither of these are proprietary, nor do they differ between PAL and NTSC.

I don't understand your comment because LiVES does not have a non-open lossless format.

Hi salsaman2.

I stand corrected re there being no lossless non-open format in Lives. Thanks for the info re open formats with having no distinction between PAL and NTSC.

---

