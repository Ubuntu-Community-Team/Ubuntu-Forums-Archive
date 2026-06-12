---
title: "convert mpeg to xvid to a specific file size"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by cazz on 2007-01-27
I have a big mpeg file that I like to convert to a xvid and 700 mb.

I have find how I can convert mpeg to xvid but not to a specific size.

---

### Post by HotFoot on 2007-02-12
You should be able to use the package "transcode" to do what you're looking for.  Install it through the synaptec package manager and then run:

transcode -y xvid -w [bitrate] -i [filein.mpeg] -o [fileout.avi]

Transcode is a very powerful and flexible tool.  Another feature I use is image cropping, but what the program can do is almost endless.  A manual for transcode can be found by typing:

man transcode

or you can visit the transcode wiki at [http://www.transcoding.org/cgi-bin/transcode?Transcode](http://www.transcoding.org/cgi-bin/transcode?Transcode) .

---

