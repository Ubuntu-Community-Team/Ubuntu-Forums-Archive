---
title: "Video a la sorenson"
date: 2007-07-11
forum: Multimedia Production
---

### Post by sefs on 2007-07-11
Has anyone here ever used sorenson squeeze.  I would like to find an equivalent application in linux.  Does any such thing exist as yet?

Product url is here: [http://www.sorensonmedia.com/pages/?pageID=2](http://www.sorensonmedia.com/pages/?pageID=2)

Thanks.

---

### Post by Sebastian Brosig on 2007-08-14
mencoder does the hard work of video encoding in the free software universe. It's not that easy to use.
 Kmenc15  is a (KDE) gui frontend for mencoder, can't say i've tried it.

---

### Post by Prefader on 2007-08-16
Squeeze allows encoding with the VP6 codec, for which I'm not aware of a linux version.

If I need to encode flash video in Linux, I use ffmpeg (flash 7).  It's fairly simple to scratch out a script that will do batch encodes and filename formatting.  Far from the same thing as squeeze, as it's lacking the nice GUI for cropping and color correction, but you *can* do it all from the command line.

If anyone knows of a better solution, I'd love to know about it.

oops!  I lied!  Looks like On2 has released a VP6 encoder for linux . . .

[http://www.on2.com/products/flix/engine/](http://www.on2.com/products/flix/engine/)

So there is an encoder for flash8 available for linux now, but I have no idea what the price is.

---

