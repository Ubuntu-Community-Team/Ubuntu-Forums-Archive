---
title: "Video Blogging and Camcorders"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by kd5tmu on 2008-01-25
Folks,
I am looking for a way to do the following in Ubuntu so I can finally get out of windows for good:
-Capture video from my camcorder
-Edit and add titles and sounds/songs
-Save video in a YouTube suitable format with a file size that I specify (usually under 100MB)


KINO will capture the video, but a 4 minute video takes 600MB!!!!  Windows Movie maker will capture the same video and add stuff to it for 40MB!

HELP!!!!  I need to get back to vlogging!

---

### Post by eye208 on 2008-01-25
> **kd5tmu said:**
> KINO will capture the video, but a 4 minute video takes 600MB!!!!  Windows Movie maker will capture the same video and add stuff to it for 40MB!
20 MBit/s is actually [rather low](http://en.wikipedia.org/wiki/DV#Video_compression) a bitrate for DV. Kino imports the uncompressed data, but that doesn't mean you can't compress it later.

During editing, working with uncompressed video has several benefits. DV is large because it is an intraframe-based format, i.e. each frame is stored independently from others. This makes scrubbing, cutting and editing the parts very easy and fast.

When I edit video in Blender, I usually work with separate frames in JPEG format. This is considerably smaller than DV without degrading quality too much. I'm not sure if Kino can be used in the same way.

---

### Post by kd5tmu on 2008-01-25
> **eye208 said:**
> 20 MBit/s is actually [rather low](http://en.wikipedia.org/wiki/DV#Video_compression) a bitrate for DV. Kino imports the uncompressed data, but that doesn't mean you can't compress it later.

During editing, working with uncompressed video has several benefits. DV is large because it is an intraframe-based format, i.e. each frame is stored independently from others. This makes scrubbing, cutting and editing the parts very easy and fast.

When I edit video in Blender, I usually work with separate frames in JPEG format. This is considerably smaller than DV without degrading quality too much. I'm not sure if Kino can be used in the same way.

Know you of a program that will compress the *.avi into the size I need?

---

### Post by philc on 2008-01-25
> **kd5tmu said:**
> Know you of a program that will compress the *.avi into the size I need?

There are several.

For command line tools FFmpeg or Mencoder will work well, but there's quite a learning curve to understand all the options available.

For GUI based tools, try Avidemux or look in the Multimedia Production category on these boards for Fuoco and Convert IT

---

### Post by eye208 on 2008-01-25
> **kd5tmu said:**
> Know you of a program that will compress the *.avi into the size I need?
It depends on your desired target format. I use MEncoder and MP4Box to make Quicktime-compatible MP4 files containing H.264 video and AAC audio. This is kind of overkill though if your target platform is Youtube. If you want to go for something better than Youtube quality, I'd recommend [Blip.tv](http://blip.tv/). They let you upload files in your own preferred format and won't touch them. Youtube always converts to low quality FLV (Flash video). Blip.tv does a similar conversion, but the original file remains accessible even by URL. This way you can insert it into your blog using the Flash plugin and e.g. [FlowPlayer](http://flowplayer.org/). (The latest Flash plugin supports MP4, H.264 and AAC formats.)

---

