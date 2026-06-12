---
title: "X264 videos are slow"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by Biffy on 2007-04-07
I am using Dapper and I've got a videofile in mp4 format. Its about 1gb in size and got theese specs:

Codec: X264 with AAC audio
Resolution: 512x384

When playing this one in mplayer (the one in the Dapper reps or the latest SVN) the video and sound works, but it is using 99-100% of my CPU and thus making the video choppy and slow. Also, after a while, the audio gets out of sync. In Mplayer, i've tried:

* Using different video drivers. Xv is the least CPU hungry driver so it works best, but still not good enough
* Using the this command when starting mplayer: -lavdopts lowres=0:fast:skiploopfilter=all . This makes a big difference, and almost makes the video non-choppy, but when there are to much movement on the screen, the CPU reaches 100% again.
* Using the SVN version of mplayer. No difference whatsover.
* When the cpu usage is so heavy, mplayer is saying that "Your system is too slow to play this" , i've tried all those recomended options it tells me to try. Still nothing.

Xine and VLC won't play the video correct. I get a blurry picture. I tried compiling the latest VLC from a howto on this forum, but i then get this error:

```
demux.c:38:25: error: avformat.h: No such file or directory
In file included from demux.c:41:
ffmpeg.h:44: error: syntax error before 'AVCodecContext'
ffmpeg.h:50: error: syntax error before 'AVCodecContext'
ffmpeg.h:85: error: syntax error before 'AVFrame'
make[6]: *** [libffmpeg_plugin_la-demux.lo] Error 1
make[6]: Leaving directory `/home/larsson/Downloads/vlc-0.8.6a/modules/codec/ffmpeg'
make[5]: *** [all-modules] Error 1
make[5]: Leaving directory `/home/larsson/Downloads/vlc-0.8.6a/modules/codec/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/larsson/Downloads/vlc-0.8.6a/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/larsson/Downloads/vlc-0.8.6a/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/larsson/Downloads/vlc-0.8.6a/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/larsson/Downloads/vlc-0.8.6a'
make: *** [all] Error 2
```

I configured with this:

```
./configure --enable-libtool --enable-dvdread --enable-vcdx  --enable-faad --enable-real --enable-flac --enable-realrtsp --enable-snapshot --enable-live555 --enable-dv --enable-theora --enable-esd
```

Can it be that i need the latest ffmpeg to be able to view X264 video?

```
larsson@ubuntu:~ $ ffmpeg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
usage: ffmpeg [[infile options] -i infile]... {[outfile options] outfile}...
Hyper fast Audio and Video encoder

```

Why is X264 video so CPU demanding and how can i solve this? Can i somehow convert this video into a regular avi file that is not so CPU demanding somehow? I dont care how this is solved, the important thing is that i can watch these videos! 

Thanks in advance!

---

### Post by Biffy on 2007-04-08
And i tried Totem with Gstreamer. Still no luck.

---

### Post by regomodo on 2007-05-04
i've noticed the same thing. 

with x264 videos, everything is choppy and audio is delayed a fair bit. i've had a search for a better codec  but haven't got far

i'll post anything i find

---

### Post by Cappy on 2007-05-04
[http://ubuntuforums.org/showthread.php?t=429741](http://ubuntuforums.org/showthread.php?t=429741)

---

### Post by Biffy on 2007-10-26
I know this is an old thread but has anyone find any solution to this? Mplayer is the only player wich plays theese files correctly but im still stuck att 98-100% CPU usage wich, after a while, makes the sound out of sync.

Why cant VLC play it? It wont even open the mkv file. Xine and totem (With xine engine and Gstreamer engine) will open it but the video playback aint right.

---

### Post by hugmenot on 2007-10-27
Yes, at getdeb.net they have a package of mplayer 1.0RC2. It has x264 speed improvements in the changelog. Check there.

---

### Post by Biffy on 2007-10-28
Thanks for your reply. I think i solved this by doing:

1)Download the latest mplayer svn
2)Compile it. (No need to install it!)
3)Run mplayer from the svn folder

Now my CPU is down at 60-70% when watching theese x264 MKV videos. I've been told that this is because the ffmpeg version is heavily outdated in Dapper. When downloading the latest mplayer svn, you automatically get the latest ffmpeg in there too.

---

### Post by moon2js on 2007-10-30
I have the same problem with H.264 (MPEG-4 AVC) videos and only those videos in Totem, Miro, and VNC (haven't tried mplayer). I thought my antiquated computer was too old to run them (not enough processing power to keep up), but I'm encouraged to hear that the codec may have a fixable problem.

---

### Post by moon2js on 2007-11-18
Does anyone know if this issue is fixed in Gutsy? I have a Feisty box that can't keep up with a lot of video podcasts, but when I fire up the Gutsy box next to it, they work fine. The Feisty box has older hardware, but I'm wondering if upgrading to Gutsy might bring in a better codec.

---

