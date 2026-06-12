---
title: "mencoder and v4l2 capture"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by xolot1 on 2007-02-21
i got a rather old camcorder that uses Hi8 tapes for storage.  i can connected to my TV card using Composite cables, and have finally started making progress in capturing data from the camera.

first i tried using mencoder with v4l2 drivers to capture, and then backed up to a more general task: playing the video stream in mplayer. i get the same error in both cases:

v4l2: ioctl streamon failed: Device or resource busy

does anyone know what this means, or what i could try?

full command and output below
```
willi@athlon:~/Desktop$ mplayer -tv driver=v4l2:width=320:height=240:device=/dev/video0:fps=25:norm=4 -vo gl:nomanyfmts tv://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) Processor (Family: 6, Model: 6, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing tv://.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Sabrent SBT-TVFM (saa7130)
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = PAL-BG; 2 = PAL-I; 3 = PAL-DK; 4 = NTSC; 5 = SECAM; 6 = PAL-M; 7 = PAL-Nc; 8 = PAL-60;
 inputs: 0 = Composite1; 1 = Television; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : MONO
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
No accelerated colorspace conversion found
SwScaler: using unscaled Planar YV12 -> RGBA special converter
VO: [gl] 320x240 => 320x240 RGBA 
libGL warning: 3D driver claims to not support visual 0x4b
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Starting playback...
v4l2: ioctl streamon failed: Device or resource busy
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (Quit)

```

---

### Post by lexen on 2008-01-11
I have the same setup, but I don't have that problem.  I get an output file which does show the input, but it is all messed up.  I am using this command:

mencoder -tv driver=v4l2:width=640:height=480:norm=8:input=1 -oac mp3lame -lameopts cbr:br=64\
    -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=900 \
    -o test001.mp4 tv://

     I am using a composite input which is input 1 not input 0, which it is by default.  Maybe you have to change your input?  Are you using NTSC or PAL?  I am using NTSC.

     The problem with mine is the output is muted and the video is messed up.  I have uploaded two screen shots, one is of a blank screen, the other is when there is an actual input.

     Maybe we can work together and fix both our problems?



Thanks,
Lexen

---

### Post by lexen on 2008-01-15
I have gotten a few steps farther but not the whole way.  Here is the command that I am putting in now:

mencoder -tv driver=v4l2:norm=7:input=1:device=/dev/video0:immediatemode=0:forceaudio:outfmt=yv12 -oac mp3lame -lameopts cbr:br=128 -srate 48000 -af lavcresample=48000\
    -ovc xvid -xvidencopts bitrate=900 \
    -o test001.avi tv:// -endpos 5

I put "-endpos 5" at the end so it would stop after 5 seconds for testing purposes.

I am getting audio now, but it doesn't sound right.  For some reason I need to record at 48000 Hz or it will sound bad.  I thought I had that covered in the command, but it still puts it at 44100.

Here is the full output:

MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: UNKNOWN/GENERIC
 Capabilites:  video capture  VBI capture device  read/write  streaming
 supported norms: 0 = PAL-BG; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = PAL-60; 7 = NTSC-M; 8 = NTSC-M-JP; 9 = NTSC-443; 10 = SECAM-DK; 11 = SECAM-L;
 inputs: 0 = Composite1; 1 = Composite2; 2 = Composite3; 3 = Composite4;
 Current input: 1
 Current format: BGR24
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(7): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
[V] filefmt:9  fourcc:0x42475218  size:640x480  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
xvid: using library version 1.1.2 (build xvid-1.1.2)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: BGR 24-bit)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using BGR 24-bit as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x8800710]SwScaler: using unscaled bgr24 -> yuv420p special converter
videocodec: XviD (640x480 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=640x480, sampled=640x480
xvid: CBR Rate Control -- bitrate=900kbit/s
Selected video codec: [rawbgr24] vfm: raw (RAW BGR24)
==========================================================================


Here are the lines that worry me:

Selected device: UNKNOWN/GENERIC

 Current format: BGR24
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(7): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!

AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)


It seems like it doesn't really know what my video card is and it also didn't change the sample rate.  Any help would be greatly appreciated. 


Thanks,
Lexen

---

### Post by lexen on 2008-01-25
I have gotten a lot farther.  I can now upload video and audio without much of a hitch, the only problem I have is that I still can't get the audio to record at 48000Hz.  Here is the command that I am using:

