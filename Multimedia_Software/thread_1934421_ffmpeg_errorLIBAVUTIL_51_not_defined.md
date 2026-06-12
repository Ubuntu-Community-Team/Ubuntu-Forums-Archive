---
title: "ffmpeg error:LIBAVUTIL_51 not defined"
date: 2012-03-02
forum: Multimedia Software
---

### Post by Luca Borrione on 2012-03-02
Hello,

I recently installed the last ffmpeg and x264 following this [howto]("http://ubuntuforums.org/showthread.php?t=786095")
with the only difference that I used this configuration

```
./configure --enable-gpl  --enable-libgsm --enable-libxvid \
--enable-libmp3lame --enable-libvorbis --enable-libfaac \
--enable-shared --enable-libopencore-amrnb --enable-libvpx \
--enable-libopencore-amrwb --enable-libtheora --enable-libx264 \
--enable-nonfree --enable-version3 --enable-x11grab
```

I'm trying to convert a h264 video file using this code
```
ffmpeg -i "input.mp4" -ar 44100 -ac 2 -ab 192k -acodec libmp3lame -s 1280x544 -vcodec libxvid -r 23.98 -b 2500k "output.avi"
```

I get this error
```
ffmpeg: relocation error: /usr/local/lib/libswresample.so.0: symbol av_opt_set_int, version LIBAVUTIL_51 not defined in file libavutil.so.51 with link time reference
```

For reference I have:
```

$ ldd /usr/local/bin/ffmpeg | grep libavutil
	libavutil.so.51 => /usr/lib/i686/cmov/libavutil.so.51 (0x00269000)

$ dpkg --get-selections | grep libavutil
libavutil-dev					install
libavutil-extra-51				install
libavutil51					deinstall

$ uname -a
Linux my-pc 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

```

Looking at the release file note of ffmpeg I've installed the 0.9.1.git and I'm using lubuntu oneiric 32bit

What should I do to solve this issue?
Many thanks in advance

---

### Post by Luca Borrione on 2012-03-02
The problem is that I don't have libswresample at all :(
```
$ cd /usr/local/bin
$ ls -lrt | grep libswresample
$

```

and I don't have it in the repository too :(
```
$ dpkg -l | grep libswres
$

```

Any suggestions?

---

### Post by ron999 on 2012-03-02
> **Luca Borrione said:**
> 
Any suggestions?
Work through the howto again, then if you still have problems post a question in the howto thread.

---

### Post by Luca Borrione on 2012-03-02
Thank you for the suggestion .. I don't know why I didn't think of posting there directly .. :D

The problem was the --enable-shared conf option see
[http://ubuntuforums.org/showthread.php?t=786095&page=213#2123]("http://ubuntuforums.org/showthread.php?t=786095&page=213#2123")

Cheers

---

