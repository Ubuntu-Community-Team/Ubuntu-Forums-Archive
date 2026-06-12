---
title: "resize mp4 file"
date: 2010-07-12
forum: Multimedia Software
---

### Post by stevetxt on 2010-07-12
My camera takes video in mp4 format.  What is the easiest way to reduce the size of one of these files to be able to send it by email or post it on a web page?  I have been searching threads for this and am all confused now.  The one minute clip in question is about 50 MB, 640 x 480, 60 frames per second.  It would be nice to get it to between one and ten MB.  Or is there currently no easy way for routinely doing this?

---

### Post by stevetxt on 2010-07-13
Anyone have luck with a way to reduce video clip size routinely?

---

### Post by ron999 on 2010-07-13
Hi
Try using **WinFF**.
It's a GUI for ffmpeg.
It might be in the Ubuntu repository, otherwise visit the website for PPA instructions.
Here:-[http://winff.org/html_new/]("http://winff.org/html_new/")

One of the WinFF pre-sets is **MPEG-4 MP4 Fullscreen**.
This pre-set uses x264 video codec with bitrate 1000Kbps and aac audio codec with bitrate 112Kbps.
The picture size is 640x480 and the framerate is 29.97fps.

Use this pre-set and evaluate your results.
Then, if you wish, you can use the 'Options' button to tweak the settings and try again.
For example, reduce the picture size or bitrate.

When using WinFF it's a good idea to use a different folder for the output file. Otherwise you might over-write the original file.

---

### Post by stevetxt on 2010-07-13
Thanks very much.  I have installed WinFF from the repositaries  I think I have to search around for some restricted extras that I amnot finding there.

---