mencoder -o test001.avi \
 -ovc lavc -lavcopts vcodec=msmpeg4:vbitrate=4000: \
 -af volume=10 \
 -ofps 20 \
 -tv driver=v4l2:norm=NTSC-M:input=1:brightness=45:contrast=-10:hue=0:saturation=20:immediatemode=0:forceaudio:outfmt=yv12 -oac mp3lame -lameopts cbr:br=128 -srate 48000 \
 tv:// -endpos 5:00

   To speed things up, I made a new file and called it video.sh and pasted the command in it.  Then I log into a failsafe session and put in the command "/home/lexen2/video.sh" 

   After a while it says "video buffer full" which sounds really bad.  Even though the output seems to be okay, it would be nice if I could get it to stop saying that.



Thanks,
Lexen

---

### Post by xzero1 on 2008-02-04
:)I have excellent results using the following command line:

```
 mencoder -ffourcc XVID -oac lavc -ovc lavc -lavcopts vcodec=mpeg4:mv0:trell:v4mv:vbitrate=3000:ildct:aspect=16/9:acodec=mp2 -tv driver=v4l2:norm=ntsc:input=2:adevice=/dev/dsp:width=720:height=480 -o test.avi tv://
```

This is realtime svideo capture at 720x480 NTSC on a athlon x2 4400 cpu.. It uses mp2 audio (slightly bigger but faster then mp3) and plays on a xvid compatible dvd player.

Note: if you get 'buffer full' then the cpu probably can't keep up with the encoding and must drop some frames. This could be acceptable if only a few are dropped.  Make a note of mencoder's fps display -- it should be very close to your intended frame rate. You can play back the encoded video file *while* encoding using vlc. This is useful for testing various recording parameters or to monitor the output.

---

### Post by lexen on 2008-02-09
How could I make it so my code could run faster?  Can you show me how to switch my audio encoding to MP2 or whatever else is fast?  I am really having a problem with speed, so I want to scale back in areas that don't really lower quality.  I don't know how to add options, so if someone could tell me where to put what option, that would be great.



Thanks,
Lexen

---

### Post by gengiskanhg on 2008-02-10
I had proved with these two codes but the same problem appear for me:

mencoder -tv norm=NTSC:chanlist=us-bcast:driver=v4l2:width=720:height=576:input=1:fps=25 tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=3000:vbitrate=1800:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o capture.mpg -endpos 01:30

mencoder -ffourcc XVID -oac lavc -ovc lavc -lavcopts vcodec=mpeg4:mv0:trell:v4mv:vbitrate=3000:ildct:aspect=16/9:acodec=mp2:abitrate=192 -tv driver=v4l2:norm=ntsc:input=1:width=720:height=480 -o test.avi tv:// -endpos 01:30

My problem is that several frames are dropped after second 60 or 90. Quality is good for me, audio is getting in by the mic jack. I use and WIN TV turner.

I had proved with the "fail mode boot terminal" but the same problem appear, any advantages... (well, the sound do not works in the terminal) worst!!!

I will be attend to help us each other in order to achieved our goal.

Thanks.

---

### Post by lexen on 2008-02-10
gengiskanhg:  Did you try using the code that xzero1 or I posted?  They might work for you if you change some of the numbers.  Audio was a weird thing for me, it just started working and I don't remember why.  Did you put the command in a .sh file?  Because that is really great and it makes it so you don't have to worry about a mistype because if it worked before, it should work again.


Thanks,
Lexen

---

### Post by xzero1 on 2008-02-11
There is always a speed vs quality tradeoff. There may be other codecs that are more efficient on your system. You might capture raw and then convert to your desired format. There are hardware based capture cards available. Dropping a frame here and there should not be an issue quality wise. Try the x264 codec -- especially if you have SMP capability. Another nice thing is mencoder can use its own config file (mencoder.conf) which helps to tune your capture.

My mencoder.conf:

```
[xvid]
profile-desc="XVID/MPEG4 capture"
quiet=1
ffourcc=XVID
oac=lavc=1
ovc=lavc=1 
lavcopts=vcodec=mpeg4:mv0=1:trell=1:v4mv=1:vbitrate=3000:ildct=1:aspect=16/9:acodec=mp2 
tv=driver=v4l2:norm=ntsc:input=2:adevice=/dev/dsp:width=720:height=480

[x264]
profile-desc="x264 capture"
oac=lavc=1
ovc=x264=1
x264encopts=crf=22:threads=2
tv=driver=v4l2:norm=ntsc:input=2:adevice=/dev/dsp:width=720:height=480

```

Using the above my command line simply becomes:
 mencoder -profile x264 -o test.avc tv://
or
mencoder -profile xvid -o test.avi tv://

For x264, 'crf' ranges from 0 (lossless) to something like 52 and is the only tuning parameter I use and makes a hugh difference in quality.

---

