---
title: "Unable to play encrypted DVDs"
date: 2009-09-27
forum: Multimedia Software
---

### Post by ajaygautam on 2009-09-27
Just installed ubuntu 9.04, running as a virtual box guest, on a mac os 10.6.1 host.

Followed instructions from:
[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

Cannot play any encrypted DVDs. Have tried with VLC, mplayer, xine, gstreamer

Error:
```
agautam@Komputor-Mac:~$ mplayer dvd://1
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8135  @ 2.66GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 7 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
*** Zero check failed in ifo_read.c:1361
    for vts_tmapt->zero_1 = 0x0001
libdvdread: Invalid title IFO (VTS_01_0.IFO).
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0

```

libdvdcss has been installed:
```

gautam@Komputor-Mac:~$ ls -l /usr/lib/libdvdcss*
lrwxrwxrwx 1 root root    18 2009-09-25 22:43 /usr/lib/libdvdcss.so.2 -> libdvdcss.so.2.1.0
-rw-r--r-- 1 root root 34028 2008-09-10 15:04 /usr/lib/libdvdcss.so.2.1.0

```

Any help / info / pointers / debug steps would be very helpful.

Thanks

Ajay

---

### Post by wilee-nilee on 2009-09-27
Did you go to Medibuntu for the package set, and the restricted extras set for your distribution in synaptic. Also Smplayer and vlc are good to install as well, these didn't work as you are missing some codecs.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

