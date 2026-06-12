---
title: "ffmpeg syntax help, please"
date: 2012-04-23
forum: Multimedia Software
---

### Post by Jose Catre-Vandis on 2012-04-23
I have a somagic easycap capture device (looks like Easycap/EzCap DC60 but different innards). I have a good command line for capturing video with it, and another for capturing audio from my line in, but would like to combine the two so that I get a/v sync.

**Video Capture** (it's a live feed piped into ffmpeg)
```
somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 | ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -i - -filter:v yadif -aspect 1.77 -b 4000k output1.avi
```

**Audio Capture**
```
ffmpeg -f alsa -ac 2 -i hw:0,0 -acodec pcm_s16le output1.wav
```

Is it possible to put the two together? I've tried a few things but not had any success.

---

### Post by FakeOutdoorsman on 2012-04-23
The *-an* option is probably being applied to all inputs. Use the *-map* option instead to select your input streams (I'm assuming you're using a compiled/non-ancient ffmpeg). The console output will tell you the input file id and the stream id. For example, the second input's first stream is 1:0. Untested example:
```
somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 | ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -i - -f alsa -ac 2 -i hw:0,0 -acodec pcm_s16le -filter:v yadif -aspect 1.77 -b 4000k -map 0:0 -map 1:0 output1.avi
```
Alternatively you could tell it to copy all streams but ignore the audio from the first input with:
```
-map 0 -map -0:a:1
```
The ffmpeg man page has a good section on *-map*.

---

### Post by Jose Catre-Vandis on 2012-04-23
Thanks FakeOutdoorsman, I'll give it a go and report back. In trying out some one-liners I took out the -an, for the same reason you allude to, but ffmpeg then had trouble finding hw:0,0 (error: no file or directory). Let's see how mapping things works out...

OK, trying out your example, a very short avi file is created and I get this in the terminal:
```
somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 | ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -i - -f alsa -ac 2 -i hw:0,0 -acodec pcm_s16le -filter:v yadif -aspect 1.77 -b 4000k -map 0:0 -map 1:0 output1.avi
ffmpeg version git-2012-03-25-6809818 Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar 25 2012 17:11:59 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
  libavutil      51. 44.100 / 51. 44.100
  libavcodec     54. 12.100 / 54. 12.100
  libavformat    54.  3.100 / 54.  3.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 65.102 /  2. 65.102
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 10.100 /  0. 10.100
  libpostproc    52.  0.100 / 52.  0.100
bad sync on line 0 @0 (0000)
resync after 221 @220(00dc)
bad sync on line 0 @484 (01e4)
bad sync on line 0 @0 (0000)
resync after 441 @440(01b8)
[rawvideo @ 0x9837d20] Estimating duration from bitrate, this may be inaccurate
Input #0, rawvideo, from 'pipe:':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: rawvideo (2vuy / 0x79757632), uyvy422, 720x480, 25 tbr, 25 tbn, 25 tbc
[alsa @ 0x98466c0] Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'hw:0,0':
  Duration: N/A, start: 1335222749.570302, bitrate: 1536 kb/s
    Stream #1:0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Please use -b:a or -b:v, -b is ambiguous
Incompatible pixel format 'uyvy422' for codec 'mpeg4', auto-selecting format 'yuv420p'
[buffer @ 0x9856780] w:720 h:480 pixfmt:uyvy422 tb:1/1000000 sar:0/1 sws_param:
[yadif @ 0x9843880] mode:0 parity:-1 auto_enable:0
[yadif @ 0x9843880] auto-inserting filter 'auto-inserted scale 0' between the filter 'src' and the filter 'Parsed_yadif_0'
[scale @ 0x98440a0] w:720 h:480 fmt:uyvy422 sar:0/1 -> w:720 h:480 fmt:yuv420p sar:0/1 flags:0x4
Output #0, avi, to 'output1.avi':
  Metadata:
    ISFT            : Lavf54.3.100
    Stream #0:0: Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 720x480 [SAR 59:50 DAR 177:100], q=2-31, 4000 kb/s, 25 tbn, 25 tbc
    Stream #0:1: Audio: pcm_s16le ([1][0][0][0] / 0x0001), 48000 Hz, 2 channels, s16, 1536 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> mpeg4)
  Stream #1:0 -> #0:1 (pcm_s16le -> pcm_s16le)
[avi @ 0x98527a0] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1419 >= 1419
av_interleaved_write_frame(): Invalid argument
```

Trying the alternate map options producing no files and this in the terminal:
```
somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 | ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -i - -f alsa -ac 2 -i hw:0,0 -acodec pcm_s16le -filter:v yadif -aspect 1.77 -b 4000k -map 0 -map 0:a:1 output1.avi
ffmpeg version git-2012-03-25-6809818 Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar 25 2012 17:11:59 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
  libavutil      51. 44.100 / 51. 44.100
  libavcodec     54. 12.100 / 54. 12.100
  libavformat    54.  3.100 / 54.  3.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 65.102 /  2. 65.102
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 10.100 /  0. 10.100
  libpostproc    52.  0.100 / 52.  0.100
bad sync on line 0 @0 (0000)
resync after 997 @996(03e4)
bad sync on line 0 @240 (00f0)
bad sync on line 0 @0 (0000)
resync after 431 @430(01ae)
[rawvideo @ 0xaee7d20] Estimating duration from bitrate, this may be inaccurate
Input #0, rawvideo, from 'pipe:':
  Duration: N/A, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: rawvideo (2vuy / 0x79757632), uyvy422, 720x480, 25 tbr, 25 tbn, 25 tbc
[alsa @ 0xaef66c0] Estimating duration from bitrate, this may be inaccurate
Input #1, alsa, from 'hw:0,0':
  Duration: N/A, start: 1335222848.331287, bitrate: 1536 kb/s
    Stream #1:0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Please use -b:a or -b:v, -b is ambiguous
Stream map '0:a:1' matches no streams.
```


So we are close ;)

