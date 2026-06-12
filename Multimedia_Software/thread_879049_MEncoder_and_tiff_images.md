---
title: "MEncoder and tiff images"
date: 2008-08-03
forum: Multimedia Software
---

### Post by TheBouleOfFools on 2008-08-03
I'm trying to use MEncoder to turn a bunch of tiff images into a short video.

The command I use is

```
mencoder mf://*.tif -mf fps=30:type=tif -ovc lavc -lavcopts vcodec=wmv2:mbd=2:trell -oac copy -o vmot.avi
```

Now, this does work on my Gentoo Linux box. However, on Debian and Ubuntu, I get

```
[demux_mf] unkown input file type.
============Sorry, this file format is not recognized/supported============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
```

I assume that this means MEncoder was built without tiff support. It does work for jpeg images, however I do not want to have to convert my images (quite a few) every time when it is not necessary. I downloaded the mplayer sources and looked through ./configure --help, but I did not see anything pertaining to tiffs.

I do have libtiff4 installed. Does anyone have any insight?

Edit: Sorry I failed to notice the Multimedia Production forum. Can this be moved, if possible?

---

### Post by TheBouleOfFools on 2008-08-04
Well ok I got it working. It seems the latest stable version chokes on tiffs, and so you have to use one from svn.

---

