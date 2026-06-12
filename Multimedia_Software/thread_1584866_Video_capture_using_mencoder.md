---
title: "Video capture using mencoder"
date: 2010-09-29
forum: Multimedia Software
---

### Post by ssaguiar on 2010-09-29
Hi to all.

I am working in a script I have, to capture video with sound from my capture board, wich is a clone of the pico2000.
This script was working in Ubuntu 9.10 untill I reformated my machine and instaled the Ubuntu 10.10, 64 bits.
The machine is an AMD Athlon II, 2.6GHz with 3 GBytes of Ram.
The former script was:
```

#!/bin/bash
clear
SERVICE="mencoder"
MOVIE=$(date +"%H%M")
NEWDIR=$(date +"/mnt/sdb/capture/%m-%Y/%d/%H/cam1/hd")
NEWDIR2=$(date +"/mnt/sdb/capture/%m-%Y/%d/%H/cam2/hd")

WIDTH=640
HEIGHT=480
AUDIOBITRATE=192
FRAMERATE="30000/1001"
ASPECT="4/3"
VIDEOCODEC="mpeg2video"
SERVICE='mencoder'
VIDEOINPUT=1
VIDEOINPUT2=2
NORMID=1
VIDEODEVICE="/dev/video1"
VIDEODEVICE2="/dev/video0"
VIDEOBITRATE=1600
VIDEOMAXBITRATE=2000
AUDIODEVICE="/dev/dsp"
AUDIORATE=44100
AUDIOCODEC="ac3"


if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
killall -15 $SERVICE
#sleep 3
fi

if [ ! -d "$NEWDIR" ]
then
mkdir -p $NEWDIR
fi

 mencoder \
    -quiet -msglevel all=-1 tv:// \
    -tv driver=v4l2:width=$WIDTH:height=$HEIGHT:input=$VIDEOINPUT:normid=$NORMID:device=$VIDEODEVICE:adevice=$AUDIODEVICE:audiorate=$AUDIORATE:immediatemode=0:forceaudio \
    -oac lavc \
    -ovc lavc \
    -of mpeg \
    -mpegopts format=dvd:tsaf \
    -vf pp=lb,harddup \
    -srate 48000 \
    -af lavcresample=48000 \
    -lavcopts vcodec=$VIDEOCODEC:vrc_buf_size=1835:vrc_maxrate=$VIDEOMAXBITRATE:vbitrate=$VIDEOBITRATE:keyint=18:vstrict=0:acodec=$AUDIOCODEC:abitrate=$AUDIOBITRATE:aspect=$ASPECT \
    -ofps $FRAMERATE \
    -o $NEWDIR/$MOVIE.mpg&

```Now, after instaling the Ubuntu 10.10, the script doesn't work anymore because there are no more the devices dsp and dsp1 I had in /dev.
The Ubuntu team seem to prefer alsa, so, now, we need to use it.
For this, I changed the script to:

```

mencoder -quiet -msglevel all=-1 tv:// \
-tv driver=v4l2:immediatemode=0:alsa:adevice=hw.0,0:input=2:width=640:height=480:input=0:normid=1:device=/dev/video1 \
-oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf  \
-vf-add kerndeint=10:0:0:1:1 eq2=1.0:0.7:0:1.5:1.0:1.0:1.0 -srate 48000 -af lavcresample=48000 \
-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=4000:vbitrate=2000:\
keyint=18:vstrict=0:aspect=4/3 -ofps 30000/1001 \
-o $NEWDIR/$MOVIE.mpg&

```With this, now I have problems with a lot of duplicated frames and some dropped frames.
Anyody can help me to solve this?

