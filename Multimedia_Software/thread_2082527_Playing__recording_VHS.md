---
title: "Playing / recording VHS"
date: 2012-11-09
forum: Multimedia Software
---

### Post by George Heine on 2012-11-09
My long-term project is to copy some aging VHS tapes to disk, and then write them
out as DVD video.  Figured the first step is to just be able to play the tapes on my PC.

I happened to have a Pinnacle Dazzle DVD recorder, so I plugged it into the VCR and to
a USB port on the PC, turned on the VCR, and entered

 ```
 $ mplayer tv://
```Suprisingly, it worked.  Well, sort of.  The picture was in black and white (the video is in color) and there was no sound. I tried with a second set of cables to eliminate the possibility of a bad wire; same result.

So, what do I need to do to get a full-color video with sound to play on my PC?  Going further, what do I need to do to rip a copy of the video to disc, preferably in a format that can easily be transferred to DVD video ?  

-thanks for any help -

Running Ubuntu 12.04 LTS, running mplayer from the repo and  ffmpeg compiled on 25 October using instructions[ here]("https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide").

 Here is a screen dump of the mplayer output:

```
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Pinnacle Dazzle DVC 90/100/101/
 Capabilities:  video capture  audio  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = NTSC-443; 5 = PAL; 6 = PAL-BG; 7 = PAL-H; 8 = PAL-I; 9 = PAL-DK; 10 = PAL-M; 11 = PAL-N; 12 = PAL-Nc; 13 = PAL-60; 14 = SECAM; 15 = SECAM-B; 16 = SECAM-G; 17 = SECAM-H; 18 = SECAM-DK; 19 = SECAM-L; 20 = SECAM-Lc;
 inputs: 0 = Composite1; 1 = S-Video;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
Selected input hasn't got a tuner!
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed YUY2
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0 1121/1121 ??% ??% ??,?% 0 0
v4l2: 1123 frames successfully processed, -186 frames dropped.
```And here is the output of dmesg after the Dazzle was connected:
```

[  217.512073] usb 1-5: new high-speed USB device number 4 using ehci_hcd
[  217.770065] IR NEC protocol handler initialized
[  217.776284] IR RC5(x) protocol handler initialized
[  217.799241] Linux video capture interface: v2.00
[  217.804727] IR RC6 protocol handler initialized
[  217.827417] IR JVC protocol handler initialized
[  217.874317] em28xx: New device Pinnacle Systems GmbH DVC90 @ 480 Mbps (2304:0
207, interface 0, class 0)
[  217.875536] em28xx #0: chip ID is em2820 (or em2710)
[  217.900992] IR Sony protocol handler initialized
[  217.905257] IR MCE Keyboard/mouse protocol handler initialized
[  217.922895] lirc_dev: IR Remote Control driver registered, major 250
[  217.927158] IR LIRC bridge handler initialized
[  218.002225] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 07 02 12 00 11 03 98 0e 6a 2e
....
[  218.002739] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xec7d5672
[  218.002745] em28xx #0: EEPROM info:
[  218.002750] em28xx #0:       AC97 audio (5 sample rates)
[  218.002755] em28xx #0:       300mA max power
[  218.002762] em28xx #0:       Table at 0x06, strings=0x0e98, 0x2e6a, 0x0000
[  218.003845] em28xx #0: Identified as Pinnacle Dazzle DVC 90/100/101/107 / Kaiser Baas Video to DVD maker / Kworld DVD Maker 2 (card=9)
[  218.396670] saa7115 14-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[  219.164433] em28xx #0: Config register raw data: 0x12
[  219.188297] em28xx #0: AC97 vendor ID = 0xffffffff
[  219.200292] em28xx #0: AC97 features = 0x6a90
[  219.200299] em28xx #0: Empia 202 AC97 audio processor detected
[  219.660330] em28xx #0: v4l2 driver version 0.1.3
[  220.588282] em28xx #0: V4L2 video device registered as video0
[  220.588329] em28xx audio device (2304:0207): interface 1, class 1
[  220.588359] em28xx audio device (2304:0207): interface 2, class 1
[  220.588412] usbcore: registered new interface driver em28xx
[  220.588418] em28xx driver loaded
[  220.707664] usbcore: registered new interface driver snd-usb-audio
```

---

### Post by George Heine on 2012-11-11
Some progress.  Based on suggestions posted at this [website]("http://radagast.ca/linux/vhs_to_dvd.html") (maintained, or was maintained at one time, by someone named Andrew) ,  was able to play in color with the following:  

```
mplayer tv:// -tv driver=v4l2:device=/dev/video0:input=0:norm=ntsc:adevice=/dev/audio0
```However, there is still no audio.  Tried using /dev/audio1 instead of /dev/audio0; no luck.


The link above provided several scripts to record VHS playback using mencoder, such as ```
mencoder tv:// -tv driver=v4l2:device=/dev/video0:input=1:norm=ntsc:adevice=/dev/audio0  -ovc lavc -oac lavc -lavcopts acodec=ac3:vcodec=mpeg2video:vbitrate=5000 -of mpeg -ofps 30000/1001  -o tv.mpeg
```   Failed with a message ```
Unable to open '/dev/audio0': No such file or directory
v4l2: 0 frames successfully processed, 0 frames dropped.
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
```Any suggestions would be welcome

---

### Post by BicyclerBoy on 2012-11-11
With your USB capture device not plugged in, run this terminal:
arecord -l

Plug in the USB device:
arecord -l
try to determine which is the audio device..

