---
title: "Kino and ffmpeg compile: x264 error"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by doundounba on 2007-02-04
Hi all,

So I'd like to get Kino with Quicktime support in Edgy (as we had in Dapper)...  This apparently means I must compile Kino from source.  OK, no problem!  Trying that (with Kino 0.9.5), the configure chokes on:

```

checking libavcodec version (build >4644)... configure: error: FFMPEG is the new, preferred DV codec. If you must only
support libdv, then you must explicitly specify it using --with-libdv-only.

```


First, I try "./configure --with-libdv-only" but this unfortunately still yields the same error.  OK.  :(  Looking here [http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=2552&mesg_id=2552&page=]("http://www.kinodv.org/dcforum/dcforum?az=show_topic&forum=101&topic_id=2552&mesg_id=2552&page=") this apparently means I need a newer ffmpeg.  Right.  Read up on this a little bit, then, after installing a bunch of new packages...

```

svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
mv ffmpeg ffmpeg-0.0.20070204
cd /ffmpeg-0.0.20070204
./configure --enable-mp3lame --enable-shared --enable-gpl --enable-faac --enable-faad --enable-a52 --enable-dts --enable-pthreads --enable-libogg --enable-libtheora --enable-vorbis --enable-libgsm --enable-pp --enable-x264 --enable-xvid --disable-debug
make

```

This goes for a while, until it dies with:

```

x264.c: In function ‘X264_init’:
x264.c:152: error: ‘struct <anonymous>’ has no member named ‘f_rf_constant’
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/pascal/software/ffmpeg-0.0.20070204/libavcodec'
make: *** [lib] Error 2
me@myhost:~/software/ffmpeg-0.0.20070204$

```


Ahhhh, OK.  This is where I hit the wall.  Do I need to roll my own x264 too?! Or is it possible to avoid doing that? I guess I could disable x264 support, but I'd prefer to have it...

:confused:  Any clues?

---

### Post by doundounba on 2007-02-04
Well, sorry to follow up on myself...  I had another little burst of energy to read up on things, and it does look like my two options are to compile ffmpeg without x264 support or to (re-)compile the latest x264 from source, as what's in the repos appears too old to support the current ffmpeg. Dependency chains are annoying.  <sigh>

Reference is here: [http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-December/006020.html]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-December/006020.html")

And indeed, ffmpeg does compile if I just remove x264 from the config options and use instead:
```

./configure --enable-mp3lame --enable-shared --enable-gpl --enable-faac --enable-faad --enable-a52 --enable-dts --enable-pthreads --enable-libogg --enable-libtheora --enable-vorbis --enable-libgsm --enable-pp --enable-xvid --disable-debug

```

Now I need to read up on rolling my own debs in such a way that things don't break in my next upgrade...  :-|

---

