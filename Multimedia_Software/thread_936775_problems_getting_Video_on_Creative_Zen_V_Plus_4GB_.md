---
title: "problems getting Video on Creative Zen V Plus 4GB with ffmpeg"
date: 2008-10-03
forum: Multimedia Software
---

### Post by zer000 on 2008-10-03
Hi everybody,

I recently got myself a Creative Zen V Plus 4GB, and it's working great for music, with [COLOR="Navy"]gnomad2[/COLOR] and/or [COLOR="Navy"]mtp-tools[/COLOR] for transferring mp3s and files to the device.

But I thought it might be fun to be able to load youtube videos onto it as well, except I can't quite get it to work. After a lot of web- and forum-searching I came across these steps that seem to work for everyone but me:

1) download the youtube video with [COLOR="#000080"]youtube-dl[/COLOR]
2) convert it to avi raw video with [COLOR="#000080"]ffmpeg[/COLOR] (since the Zen V Plus doesnt support *any* video compression codecs, silly yeah, but that's apparently how it is) using the following commandline:
```
ffmpeg -i mdKPLDYKdWU.flv -vcodec rawvideo -r 15 -pix_fmt rgb24 -acodec adpcm_ima_wav -s 128x128 charly-the-unicorn.avi
```
3) transfer it to the Zen V Plus device
```
mtp-sendfile charly-the-unicorn.avi charly-the-unicorn.avi
```

this *almost* works, in the sense that the video appears on the device, i can play it, the sound works perfectly, and the video ... appears. but it's wrong, the screen flickers, and the frames are squeezed flat and repeated a couple of times across the screen, interleaved with some noise.
which suggests to me that there is something wrong with the encoded with of the frames and the headers in between them?

or possibly the pix_fmt option is wrong?

because there's also something weird going on with that, when i try to request a list of all the possible pix_fmt options, it gives me an error (which it shouldnt, according to ffmpeg's documentation) :

```
blah/tmp$ ffmpeg -pix_fmt list
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Must supply at least one output file
```

does anyone know what's up with this, or perhaps have any ideas or suggestions what more to try or where to look further? 
because I've trawled through the web and this forum, and I'm running out of ideas what to try next ... :)

---

