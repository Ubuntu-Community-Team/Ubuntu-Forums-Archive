---
title: "Can't get cable TV - Kworld115"
date: 2009-06-25
forum: Multimedia Software
---

### Post by speeddad on 2009-06-25
Hi,

I can not get cable TV to come in on my Kworld115 card.  I can get over the air HDTV.  The system is dualboot and cable comes in while in windows.

I an using kubuntu 8.04.

I have tried me-tv, kdetv, TVtime, XawTV, MythTV and KMPlayer.  All with no success.  If I scan for broadcast channels kdetv and TVtime give me two old analog stations, with no sound.  If I scan for cable with kdetv or TVtime, I get two or three channels that are colored static an dlines.  me-tv tries to scan (it seems to work best if I select us-NY-TWC-NYC), but usually crashes and leaves an invalid channels.conf.  XawTV just has a blank screen.  MythTV gives a database error in setup.

I created a channels.conf using the code below, but nothing has been able to recognize it.

```
/usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > /home/speeddad/.mplayer/channels.conf
```

dmesg | grep -i saa713 returned

```
[   43.745079] saa7130/34: v4l2 driver version 0.2.14 loaded
[   43.745135] saa7133[0]: found at 0000:03:07.0, rev: 209, irq: 21, latency: 32, mmio: 0xfddff000
[   43.745142] saa7133[0]: subsystem: 17de:7352, board: Kworld ATSC110/115 [card=90,insmod option]
[   43.745148] saa7133[0]: board init: gpio is 100
[   43.879910] saa7133[0]: i2c eeprom 00: de 17 52 73 ff ff ff ff ff ff ff ff ff ff ff ff
[   43.879917] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.879921] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.879924] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.879928] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.879931] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.879935] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   43.879939] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   44.044103] tuner 1-0061: chip found @ 0xc2 (saa7133[0])
[   44.068679] saa7133[0]: registered device video0 [v4l2]
[   44.068693] saa7133[0]: registered device vbi0
[   44.151597] saa7134 ALSA driver for DMA sound loaded
[   44.151616] saa7133[0]/alsa: saa7133[0] at 0xfddff000 irq 21 registered as card -2
[   44.299868] DVB: registering new adapter (saa7133[0])
```

dmesg | grep -i nxt200 returned

```
[   44.259840] nxt200x: NXT2004 Detected
[   44.299872] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   44.307835] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   45.934192] nxt2004: Waiting for firmware upload(2)...
[   47.479294] nxt2004: Firmware upload complete
```

When I run KMplayer in console, I get the following.

```
MPlayer 1.0rc2-4.2.4 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Kworld ATSC110/115
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = PAL-BG; 2 = PAL-I; 3 = PAL-DK; 4 = NTSC; 5 = SECAM; 6 = SECAM-DK; 7 = SECAM-L; 8 = SECAM-Lc; 9 = PAL-M; 10 = PAL-Nc; 11 = PAL-60;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : MONO
ID_VIDEO_ID=0
ID_FILENAME=tv://
ID_DEMUXER=tv
ID_VIDEO_FORMAT=YV12
ID_VIDEO_BITRATE=0
ID_VIDEO_FPS=25.000
xscreensaver_disable: Could not find XScreenSaver window.
Opening video filter: [pp=lb]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
ID_VIDEO_CODEC=rawyv12
Audio: no sound
Starting playback...
```


Please help me.  Booting into windows makes me feel dirty.

---

