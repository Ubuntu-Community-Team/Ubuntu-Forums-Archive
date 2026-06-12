---
title: "Help converting mp4 to xvid with avconv"
date: 2013-03-01
forum: Multimedia Software
---

### Post by rgladwell on 2013-03-01
I normally use avidemux to convert mp4s to Xvid AVI for my Philips Streamium SLM5500 which only seems to support Xvid. Normally I select MPEG-4 ASP (Xvid) at Two Pass with an average bitrate f 1500kb/s for video and AC3 (lav) audio and it converts correctly.

However, I'm trying to using avconv so I can automate the process with a script, but when I do this the video stutters and stops playing part way through. I have a suspicion its something to do with a faulty audio conversion.

The commands I'm using are as follows:
```

avconv -y -i video.mp4 -pass 1 -vtag xvid -c:a ac3 -b:a 128k -b:v 1500k -f avi /dev/null
avconv -y -i video.mp4 -pass 2 -vtag xvid -c:a ac3 -b:a 128k -b:v 1500k -f avi video.avi
```

There is a bewildering array of arguments for avconv. Is there something I'm doing wrong? Is there a way I can script avidemux from a headless server?

Please see command line output:

```
$ avconv -y -i video.mp4 -pass 1 -vtag xvid -an -b:v 1500k -f avi /dev/null
avconv version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'video.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
    creation_time   : 2013-02-04 13:53:38
  Duration: 00:44:09.16, start: 0.000000, bitrate: 669 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 720x404 [PAR 1:1 DAR 180:101], 538 kb/s, 25 fps, 25 tbr, 100 tbn, 50 tbc
    Metadata:
      creation_time   : 2013-02-04 13:53:38
    Stream #0.1(und): Audio: ac3, 44100 Hz, stereo, s16, 127 kb/s
    Metadata:
      creation_time   : 2013-02-04 13:53:42
[buffer @ 0x7f4c40] w:720 h:404 pixfmt:yuv420p
Output #0, avi, to '/dev/null':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
    creation_time   : 2013-02-04 13:53:38
    ISFT            : Lavf53.21.1
    Stream #0.0(und): Video: mpeg4, yuv420p, 720x404 [PAR 1:1 DAR 180:101], q=2-31, pass 1, 1500 kb/s, 25 tbn, 25 tbc
    Metadata:
      creation_time   : 2013-02-04 13:53:38
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> mpeg4)
Press ctrl-c to stop encoding
frame=66227 fps=328 q=2.0 Lsize=       0kB time=2649.16 bitrate=   0.0kbits/s    
video:401602kB audio:0kB global headers:0kB muxing overhead -100.000000%
$ avconv -y -i video.mp4 -pass 2 -vtag xvid -c:a ac3 -b:a 128k -b:v 1500k -f avi video.avi
avconv version 0.8.5-6:0.8.5-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Jan 24 2013 14:49:20 with gcc 4.7.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'video.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
    creation_time   : 2013-02-04 13:53:38
  Duration: 00:44:09.16, start: 0.000000, bitrate: 669 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 720x404 [PAR 1:1 DAR 180:101], 538 kb/s, 25 fps, 25 tbr, 100 tbn, 50 tbc
    Metadata:
      creation_time   : 2013-02-04 13:53:38
    Stream #0.1(und): Audio: ac3, 44100 Hz, stereo, s16, 127 kb/s
    Metadata:
      creation_time   : 2013-02-04 13:53:42
[buffer @ 0x12b4f00] w:720 h:404 pixfmt:yuv420p
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
[mpeg4 @ 0x12b3ec0] [lavc rc] Using all of requested bitrate is not necessary for this video with these parameters.
Output #0, avi, to 'video.avi':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
    creation_time   : 2013-02-04 13:53:38
    ISFT            : Lavf53.21.1
    Stream #0.0(und): Video: mpeg4, yuv420p, 720x404 [PAR 1:1 DAR 180:101], q=2-31, pass 2, 1500 kb/s, 25 tbn, 25 tbc
    Metadata:
      creation_time   : 2013-02-04 13:53:38
    Stream #0.1(und): Audio: ac3, 44100 Hz, stereo, flt, 128 kb/s
    Metadata:
      creation_time   : 2013-02-04 13:53:42
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> mpeg4)
  Stream #0:1 -> #0:1 (ac3 -> ac3)
Press ctrl-c to stop encoding
Input stream #0:1 frame changed from rate:44100 fmt:s16 ch:2 to rate:44100 fmt:flt ch:2
frame=66227 fps=284 q=2.2 Lsize=  458486kB time=2649.13 bitrate=1417.8kbits/s    
video:413716kB audio:41393kB global headers:0kB muxing overhead 0.741969%

```

---

