---
title: "No Audio with PVR-150"
date: 2008-06-16
forum: Multimedia Software
---

### Post by dshookowsky on 2008-06-16
My wife bought me a PVR-150 card for Father's day.  It was a white-box model that has a built-in FM tuner.  

I've gotten as far as getting video in MPlayer, VLC, and MythTV, but I don't get any audio out.  I DID get audio output for one brief moment by using:

```

v4l2-ctl -d /dev/video0 --set-audio-input=0

```

Note in the mplayer output, that I've tried the following variations with no change in behavior

```

mplayer /dev/video0
mplayer /dev/video0 -ao sdl
aoss mplayer /dev/video0

```


Here are the details that I can think to show

```

dmesg | grep ivtv
[   46.424466] ivtv:  Start initialization, version 1.1.0
[   46.424639] ivtv0: Initializing card #0
[   46.424643] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   46.434609] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   46.537800] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   46.676361] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   46.679374] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   47.163150] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   47.192502] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   47.254785] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   47.254835] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   47.254852] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   47.254867] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   47.254883] ivtv0: Registered device radio0 for encoder radio
[   47.254886] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   47.254907] ivtv:  End initialization
[   63.925784] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   64.124932] ivtv0: Encoder revision: 0x02060039

```

```

lsmod | grep ivtv
ivtv                  140352  0 
i2c_algo_bit            7300  2 bttv,ivtv
cx2341x                13444  1 ivtv
tveeprom               16656  2 bttv,ivtv
videodev               29440  2 bttv,ivtv
v4l2_common            18304  7 bttv,wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15492  3 bttv,ivtv,videodev
i2c_core               24832  14 bttv,wm8775,cx25840,nvidia,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,ivtv,i2c_algo_bit,tveeprom,i2c_nforce2

```

```

cat /proc/asound/cards
 0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x531102) at 0xc000, irq 21

```

```

mplayer /dev/video0
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 2800+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
VIDEO:  MPEG2  640x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 640 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12 
A:  15.4 V:  14.5 A-V:  0.844 ct: -0.803 397/397 10%  4% 26.2% 50 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

```

```

$ v4l2-dbg -C
host 0x0: cx23416    revision 0x00000000
i2c 0x1b: wm8775     revision 0x00000000
i2c 0x44: cx25843    revision 0x00008434

```

```

$ls -l /dev/video*
crw-rw----+ 1 root video 81,  0 2008-06-15 23:58 /dev/video0
crw-rw----+ 1 root video 81, 24 2008-06-15 23:58 /dev/video24
crw-rw----+ 1 root video 81, 32 2008-06-15 23:58 /dev/video32

$groups
shookow adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev sambashare mythtv

```

---

### Post by dshookowsky on 2008-06-16
The inevitable result of posting that it doesn't work on the forums is to have it work.  Kind of.  I restarted my machine and fired up the mythtv-backend.  When I went to watch video, I had low-volume audio as well.  

I was just going to post that I couldn't make it work in mplayer, but decided to test it and of course that's working now too.

---

### Post by wolfen69 on 2008-06-16
you probably need to do the [PulseAudioFix]("http://ubuntuforums.org/showthread.php?t=776739")

---

