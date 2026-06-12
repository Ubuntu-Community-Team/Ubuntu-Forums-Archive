---
title: "dvd-slideshow ffmpeg problem"
date: 2007-10-24
forum: Multimedia Production
---

### Post by barna on 2007-10-24
Hi,
In Gutsy, I tried to make a simple DVD slideshow from a few pictures, but failed. The error message is like this:

```

[dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] /home/barna/Documents/Pannonia/11/Gyimes/zene/Track 07.mp3
[dvd-slideshow] fade_in_time=0:0:3.000 fade_out_time=0:0:3.000
[dvd-slideshow] total_audio_length=0:5:32.068
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio for /home/barna/Documents/Pannonia/11/Gyimes/                                                              zene/Track 07.mp3...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/barna/Documents/Pannonia/11/DVD/media/dvd-slideshow.lo                                                              g for details
[dvd-slideshow] cleanup...
<font color=#ff0000>Slideshow error.

```

Does anybody have an idea why? I found a possible explanation in this thread at a gentoo forum: [http://forums.gentoo.org/viewtopic-p-3240040-highlight-.html?sid=732af110590ee32c3e6e3e95c65019c4]("http://forums.gentoo.org/viewtopic-p-3240040-highlight-.html?sid=732af110590ee32c3e6e3e95c65019c4")
Towards the end of this thread somebody suggests:

> 
Please do downgrade Your ffmpeg to older version " emerge -va =media-video/ffmpeg-0.4.9_p20070129 "
Newer version of ffmpeg has changed commandline options ( bitrate needs letter k in ending). And dvd-slidesshow is not yet updated with patch in portage..
By downgrading everything works like charm


Can this be the problem? If yes, can one somehow downgrade ffmpeg in Gutsy?

Thanks
Daniel

---

### Post by barna on 2007-10-28
Yes, this seems to be indeed the problem. I have downloaded and installed the latest dvd-slideshow from sourceforge (0.8.0), but this still did not have the necessary changes. After changing the line

```

ffmpeg -i "$tmpdir/audio1.wav" -y -vn -ab $audio_bitrate -acodec ac3 -ar $audio_sample_rate -ac 6 "$tmpdir/audio1.ac3" >> "$outdir/$logfile" 2>&1

```

in /usr/bin/dvd-slideshow to

```

ffmpeg -i "$tmpdir/audio1.wav" -y -vn -ab ${audio_bitrate}k -acodec ac3 -ar $audio_sample_rate -ac 6 "$tmpdir/audio1.ac3" >> "$outdir/$logfile" 2>&1

```

everything seems to work now. (I expected that the video bitrate options of ffmpeg also need to be modified, but seemingly not....)

... and everywhere else, where you find ffmpeg with the -ab option, add a 'k' to the end of the value, as in the example above

---

### Post by william_nbg on 2007-10-31
**Huh**! It still wouldn't work on mine - getting the same error - and I only have to make one stupid slide-show for my girlfriend.

found another fix in a different forum:

In dvd-slideshow: Change on line 3989 and 4004 - like this

*audio_bitrate=224*

to

*audio_bitrate=224k*



And it seems to work fine on my box - at least one test run has.

---

### Post by miceagol on 2008-01-30
I did all this (including updating dvd-slideshow to 0.8.0-pre10), but get the error
```

ffmpeg: unrecognized option '-ab'

``` 
That's weird, because it's a common option. Asking for the ffmpeg version gives me this:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)

```
Any ideas?

---

### Post by miceagol on 2008-01-30
Solved it by upgrading ffmpeg to latest SVN:
```

sudo apt-get install subversion
cd <folder/where/you/want/to/download>
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure
make
make install

```

---

### Post by rafalmag on 2008-05-15
I had the same problem.
Thanks to  barna and miceagol.

I post solution:

In /usr/bin/dvd-slideshow you should change: every ```
$audio_bitrate
``` to ```
${audio_bitrate}k
```
and next:
```
sudo apt-get install subversion
cd <folder/where/you/want/to/download>
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure
make
make install
```

Now it works like a charm.

---