You can use v4lctl
[http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing](http://www.linuxtv.org/wiki/index.php/V4L_TV_Viewing)
to control settings etc..

You can capture/play with ffmpeg/fplay.
To capture to file simlar to DVD formats:
ffmpeg -f alsa -i hw:0 -f video4linux2 -framerate 25 -video_size 768x576 -i /dev/video0 -c:v mpeg2video -flags +ilme+ildct tmp.mpg

The "-i hw:0" bit has to be changed to suit your h/w.
If you are dealing with ntsc then 
- framerate  30 -videosize 640x480
You should capture & maintain the video interlacing for the target DVD.

---

### Post by George Heine on 2012-11-11
BicyclerBoy, thanks for your input.

> With your USB capture device not plugged in, run this terminal:
arecord -l

Plug in the USB device:
arecord -l
try to determine which is the audio device.. OK, here's the output  after the capture device is plugged in ("card 1") 
```
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: DVC90 [DVC90], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Studying the arecord man page, was able to get audio input by ```
$ arecord -D hw:CARD=DVC90,DEV=0 -r 44100 -c 2 -f S16_LE |aplay -
```At least the hardware works.  I did need to specify the CARD and DEVICE names; with just "hw:0" , no errors are reported, but there is no sound.  

So, how do I translate these specs over to an mplayer/mencoder/ffmpeg command line?  Am assuming it's something like ```
mplayer tv:// -tv driver=v4l2:device=/dev/video0:input=0:norm=ntsc:**adevice=hw.0**:amode=2:audiorate=44100:forceaudio:immediatemode=0

```but can't seem to get the syntax right.

---

### Post by BicyclerBoy on 2012-11-11
This might work:
ffmpeg -f alsa -i hw:1 -f video4linux2 -framerate 30 -video_size 640x480 -i /dev/video0 -c:v mpeg2video -flags +ilme+ildct tmp.mpg

arecord -c 2 -r 48000 -D hw:1

hw:0 would be your onboard mic/line-in

You can check the video with
ffplay -f video4linux2 -framerate 30 -video_size 640x480

I haven't figured out how to get ffplay to use the alsa input..

I suspect that your mplayer cmd is using OSS sound interface so maybe something like this: adevice=hw=1.0:arate=32000..
Have to use "=" for ":" & replace "," with ".".

Mencoder is a deprecated part of mplayer project.

---

### Post by George Heine on 2012-11-15
```
arecord -c 2 -r 48000 -D hw:1
```This works to capture audio from the VCR.

Switched to a different computer, which has an onboard camera (/dev/video0) as well as an onboard mike (hw:0), and used:```
ffmpeg -f alsa -i hw:0 -f video4linux2  -video_size 640x480  -i /dev/video0 -c:v mpeg2video -flags +ilme+ildct tmp.mpg
```   The above command works and the output video plays with sound in both mplayer (a little out of sync) and in ffplay.  
Using /dev/video1 and hw:1:  ```
ffmpeg -f alsa -i hw:1 -f video4linux2  -video_size 640x480  -i /dev/video1 -c:v mpeg2video -flags +ilme+ildct tmp.mpg
``` a video is recorded and there are no error messages about sound, but no sound is audible with the video.

Any ideas?

---

### Post by BicyclerBoy on 2012-11-16
Try adding an input channel count/samplerate option & audio codec:

ffmpeg -f alsa -ac 2 -ar 48000 -i hw:1 -c:a mp2 -f video4linux2 -framerate 30 -i /dev/video0 -video_size 640x480 -c:v mpeg2video -flags +ilme+ildct tmp.mpg

Possibly we have not identified the correct audio input..
aplay -l

could need to use -i hw:1,0 or -i hw:1,1

Note: use "q" to stop ffmpeg capture...using <ctrl>+<c> leaves things hanging..
close/re-open terminal if things go wrong..

---

### Post by jond5789 on 2012-11-24
Maybe this will help ... I have a DVC90 and finally figured out why I could only get audio with mplayer/mencoder and never with avconv/ffmpeg: apparently the device defaults to audio muted (which mplayer handles fine). But for avconv/ffmpeg, you can do the same with v4l2-ctl before calling avconv ...

videoinput=0 # 0 composite, 1 svideo

v4l2-ctl --set-standard=ntsc  --set-input=$videoinput --set-ctrl=mute=0

---

### Post by Dale61 on 2012-11-26
I'm probably out of line and not in the spirit of this thread, but of you have connected a DVD recorder to your VHS VCR, why not just copy the VHS content direct to the DVD recorder?

We had access to the whole Stephen King boxset on VHS, and we copied all the tapes to our DVD recorder, but mind you, it does have a 250GB internal HDD.

---

### Post by George Heine on 2013-03-14
Happened on a soluiton to getting ffmpeg to record both video and audio.  
First step is to get the small v4l2ucp package from the repos.
At the command line, enter
```
v4l2ucp <devicename>
```
Where "<devicename>" is how your system recognizes the USB connection to your VHS;
on my system, this is /dev/video1, (/dev/video0 is the builtin webcam).
A gui menu pops up; uncheck the box that says "mute", save changes, and exit.
Then enter
```
ffmpeg -f alsa -i hw:CARD=DVC90 -f video4linux2  -video_size 640x480 -i /dev/video1 -c:v mpeg2video -flags +ilme+ildct tmp.mpg
```;
and the video, full color with audio, will be recorded.

NOTES:
1) if you access the VCR with other software, such as mplayer, you may need unmute the audio again before recording.
2) Haven't yet found a command-line alternative to v4l2ucp.  There is a program called "v4l2ctrl", but documentation is very sketchy.  I believe there is also a v4l2 module in python.
3) The audio and video are still slightly out of sync, but that is the subject for a different thread.

---

