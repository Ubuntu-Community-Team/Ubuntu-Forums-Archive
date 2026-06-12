---
title: "Fuzzy Camcorder Video"
date: 2010-08-21
forum: Multimedia Software
---

### Post by Joshun on 2010-08-21
Hi,

I have a Canon Legria FS307 Camcorder. It records to a .mod file, which is a standard mpeg2 video file. However, when the file is played back on ubuntu, it is really fuzzy, with the exception of the kaffeine multimedia player, which plays it back perfectly.

I have attached some screenshots to illustrate the problem.

Please could somebody help with this.

Joshun

---

### Post by Joshun on 2010-08-21
When rendered to different formats, the picture is still blurry if you render it to PAL, but if you render it to NTSC, the picture is perfect. This is incredibly unusual as it is a PAL camera.

---

### Post by sgtGarcia on 2010-08-21
Maybe - but this would be very weird - it is interlaced and kaffeine have set deinterlace default on. :?::?::?:
Try to switch on deinterlacer in VLC.

edit:

I see on the first pic that it is interlaced.

---

### Post by Joshun on 2010-08-22
Yes, kaffeine enables deinterlace by default, which is what improves the picture. I can confirm this because turning on deinterlace in the xine player also makes a perfect picture :D:KS. Is this normal behaviour, that deinterlace should have to be turned on in order to produce a good picture?

---

### Post by DrMelon on 2010-08-22
> **Joshun said:**
> Yes, kaffeine enables deinterlace by default, which is what improves the picture. I can confirm this because turning on deinterlace in the xine player also makes a perfect picture :D:KS. Is this normal behaviour, that deinterlace should have to be turned on in order to produce a good picture?
It's fairly normal for some older models of camcorder. Newer ones don't have this issue.

---

### Post by Joshun on 2010-08-22
It's a very new camcorder though. Anyway adding the -deinterlace option in transcode enables me to convert the video to non interlaced before rendering, which is a little annoying, but kindoff solves my problem.

---

