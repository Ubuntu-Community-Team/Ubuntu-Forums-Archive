---
title: "Concatenate videos without re-rendering?"
date: 2009-12-25
forum: Multimedia Software
---

### Post by rslee on 2009-12-25
I have a Flip MinoHD camcorder and I'd like to be able to string a series of video files together without re-rendering them.  I'm assuming this is possible if the files all use the same container and codecs.

If not, is there a way to have Pitivi maintain the original h.264 data?  Or what are good bitrate/quality settings to use if I'm mostly going to be uploading videos to YouTube/Facebook/etc.?

Thanks!

---

### Post by FakeOutdoorsman on 2009-12-28
> **rslee said:**
> I have a Flip MinoHD camcorder and I'd like to be able to string a series of video files together without re-rendering them.  I'm assuming this is possible if the files all use the same container and codecs.
You can try MP4Box to concatenate several MP4 files.  It is part of the **gpac** package:
```
MP4Box -cat input1.mp4 -cat input2.mp4 -cat input3.mp4 output.mp4
```
I'm unsure what types of formats MP4Box accepts as inputs.
> **rslee said:**
> Or what are good bitrate/quality settings to use if I'm mostly going to be uploading videos to YouTube/Facebook/etc.?
I believe YouTube uses FFmpeg to decode videos (I could be wrong) so it can accept a huge variety of formats.  You will want to upload the highest quality video you have (which can depend on your bandwidth, upload speed, patience, hard drive space, etc) because YouTube and Facebook are going to re-encode it anyway.  You may have to re-encode your video due to some sort of constraint. For example I sometimes use the lossless huffyuv encoder, but the resulting file can be huge.  My last video file was around 30 GB.  A good encoding setting could be:
```
ffmpeg -i input -acodec libfaac -ac 2 -ab 192k -vcodec libx264 -vpre hq -crf 18 -threads 0 output.mp4
```
If that takes too long, change *-vpre hq* to *-vpre normal*.  To use this command, you may have to enable some restricted encoders:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

If you're going to be uploading more than a few videos, then I recommend compiling FFmpeg and x264 to take advantage of the latest quality enhancements that are lacking in the repository versions.  This option is described in the link above.

---

### Post by Valeryan_24 on 2010-01-03
Hello,

I have a similar question regarding Pitivi :

Is it possible to mix different videos with have exactly same dimensions 
and resolution : I mean just concatenate / join them, without rendering 
codecs.

Ex: video A.avi, 8 minutes and video B.avi, 12 minutes (which can be 2 
parts exctracted of a global film)

I want to join video A and B to one avi video file which would read A+B 
following automatically, for a total lenght of 20 minutes.

In Avidemux for example, it is very easy : open video A, add video B, 
and register, it takes only a few seconds...

I tried same thing in Pitivi, but I found only project with video codec 
theoraenc, audio codec vorbisenc preferences, and re-rendering, it took 
more than 8 minutes, used CPU etc...

As Pitivi is much more complete, flexible and GUI-easy than Avidemux, as 
it should be included as default in the next versions of Ubuntu, I'd 
like to switch on it, but I need this very basic feature.

Did I make something wrong, and if yes how to do this concatenating ?

Thanks in advance for your help. :)

---

### Post by Valeryan_24 on 2010-01-04
Answer received on Pitivi mailing list :

[I]Currently rendering will decode and reencode all the files.

  Rendering without decoding/encoding is only possible if:
  (1) the source files are used from the beginning of a GOP (i.e. starts
with a keyframe) to the end of a GOP (i.e. just before a keyframe or at
the end of the file)
  (2) AND no effects are applied (no volume modification, no alpha
modification, no blending, NOTHING)
  (3) AND the source files are 100% the same (same codecs, same
width/heigh/bitrate/profile/level/depth,...)

  It is planned.. but is not a top priority right now since to properly
implement this in PiTiVi you need detection of the above 3 requirements
(item 2 could be trivial, the other ones are a bit trickier).

  [There is] a script to concatenate parts of qt/h264 files using GNonLin (without decoding) and it apparently works fine.
[/I]

---

### Post by x2305andy2305x on 2011-07-08
Hi, I'm also interested in how to concat x264 encoded mp4s, encoded with FFMPEG.

I've tried MP4Box but the results are not good. Sometimes the output mp4 has the first video used in the concatenation looped twice at the start. And noneof the mp4s outputted by MP4Box are qt-faststart-able. This would mean there's a problem right?

Reprocessing the MP4Box output file with ffmpeg (-vcodec copy) also yields some interesting outputs, sometimes it works, sometimes it only outputs a broken mp4 as large as the first file that had been used in the original concat.

Any ideas?

---

