---
title: "File signatures for H.264 video files ?"
date: 2013-05-30
forum: Multimedia Software
---

### Post by ubufs on 2013-05-30
Hi,

Does anyone know which are file signatures must be used to recover video files using the H.264 / MPEG-4 AVC compression ?

( The question was already asked here, but the thread was closed before anyone could answer : [http://ubuntuforums.org/showthread.php?t=154520](http://ubuntuforums.org/showthread.php?t=154520) )

I believe that H.264 is only a video compression codec and that H.264 compressed content is enclosed inside other multimedia files like AVI, mp4, a.s.o.

Hence, the files signatures to look at would be those of the container video files.

I'm not sure however if different signatures are used when those files contain h.264 compressed flows.

The configuration file of Scalpel contains the following lines :
# AVI (Windows animation and DiVX/MPEG-4 movies)
      avi    y    50000000 RIFF????A

Where "RIFF????A" is the file signature of the file header.

I'm not certain if it still valid signature for an AVI file with H.264 content inside, as such files seem possible.

From what I read, I believe that MPEG-4 and MPEG-4 AVC are not the same, and that MPEG-4 AVC would be equivalent to H.264. 
But I'm really not sure about this.

Does someone here has better knowledge about this ?

---

