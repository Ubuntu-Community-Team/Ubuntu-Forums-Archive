---
title: "Mplayer-vaapi on E-350 APU problems"
date: 2011-10-16
forum: Multimedia Software
---

### Post by the_X_files on 2011-10-16
I've been trying to get the hardware acceleration on my new ASROCK E350M1 motherboard all day without any luck. I am usuing Ubuntu 11.10 64 bit version. I installed libva1_0.32.0-1+sds2_amd64.deb, libva-dev_0.32.0-1+sds2_amd64.deb, xvba-video_0.8.0-1_amd64.deb and compiled successfully mplayer-vaapi from splitted-desktop.com. 

fglrxinfo output:
```
display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6300 series Graphics
OpenGL version string: 4.1.11079 Compatibility Profile Context

```

vainfo output:
```
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

And when I try to play some mkv 1080p file I get the following error:
```
./mplayer -vo vaapi -va vaapi /media/path.mkv 
MPlayer SVN-r32819-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/path.mkv.
libavformat file format detected.
[matroska,webm @ 0x1c77560] Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0, Zookeeper.2011
[lavf] stream 1: audio (dca), -aid 0, -alang eng, DTS-CORE 1536K
VIDEO:  [H264]  1920x800  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in /media/path/
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0


MPlayer interrupted by signal 11 in module: preinit_libvo
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

Any ideas? ](*,)

Edit: I fixed it!!!
If someone experience the same problem -> [https://bugs.launchpad.net/libva/+bug/800022](https://bugs.launchpad.net/libva/+bug/800022)

---

