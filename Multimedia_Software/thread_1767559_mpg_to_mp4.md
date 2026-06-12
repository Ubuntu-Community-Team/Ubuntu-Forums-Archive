---
title: "mpg to mp4"
date: 2011-05-25
forum: Multimedia Software
---

### Post by dozycat on 2011-05-25
I am trying to convert some video I am recording  from my kworld card from mpg to h.264 with sound mp3  ac3 (mp4)
So ican save the video to an usb and to see it in an plasma tv. 
I used trasmageddeon and i got video on the tv but no audio.
I tried:

```
 
$ ffmpeg -map 0:0 -map 0:1 -i video.mpg -threads 2 -b 604k -vcodec h264 -ac 1 -ab 256k -ar 44100 -acodec mpeg4aac -coder 1 -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me hex -subq 5 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -vol 500 movie.mp4 
```but it gives me:
 ffmpeg -map 0:0 -map 0:1 -i video.mpg -threads 2 -b 604k -vcodec h264 -ac 1 -ab 256k -ar 44100 -acodec mpeg4aac -coder 1 -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me hex -subq 5 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -vol 500 movie.mp4
ffmpeg version git-N-30215-g48df6a2, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 25 2011 05:44:41 with gcc 4.5.2
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libvpx
  libavutil    51.  2. 1 / 51.  2. 1
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2. 10. 0 /  2. 10. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, avi, from 'video.mpg':
  Metadata:
    encoder         : MEncoder 1.0rc4-4.5.2
  Duration: 00:01:00.04, start: 0.000000, bitrate: 1686 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 1:1 DAR 3:2], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 32000 Hz, stereo, s16, 128 kb/s
Unrecognized option 'me'


any ideas

---

### Post by andrew.46 on 2011-05-26
Can your original file simply be played on your tv as is? It looks like a pretty standard mpeg4 video + mp3 sound and would certainly play directly from usb on my wife's fancy television :).

If you are keen to encode, and I see you have a nice new version of FFmpeg, h264 is a good choice but you would be best to use some presets. Are you keen to use mpeg4aac for the sound or will mp3 suffice? For simple mp3 I would suggest the following pared down commandline:

```

ffmpeg -i video.mpg \
       -vcodec libx264 -preset slow -crf 22 -threads 0 \
       -acodec copy \
        movie.mp4

```

but if your were set on mpeg4aac with a little added volume perhaps the following:

```

ffmpeg -i video.mpg \
       -vcodec libx264 -preset slow -crf 22 -threads 0 \
       -acodec mpeg4aac -ab 256k -ar 44100 -vol 500 \
       movie.mp4

```

But I would be surprised if your nice tv did not recognise bog standard mp3 sound. Anyway perhaps try the commandline I have suggested and see if this gives you a decent file?

***Edit: **mpeg4aac encoder was removed about 4 years ago, apologies for the incorrect post :(.*

---

### Post by dozycat on 2011-05-26
the first one works but no sound in the tv.

the second says:

Unknown encoder 'mpeg4aac'

I followed this tutorial:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

for installing the ffmeg

and the package libavcodec-extra-52 but no  mpeg4acc

---

### Post by andrew.46 on 2011-05-27
> **dozycat said:**
> 
the second says:

Unknown encoder 'mpeg4aac'

I followed this tutorial:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

for installing the ffmeg

and the package libavcodec-extra-52 but no  mpeg4acc

That is because FFmpeg does not have an mpeg4aac encoder (it was removed many years ago) and I should not post crap while doing nightshift :(. My apologies for not picking that one up. So you are certain that your tv will work with aac sound? If so you could simply use libfaac, which is enabled in Fakeoutdoorsman's guide:

```

ffmpeg -i video.mpg \
       -vcodec libx264 -preset slow -crf 22 -threads 0 \
       -acodec libfaac -ab 256k -ar 44100 -vol 500 \
       movie.mp4

```

You can see the aac encoders available to you by running:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -codecs | grep -i aac[/COLOR]**
ffmpeg version git-N-30260-g39e4206, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 26 2011 17:54:05 with gcc 4.5.2
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-amrwbenc --enable-libvo-aacenc --enable-libfreetype --enable-nonfree --enable-gpl --enable-version3
  libavutil    51.  2. 2 / 51.  2. 2
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2. 11. 0 /  2. 11. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
**[COLOR="Red"] DEA    aac             Advanced Audio Coding[/COLOR]**
 D A    aac_latm        AAC LATM (Advanced Audio Codec LATM syntax)
[B][COLOR="Red"]  EA    libfaac         libfaac AAC (Advanced Audio Codec)
  EA    libvo_aacenc    Android VisualOn AAC[/COLOR][/B]

```

You are after the ones marked 'E' which of course denotes Encoder, you should have libfaac in there. BTW you do not need libavcodec-extra-52 if you have installed by following Fakeoutdoorsman's guide.

It all comes down to what codecs and containers that your tv will support, do you have some documentation on this? If you know that definitely there should be absolutely no trouble converting your video with the git FFmpeg...

---

### Post by dozycat on 2011-05-27
That worked, Thanks.

So if someone needs so record from an kworld to viera panasonic tc-p50x3 or tc-p42x3. Do this:

```

mencoder tv:// -tv driver=v4l2:norm=NTSC:fps=25:outfmt=yuy2:quality=0:input=0:width=720:height=578:chanlist=us-bcast:volume=80:amode=1:normid=0:audiorate=32000:alsa:adevice=hw.1:channel=3 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1500:keyint=25 -oac mp3lame -lameopts cbr:br=128:mode=0 -endpos 02:00:00 -vf pp=hb/vb/dr/al/lb,denoise3d -o video.mpg


```

It will drop frames but it looks ok to me at least. To bad FFmeg is not acepting alsa yet.

Then:
```

ffmpeg -i video.mpg        -vcodec libx264 -preset slow -crf 22 -threads 0        -acodec libfaac  -ab 256k -ar 44100 -vol 500        movie.mp4




```

Now  take to the tv in an usb.
Now next project  mediatomb to viera.

---

