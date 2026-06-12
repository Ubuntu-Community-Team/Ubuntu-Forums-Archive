---
title: "Avi -&gt; Tiff"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by LarsP on 2007-11-14
How can I convert an .avi clip to a sequence of tiff(or other lossless format) images?

---

### Post by ron999 on 2007-11-14
Hi

Avidemux will save a series of JPEGs - which aren't lossless.
Use File > Save > Save Selection as JPEG images.

VLC will save a series of PNGs - which are lossless.
But I think that this can only be used from the command line using 'image'.
See this link:-[http://wiki.videolan.org/Video_Output]("http://wiki.videolan.org/Video_Output")

I've saved selections with Avidemux, and it works OK.
But I haven't tried to do it with VLC, so I can't comment.

---

### Post by disturbedite on 2007-11-14
png would be the preferable lossless format.  i believe this is possible (and vice versa) with ffmpeg.

---

### Post by LarsP on 2007-11-15
Thanks for the replies.
The VLC thing would have been perfect since you can specify to only take one of n frames by using --image-out-ratio=n. The problem was that vlc couldn't handle my 1920x1080 uncompressed avi. I ended up using "take screenshot" in totem. That was a pain, since i needed 100 images for testing JPEG 2000 codecs.

---

