---
title: "screencast with ffmpeg"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by fifa255 on 2007-07-26
I'm trying to use ffmpeg to create a screencast but do so by capturing rawvideo from the x11 display and then encode it later.  I have tried other programs like xvidcap and recordmydesktop but they produce choppy video with lots of dropped frame rates as I am trying to capture my 1600x1200 desktop at 25fps.  I have already compiled ffmpeg with x11grab support enabled and can capture video of my desktop and encode with mpeg4 on the fly.

I followed this tutorial on compiling with x11grab support [http://www.howforge.com/rebuilding-ffmpeg-to-create-screencast-in-ubuntu](http://www.howforge.com/rebuilding-ffmpeg-to-create-screencast-in-ubuntu)

I was able to capture video encoded in mpeg4 format but with low fps and choppy video with this command:
ffmpeg -vcodec mpeg4 -b 1000 -r 10 -g 300 -vd x11:0,0 -s 1280x768 -an test.avi
screenshot below

However because of the low fps I was trying to get raw capture using the 'rawvideo' or 'copy' for the vcodec argument but I get the following problems
-----------------------------------------------
ffmpeg -vcodec copy -b 1000 -r 10 -g 300 -vd x11:0,0 -an -s 1280x1024 test.avi

ffmpeg version CVS, build 3342336, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-ldflags=-L/usr/X11R6/lib --enable-x11grab --enable-gpl 
  built on Jul 26 2007 17:57:02, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
File 'test.avi' already exists. Overwrite ? [y/N] y
device: x11:0,0 -> x: 0 y: 0 width: 0 height: 0
x11grab: AVParameters don't have any video size. Use -s.
Could not find video grab device
------------------------------------------
ffmpeg -vcodec rawvideo -b 1000 -r 10 -g 300 -vd x11:0,0 -an -s 1280x1024 test.avi

ffmpeg version CVS, build 3342336, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-ldflags=-L/usr/X11R6/lib --enable-x11grab --enable-gpl 
  built on Jul 26 2007 17:57:02, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
File 'test.avi' already exists. Overwrite ? [y/N] y
device: x11:0,0 -> x: 0 y: 0 width: 1280 height: 1024
x11grab: shared memory extension found
Input #0, x11grab, from '':
  Duration: N/A, bitrate: N/A
  Stream #0.0, 10.00 fps: Video: rawvideo, rgba32, 1280x1024, 419430 kb/s
Output #0, avi, to 'test.avi':
  Stream #0.0,   nan fps: Video: rawvideo, 1280x1024, q=2-31, 1000 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    0 q=0.0 Lsize=       5kB time=10000000000.0 bitrate=   0.0kbits/s    
video:0kB audio:0kB global headers:0kB muxing overhead inf%
------------------------------------------------------------------

Can anyone help with this?  I know there must be some Ubuntu/ffmpeg guru out there who knows what's going on.  Thanks.

---

