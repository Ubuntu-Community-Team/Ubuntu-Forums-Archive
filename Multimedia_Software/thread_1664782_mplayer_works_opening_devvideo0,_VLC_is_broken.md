---
title: "mplayer works opening /dev/video0, VLC is broken"
date: 2011-01-11
forum: Multimedia Software
---

### Post by sdowney717 on 2011-01-11
any ideas?, VLC used to work
it is an avc-2010 video capture card

mplayer here
```
scott@scott-desktop:~$ mplayer /dev/video0
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 224.0 kbit/14.58% (ratio: 28000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 720x540 Planar YV12 
[mpeg2video @ 0x144a760]warning: first frame is no keyframe
[VD_FFMPEG] DRI failure.
[mpeg2video @ 0x144a760]warning: first frame is no keyframe,?% 1 0 
A:  12.4 V:  12.4 A-V:  0.000 ct: -0.285 349/349  3%  7% 14.3% 7 0 
Exiting... (Quit)
scott@scott-desktop:~$ 

```

VLC here
```
scott@scott-desktop:~$ vlc /dev/video0
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8587914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb67fe0d4, 0xb67fe048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1294229741)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:14431): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:86: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/ubuntu-sunrise/gtk-2.0/gtkrc:90: Murrine configuration option "gradients" is no longer supported and will be ignored.
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
libdvdnav: Using dvdnav version 0.2.1cvs from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: Can't seek to block 32
libdvdnav: Unable to find map file '/home/scott/.dvdnav/.map'
libdvdread: UDFFindFile(/VIDEO_TS/VIDEO_TS.IFO)
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread: UDFFindFile(/VIDEO_TS/VIDEO_TS.BUP)
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[0x88be21c] main access error: Read error: Device or resource busy
[0x88be21c] filesystem access error: failed to read (Device or resource busy)
[0x88be3ec] main stream error: cannot pre fill buffer
scott@scott-desktop:~$ 

```

---

