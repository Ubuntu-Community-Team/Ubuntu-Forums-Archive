---
title: "mplayer hdmi"
date: 2011-05-28
forum: Multimedia Software
---

### Post by dozycat on 2011-05-28
I got ubuntu 11.04 with kworld  and i want to use mplayer to see tv. And my sound is hdmi.

I can record with:

```

mencoder tv:// -tv driver=v4l2:norm=NTSC:fps=30000/1001:outfmt=yuy2:quality=0:input=0:width=720:height=578:chanlist=us-bcast:volume=80:amode=1:normid=0:audiorate=32000:alsa:adevice=hw.1:channel=3  -ovc x264 -x264encopts threads=2:bitrate=900:subq=2 -oac faac -faacopts br=192:mpeg=4:object=2 -endpos 00:01:00 -o prueba440.avi  

```thats itu h.264, still looking for h.264 avc.

or 

```
mencoder tv:// -tv driver=v4l2:norm=NTSC:fps=25:outfmt=yuy2:quality=0:input=0:width=720:height=578:chanlist=us-bcast:volume=80:amode=1:normid=0:audiorate=32000:alsa:adevice=hw.1:channel=3 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1500:keyint=25 -oac mp3lame -lameopts cbr:br=128:mode=0 -endpos 02:00:00 -vf pp=hb/vb/dr/al/lb,denoise3d -o prueba753.mpg
```thats FFmpeg MPEG-4, both records got sound.

But using the same options with mplayer.

```

mplayer tv:// -tv driver=v4l2:norm=NTSC:fps=30000/1001:outfmt=yuy2:quality=0:input=0:width=720:height=578:chanlist=us-bcast:volume=80:amode=1:normid=0:audiorate=32000:alsa:adevice=hw.1:channel=3 -ao alsa:device=hdmi
/CODE]
I got video but no sound, error:

[CODE]
mplayer  tv:// -tv driver=v4l2:norm=NTSC:fps=30000/1001:outfmt=yuy2:quality=0:input=0:width=720:height=578:chanlist=us-bcast:volume=80:amode=1:normid=0:audiorate=32000:alsa:adevice=hw.1:channel=3 -ao alsa:device=hw=1.3
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Kworld Plus TV Analog Lite PCI
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = PAL; 5 = PAL-BG; 6 = PAL-H; 7 = PAL-I; 8 = PAL-DK; 9 = PAL-M; 10 = PAL-N; 11 = PAL-Nc; 12 = PAL-60; 13 = SECAM; 14 = SECAM-B; 15 = SECAM-G; 16 = SECAM-H; 17 = SECAM-DK; 18 = SECAM-L; 19 = SECAM-Lc;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : STEREO
Selected channel: 3 (freq: 61.250)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...
v4l2: 233 frames successfully processed, 0 frames dropped.


```But:

```

mplayer -ao alsa:device=hdmi video.mpg

```The videos work perfectly.

Ptd: Any one knows how code in mencoder to H.264 / AVC.

---