This is the output of the command line:
```

 mencoder tv:// \
> -tv driver=v4l2:immediatemode=0:alsa:adevice=hw.0,0:input=2:width=640:height=480:input=0:normid=1:device=/dev/video1 \
> -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf  \
> -vf-add kerndeint=10:0:0:1:1 eq2=1.0:0.7:0:1.5:1.0:1.0:1.0 -srate 48000 -af lavcresample=48000 \
> -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=4000:vbitrate=2000:\
> keyint=18:vstrict=0:aspect=4/3 -ofps 30000/1001 \
> -o test.mpg

```output:
```

MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: BT878 video ( *** UNKNOWN/GENER
 Capabilites:  video capture  video overlay  VBI capture device  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = PAL; 5 = PAL-BG; 6 = PAL-H; 7 = PAL-I; 8 = PAL-DK; 9 = PAL-M; 10 = PAL-N; 11 = PAL-Nc; 12 = PAL-60; 13 = SECAM; 14 = SECAM-B; 15 = SECAM-G; 16 = SECAM-H; 17 = SECAM-DK; 18 = SECAM-L; 19 = SECAM-Lc;
 inputs: 0 = Composite0; 1 = Composite1; 2 = S-Video; 3 = Composite3;
 Current input: 0
 Current format: YVU420
Selected input hasn't got a tuner!
[V] filefmt:9  fourcc:0x32315659  size:640x480  fps:29.970  ftime:=0.0334
PACKET SIZE: 2048 bytes, deltascr: 43885
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [kerndeint=10:0:0:1:1]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (640x480 fourcc=3267706d [mpg2])
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Limiting audio preload to 0.4s.
Increasing audio density to 4.
Forcing audio preload to 0, max pts correction to 0.
Writing header...
INITV: 0.200, 0.167, fps: 29.970
Pos:   0.4s     13f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:   0.5s     15f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:   1.5s     44f ( 0%) 27.85fps Trem:   0min   0mb  A-V:0.000 [3168:0]
Skipping frame!
Pos:   1.6s     46f ( 0%) 27.85fps Trem:   0min   0mb  A-V:0.000 [3135:0]
Skipping frame!
Pos:   1.6s     48f ( 0%) 28.00fps Trem:   0min   0mb  A-V:0.000 [3108:0]
Skipping frame!
Pos:   1.6s     49f ( 0%) 28.24fps Trem:   0min   0mb  A-V:0.000 [3108:0]
Skipping frame!
Pos:   1.6s     51f ( 0%) 28.05fps Trem:   0min   0mb  A-V:0.000 [3084:0]
Skipping frame!
Pos:   1.7s     53f ( 0%) 28.19fps Trem:   0min   0mb  A-V:0.000 [3059:0]
Skipping frame!
Pos:   1.7s     54f ( 0%) 28.41fps Trem:   0min   0mb  A-V:0.000 [3059:0]
Skipping frame!
Pos:   1.7s     56f ( 0%) 28.25fps Trem:   0min   0mb  A-V:0.000 [3037:0]
Skipping frame!
Pos:   1.7s     58f ( 0%) 28.39fps Trem:   0min   0mb  A-V:0.000 [3010:0]
Skipping frame!
Pos:   1.7s     59f ( 0%) 28.45fps Trem:   0min   0mb  A-V:0.000 [3010:0]
Skipping frame!
^Cs:   1.8s     61f ( 0%) 28.44fps Trem:   0min   0mb  A-V:0.000 [2989:0]
Skipping frame!
Pos:   1.8s     62f ( 0%) 28.53fps Trem:   0min   0mb  A-V:0.000 [2989:0]
^CPos:   1.8s     63f ( 0%) 27.07fps Trem:   0min   0mb  A-V:0.000 [3535:0]
Flushing video frames.
Writing index...

Overhead: 2.682% (13051 / 486661)
Writing header...

Video stream: 3535.817 kbit/s  (441977 B/s)  size: 486661 bytes  1.101 secs  31 frames
v4l2: 33 frames successfully processed, 0 frames dropped.

```It keeps having lots of duplicate frames.


Thanks

---

### Post by flovo77 on 2011-01-15
I guess I had the same issue in a different set up: Capturing with an em28xx based video interface but using a separate sound hardware via ALSA.

Problem seems to be: The timing of your sound hardware runs out of phase and/or the driver is not as sync tolerant as it should be. 

Example: When using the on board sound hardware of my box, I get duplicate frames and drops but when using my external sound blaster MP3+ USB box as sound device, I have no problems at all.

Hope this helps,

Florian

---

