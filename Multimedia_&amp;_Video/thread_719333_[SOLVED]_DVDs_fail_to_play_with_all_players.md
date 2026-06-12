---
title: "[SOLVED] DVDs fail to play with all players"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by HolyRunner on 2008-03-09
I can't get DVD playback to work at all on two of my machines.  One is running Ubuntu 7.10 and the other Mythbuntu.  I've tried mplayer, VLC, and totem; all fail to play DVDs.

Here is what mplayer spits out.
mplayer
```
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
libdvdread: Invalid IFO for VMGM (VIDEO_TS.BUP).
Can't open VMG info!
File not found: '1'
Failed to open dvd://1.

Exiting... (End of file)

```

This would make you think the dvd isn't being mounted properly but the DVD appears on my desktop and I can browse /media/cdrom0
```
holyrunner@Refined:/media/cdrom0$ ls
AUDIO_TS  JACKET_P  VIDEO_TS

```

And /dev/dvd points to the correct place
```
holyrunner@Refined:/$ ls -l /dev/dvd
lrwxrwxrwx 1 root root 3 2008-03-09 03:16 /dev/dvd -> hda
holyrunner@Refined:/$ ls -l /dev/hda
brw-rw---- 1 root cdrom 3, 0 2008-03-08 22:16 /dev/hda

```

Both computers read/write/play DVDs fine in Windows.  I don't know what else to try.  Any ideas?

Burner is NEC ND-3550A and gets reported as _NEC DVD_RW ND-3550A

---

### Post by xc3RnbFO8P on 2008-03-09
Try to install this, in **terminal**:

> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by HolyRunner on 2008-03-09
That worked! Thanks Ringi.  I had already added the Medibuntu repository to my sources.list, guess I didn't have everything I needed installed.

---

### Post by xc3RnbFO8P on 2008-03-09
Mark it as solved :)

---

