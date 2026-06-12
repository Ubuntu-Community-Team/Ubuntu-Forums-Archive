---
title: "Stuttering audio/video playback on Inspiron Mini10 after system updates"
date: 2015-09-20
forum: Multimedia Software
---

### Post by Juhele on 2015-09-20
Hi,
I am using Dell Inspiron Mini10 with 32bit Lubuntu 14.04 as a small travel machine for web/mail and rough photo filtering and backups to external HDD. I also put there few movies in non-HD resolution and it worked fine when nothing than SMPlayer was running. However, yesterday after some updates I found out that the video playback is simply terrible - sometimes it looks like the video playback speed is slightly higher but the audio is always stuttering.

Tried VLC, SMPlayer and Bomi, but no solution. Even movie 624x352 pixels is terrible.

Tried mplayer in console and it says this:

```
flynn@limetka:~/Zabava/Filmy$ mplayer Test_movie.avi
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Cannot open file '/home/flynn/.mplayer/input.conf': No such file or directory
Failed to open /home/flynn/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.

Playing Test_movie.avi.
Detected file format: AVI (Audio Video Interleaved) (libavformat)
[avi @ 0xb65be360]max_analyze_duration reached
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (mp3), -aid 0
Clip info:
encoder: Lavf54.63.104
Load subtitles in .
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
[ass] auto-open
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [libavcodec]
Selected audio codec: MPEG 1.0/2.0/2.5 layers I, II, III [mpg123]
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VIDEO: 1024x576 25.000 fps 0.0 kbps ( 0.0 kB/s)
VO: [x11] 1024x576 => 1024x576 Planar YV12
[swscaler @ 0xb649b920]using unscaled yuv420p -> bgra special converter
A: 4.6 V: 3.3 A-V: 1.267 ct: -0.020 0/ 0 28% 26% 3.3% 50 0


************************************************
**** Your system is too SLOW to play this! ****
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

A: 132.7 V: 104.9 A-V: 27.794 ct: -0.020 0/ 0 31% 23% 2.2% 2578 0

Exiting... (Quit)
flynn@limetka:~/Zabava/Filmy$
```

Choosing "SDL" is SMPlayer does not solve it. "Alsa" results in slighly better but still stuttering sound and looks like the video playback speed is higher than it should be.
Also tried to delete settings for smplayer and pulse in /home, but no effect. "Pulse" also no solution - still strange video and stuttering audio.

Here is part of hardinfo report for my PC - I know the hardware is weak but it worked some time ago:

```
Processor : 2x Intel(R) Atom(TM) CPU Z530 @ 1.60GHz
Memory : 1016MB (243MB used)
Operating System : Ubuntu 14.04.3 LTS
-Display-
Resolution : 1366x768 pixels
OpenGL Renderer : Unknown
X11 Vendor : The X.Org Foundation
-Multimedia-
Audio Adapter : HDA-Intel - HDA Intel MID
VGA compatible controller : Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07) (prog-if 00 [VGA controller])
Audio device : Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
```

xvinfo says
```
flynn@limetka:~/Zabava/Filmy$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
flynn@limetka:~/Zabava/Filmy$
```

any ideas?

thanks

---

