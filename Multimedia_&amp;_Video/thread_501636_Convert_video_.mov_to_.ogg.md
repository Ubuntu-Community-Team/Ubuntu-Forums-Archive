---
title: "Convert video: .mov to .ogg?"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by topquark170 on 2007-07-15
I acquired (as a gift) a digital camera which takes videos.  Unfortunately, the only video output option for the camera is .mov, so I would like to be able to convert these to .ogg.  Does anyone know a program / script which will do this?  Ideally, it would handle all the files in a directory at once... but I could add another script to do that myself.  

I have already tried mencoder, and found that 

```

$mencoder -ovc help

```

returns 

```

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
   xvid     - XviD encoding
   x264     - H.264 encoding

```

To add ogg to my mencoder output options would be an equivalent solution to this problem.

Thank you.

---

### Post by Major_Kong on 2007-07-16
Try uising avidemux it's much more user-friendly than the mencoder command line.

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

---

