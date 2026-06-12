---
title: "ffmpeg on Mythbuntu missing some codecs?"
date: 2009-02-06
forum: Mythbuntu
---

### Post by ubnewbie2 on 2009-02-06
I am trying to run ffmpeg as a user job to convert some recordings to a small pda size. The command line that works on my desktop Ubuntu 8.10 does not work on mythbuntu.

Firstly it complained that libxvid was unknown, so I changed that to xvid. Next it complained libmp3lame was unknown.

Is ffmpeg used by Mythtv itself?  Can I cause problems in Mythtv if I change ffmpeg.   I have found instructions that range from removing and reinstalling ffmpeg, to rebuilding it from source to include these codecs, but I don't want to upset Mythtv.

Other solutions also welcome :)

---

### Post by ian dobson on 2009-02-07
Hi,

From what I understand mythtv doesn't actually use the OS installed versions of any libs. They (the dev's) install a private version of the libs that thye need for media decoding. This makes sense for the dev's as they don't have to worry about which versions are installed by the OS.

So you should be able up install what ever version of ffmpeg that you want.

It looks as if the ubuntu version of ffmpeg isn't compiled with all codecs:-

```

root@alpha2:~# ffmpeg -v
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
ffmpeg: missing argument for option '-v'
 
```

Try ffmpeg -format | more to see what codecs are supported.

Couldn't you use mythtranscode to transcode videos?

Regards
Ian Dobson

---

### Post by ubnewbie2 on 2009-02-07
> **ian dobson said:**
> Hi,

From what I understand mythtv doesn't actually use the OS installed versions of any libs. They (the dev's) install a private version of the libs that thye need for media decoding. This makes sense for the dev's as they don't have to worry about which versions are installed by the OS.

So you should be able up install what ever version of ffmpeg that you want.

That's good.
> **ian dobson said:**
> 
It looks as if the ubuntu version of ffmpeg isn't compiled with all codecs:-


Yes, it seems so.  I wonder why.

> **ian dobson said:**
> 
Couldn't you use mythtranscode to transcode videos?

Regards
Ian Dobson

Well, the device I am preparing the video for (an iriver E100) is quite particular about the specification.  Basically mpeg4 sp, using divx/xvid for video and mp3 for audio, and 320x240 resolution (or 320x180 for 16:9 I suppose)

The ffmpeg command line I have found to work is

```
ffmpeg -i "$SRC_FILE" -r 29.97 -vcodec xvid -vtag XVID -s 320x180 -aspect 4:3 -maxrate 1800k  -b 512kb -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000  -ab 128k -ac 2 "$DEST_FILE"

```


and I have that in a user script for launching as a user job from mythweb when I want a particular show for my player.  

I don't know if mythtranscode can produce a file to those specs. The command line parameters seem sparse, and I don't see how to specify codecs to be used, for example.

---

### Post by ian dobson on 2009-02-07
Hi,

If you really need to recompile ffmpeg yourself have a look here:-
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

after downloading the source the important bit is :-
./configure --enable-liba52 --disable-debug --enable-libfaad --enable-libfaac --enable-gpl --enable-amr_nb --enable-amr_wb  --enable-libx264 **--enable-libxvid **--enable-pthreads --enable-libvorbis --enable-pp --enable-libtheora --enable-libgsm --enable-swscaler --disable-debug --enable-shared --prefix=/usr

Or maybe just enable the Medibuntu repository to enable some "non-free" software.
 
Regards
Ian Dobson

---

### Post by ubnewbie2 on 2009-02-07
> **ian dobson said:**
> Hi,

If you really need to recompile ffmpeg yourself have a look here:-
[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

after downloading the source the important bit is :-
./configure --enable-liba52 --disable-debug --enable-libfaad --enable-libfaac --enable-gpl --enable-amr_nb --enable-amr_wb  --enable-libx264 **--enable-libxvid **--enable-pthreads --enable-libvorbis --enable-pp --enable-libtheora --enable-libgsm --enable-swscaler --disable-debug --enable-shared --prefix=/usr

Or maybe just enable the Medibuntu repository to enable some "non-free" software.
 
Regards
Ian Dobson

OK, thanks.  Should there also be a --enable-libmp3lame as well ?

---

### Post by ian dobson on 2009-02-07
Hi,

I would imagine yes, I try and only use the "standard" tools supplied by Ubuntu.

Regards
Ian Dobson

---

### Post by ubnewbie2 on 2009-02-07
Good tip.  I found that my iriver player would accept videos created with mythbuntu's ffmpeg  xvid and mp3 codecs instead of libxvid and libmp3lame.  I am happily using those optins in my script now.

Thanks.

---

