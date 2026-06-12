---
title: "Microsoft Lifecam Cinema audio sync issues"
date: 2011-01-05
forum: Multimedia Software
---

### Post by kingsqueak on 2011-01-05
Does anyone have any tips for getting the audio synced with the video when recording from a MS Lifecam Cinema?

I've tried guvcview, ffmpeg, vlc, they all have the issue so far.

The video is badly out of sync with the audio.

Full one-liners that are working would be great.

I know very little about video in general and have tried toggling options around but haven't found my 'missing link' combination yet.

I've tried varying resolutions from 320x240 to vga to full 720p res.  I've toggled around various options for encoding in guvcview...though 'blindly'.

Same hardware (Atom 330 box with 4G in it) with Win7 handles full 720p recording with no problems at all so it's not just the lightweight box I'm running I don't think.

My desired result is just to make video clips in some 'standard' format, that can be shared easily...mpg avi, whatever will work.

I'm running 10.04 32bit on this box.

---

### Post by kingsqueak on 2011-01-05
I made some progress.  I got guvcview to work with the following options.

15/1 fps
640x360
YUYV output

YUY2 - uncomp YUV vid codec
AVI for vid format.

I still haven't figured out how to do the equivalent using ffmpeg.

I think now that my issue may be that I'm trying to encode/compress on the fly.  What I really want is whatever will be the least overhead 'raw' format to dump to disk.  I can compress/convert later.

Still confused with all the codec and file format information.

---