### Post by FakeOutdoorsman on 2013-03-01
Does it stutter with just the Philips device or any player? avconv is notoriously buggy.  I recommend trying a recent, [static build of ffmpeg](https://ffmpeg.org/download.html#LinuxBuilds) to rule out any avconv/fake "ffmpeg" bug(s). No need to install or anything. Just download the archive, extract, and then execute the binary:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.2013-03-01.tar.gz
tar xzvf ffmpeg.static.32bit.2013-03-01.tar.gz
./ffmpeg -i input [output options] output
```

You can run the static build of the real ffmpeg by navigating to the containing directory and then (note the preceding **./**):
```
./ffmpeg -i input [output options] output
```
or you can provide the full path:
```
/home/linuxuser/ffmpeg -i input [output options] output
```

Doublecheck that you're using real ffmpeg:
```
$ ./ffmpeg
ffmpeg version N-50525-gc257fe1 Copyright (c) 2000-2013 the **FFmpeg** developers
```

and not bizarro ffmpeg:
```
$ ffmpeg
ffmpeg version 0.8.5-4:0.8.5-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the **Libav** developers
  built on Jan 24 2013 18:01:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
```

If you want a more permanent solution, or don't want to have to use the full path each time you want to invoke ffmpeg then you can place the ffmpeg binary in a directory and add the directory to your $PATH as shown in [How to add a directory to my path?](http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-path)

Also see:
[list]
[*][Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017)
[*][The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)
[/list]

---

### Post by andrew.46 on 2013-03-01
I have a similar problem with my wife's TV, in that it only plays 'xvid' in an avi container. Mind you it would not play back ac3 audio. If you follow FakeOutdoorsman's recommendation (and this would be a good idea) perhaps as well as FakeOutdoorsman's example you also could try this *single pass* example which has worked well for me for some time:

```

ffmpeg -y -i "input.mp4" -threads auto \
-c:v mpeg4 -q:v 5 -vtag XVID -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
-c:a libmp3lame -ac 2 -q:a 3 -ar 44100 \
"output.avi"

```

Perhaps alter the audio line to ac3, although mp3 is pretty universal, and experiment a little with the *-q:v 5* setting. The avi container and even xvid is all a little sad in this modern age but some of these devices are still anchored in the past :(.

---

### Post by FakeOutdoorsman on 2013-03-01
> With our powers combined...

Yes, using recent ffmpeg with Andrew's example or similar command would be the way to go.

---

### Post by rgladwell on 2013-03-02
Hey, thanks for the tips guys. I did try with the binary ffmpeg downloaded directly from the ffmpeg web site and Andrew's suggestions, but I still get the same result: the video plays fine on my Ubuntu laptop but when I stream it through my Philip Streamium it plays silently for about a minute than stutters and stops altogether.

What exactly does the '-q:v' parameter do and how should i play around with it?

---

### Post by FakeOutdoorsman on 2013-03-02
> **rgladwell said:**
> ...I still get the same result: the video plays fine on my Ubuntu laptop but when I stream it through my Philip Streamium it plays silently for about a minute than stutters and stops altogether.

Curses. Getiing things right for picky devices isn't always an easy task, and of course the [specifications](http://download.p4c.philips.com/files/s/slm5500_05/slm5500_05_dfu_eng.pdf) never really give exact details:

> Video playback
DivX 3.11, DivX 4, DivX 5, MPEG1, MPEG2, MPEG4, XviD, WMV, WMV-DRM, HD-MPEG2 (on wired network)

Audio playback
MP3, PCM, WAV, WMA-DRM, WMA, AAC-MPEG4

If you have a video that does play normally then the output of ffprobe could be useful:
```
ffprobe -i input_file.avi
```

> **rgladwell said:**
> What exactly does the '-q:v' parameter do and how should i play around with it?
"-qscale:v" (or the alias "-q:v") is a method to control the output quality for this particular encoder. 2-5 is a good range, and a lower value is a higher quality. If you don't really care about the file size then just go with 2.

---

### Post by rgladwell on 2013-03-03
Thanks for your advice with this, really helpful. :-)

Here is an ffprobe of something that does play correctly:

> Input #0, avi, from 'video.avi':
  Duration: 00:20:02.04, start: 0.000000, bitrate: 1638 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 720x404 [SAR 1:1 DAR 180:101], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 128 kb/s

and here is the ffprobe output from something I've tried to encode as above:


> Input #0, avi, from 'video.avi':
  Metadata:
    encoder         : Lavf54.63.102
  Duration: 00:21:34.45, start: 0.000000, bitrate: 408 kb/s
    Stream #0.0: Video: mpeg4 (Simple Profile), yuv420p, 720x404 [PAR 1:1 DAR 180:101], 23.98 fps, 23.98 tbr, 23.98 tbn, 24k tbc
    Stream #0.1: Audio: ac3, 44100 Hz, stereo, s16, 128 kb/s

I notice the output stream has a couple of differences, noticeably the 's16' string.

---

### Post by andrew.46 on 2013-03-28
It would be unusual but perhaps use* libxvid *for the video stream:
```

-c:v libxvid
```

See if your copy has been against xvid with some variation of the following:

```

andrew@skamandros~$ [COLOR="#FF0000"]ffmpeg -codecs 2>/dev/null | grep xvid[/COLOR]
 DEV.L. mpeg4                MPEG-4 part 2 (decoders: mpeg4 mpeg4_vdpau ) (encoders: mpeg4 libxvid )

```

---