I am aware of the pix_fmt problem, the video capture works properly if I use uyvy422 in the chain, but not if I put yuv420p (weird). And what are the comments about "-b" all about, not seen those before. I tried a "-b:a" and the comment went away, but don't understand what or why ;)

---

### Post by Jose Catre-Vandis on 2012-04-24
OK, got it working with this:
```
sudo somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 | \
ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -i - -f alsa \
-ac 2 -i hw:0,0 -filter:v yadif -aspect 1.77 -b 4000k -map 0:0 -map 1:0 \
output1.avi
```

But audio appears to start off in sync but by the end of a 1 minute clip is @ 6 seconds ahead of video. I had to take out -acodec pcm_s16le, so ffmpeg reverts to using libmp3lame. This may have something to do with framerate as the capture card requires ntsc for a good picture but is outputting at 25 fps. I tried putting -r 30 before the output1.avi in the chain but this didn't help with a/v sync.

How to get a/v sync then ?

Here is the ffmpeg -i output of the resultant file:
> Stream #0:0: Video: mpeg4 (Simple Profile) (FMP4 / 0x34504D46), yuv420p, 720x480 [SAR 59:50 DAR 177:100], 25 tbr, 25 tbn, 25 tbc
Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, stereo, s16, 128 kb/s

[EDIT] I put a movie DVD in the xbox and captured a clip, a/v was good. There is a delay before capturing starts which I don't see when trying to capture gameplay or the Xbox menu display

If it helps this is the playback only command, using mplayer:
> somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 | mplayer -nocache -vf yadif -demuxer rawvideo -rawvideo "ntsc:format=uyvy:fps=30000/1001" -aspect 1.77 -

---

### Post by Jose Catre-Vandis on 2012-04-26
bump

---

### Post by FakeOutdoorsman on 2012-04-27
> **Jose Catre-Vandis said:**
> 
And what are the comments about "-b" all about, not seen those before. I tried a "-b:a" and the comment went away, but don't understand what or why ;)
The functionality of *-b* has been changed and made more specific:
> It is now possible to precisely specify which stream should an AVOption apply to. E.g. -b:v:0 2M sets the bitrate for the first video stream, while -b:a 128k sets the bitrate for all audio streams. Note that the old -ab 128k syntax is deprecated.

> **Jose Catre-Vandis said:**
> But audio appears to start off in sync but by the end of a 1 minute clip is @ 6 seconds ahead of video. I had to take out -acodec pcm_s16le, so ffmpeg reverts to using libmp3lame. This may have something to do with framerate as the capture card requires ntsc for a good picture but is outputting at 25 fps. I tried putting -r 30 before the output1.avi in the chain but this didn't help with a/v sync.

Try moving *-r ntsc* or *-r 30000/1001* as an input option (before "-i -"). Also try it without "-filter:v yadif".

---

### Post by Jose Catre-Vandis on 2012-04-29
YAY!! :)

> sudo somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 | \
ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -r ntsc -i - \
-f alsa -ac 2 -i hw:0,0 -filter:v yadif -aspect 1.77 -qscale 2 output1.avi

Moving/putting **"-r ntsc"** before the **" -i - "** did the trick. I initially lost video quality, so tried -sameq then -qscale 2 did the trick. This works but is probably not right ;)

Many thanks for the pointers :)

After a bit more testing, too high a video bitrate was causing "alsa buffer xrun" 's which crashed the output video. So ended up working up from 500k to a final best of 2200k:
> sudo somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 | \
ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -r ntsc -i - \
-f alsa -i hw:0,0 -aspect 1.77 -b:v 2200k output1.avi

---

### Post by FakeOutdoorsman on 2012-04-29
> **Jose Catre-Vandis said:**
> I initially lost video quality, so tried -sameq then -qscale 2 did the trick. This works but is probably not right ;)

I usually recommend using *-qscale* for the encoder you're using ("mpeg4") unless it gives you the "alsa buffer xrun" as you've already mentioned. *-sameq* should be forgotten. It  does not mean "same quality" as the documentation used to imply and has limited usefulness.

---

