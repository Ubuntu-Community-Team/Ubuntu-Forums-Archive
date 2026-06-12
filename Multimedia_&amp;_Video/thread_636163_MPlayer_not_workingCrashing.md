---
title: "MPlayer not working/Crashing"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by KeeperOS on 2007-12-09
Have 7.10 Gutsy. Ran this several times from a LiveCD just to be sure.

First I add the Universe/Multiverse repositories and install mplayer.

I try to run gmplayer to play a matroska video file and get a video error.
It says that there is no XVideo support for my video card (ATI x1950 Pro, using the default ubuntu drivers, not the restricted ones).

> Playing /XXXFile.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "*File Title*", -vid 0
[mkv] Track ID 2: audio (A_AC3) "Japanese Audio (5.1ch Dolby Digital (AC3))", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***) "English Subs (***)", -sid 0, -slang eng
[mkv] Will play video track 1
Matroska file format detected.
VIDEO:  [avc1]  704x480  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)
ubuntu@ubuntu:~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
Then I add the medibuntu repositories and install the w32codecs and libdvdcss2 packages.

After that the error message is the following:
> MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (Family: 15, Model: 67, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
*** glibc detected *** gmplayer: munmap_chunk(): invalid pointer: 0x089d3390 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb6a0b92b]
gmplayer(gconvert_uri_to_filename+0x127)[0x811b027]
======= Memory map: ========
08048000-0885d000 r-xp 00000000 00:12 28550      /cow/usr/bin/mplayer
0885d000-088c6000 rw-p 00815000 00:12 28550      /cow/usr/bin/mplayer
088c6000-08a94000 rw-p 088c6000 00:00 0          [heap]
b60ca000-b60db000 r--p 00000000 07:00 35467      /rofs/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
b60db000-b619c000 rw-p b60db000 00:00 0 
b6212000-b623d000 rw-s 00000000 00:09 983054     /SYSV00000000 (deleted)
b623d000-b62a6000 rw-s 00000000 00:09 950285     /SYSV00000000 (deleted)
b62a6000-b633a000 rw-p b62a6000 00:00 0 
b633b000-b6367000 rw-p b633b000 00:00 0 
b6367000-b63c7000 rw-s 00000000 00:09 884748     /SYSV00000000 (deleted)
b63c7000-b63d9000 r-xp 00000000 07:00 80114      /rofs/usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b63d9000-b63da000 rw-p 00011000 07:00 80114      /rofs/usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b63da000-b63e3000 r-xp 00000000 07:00 101193     /rofs/lib/tls/i686/cmov/libnss_files-2.6.1.so
b63e3000-b63e5000 rw-p 00008000 07:00 101193     /rofs/lib/tls/i686/cmov/libnss_files-2.6.1.so
b63e5000-b63ed000 r-xp 00000000 07:00 101196     /rofs/lib/tls/i686/cmov/libnss_nis-2.6.1.so
b63ed000-b63ef000 rw-p 00007000 07:00 101196     /rofs/lib/tls/i686/cmov/libnss_nis-2.6.1.so
b63ef000-b63f6000 r-xp 00000000 07:00 101187     /rofs/lib/tls/i686/cmov/libnss_compat-2.6.1.so
b63f6000-b63f8000 rw-p 00006000 07:00 101187     /rofs/lib/tls/i686/cmov/libnss_compat-2.6.1.so
b63f8000-b63f9000 rw-p b63f8000 00:00 0 
b63f9000-b63ff000 r-xp 00000000 07:00 80089      /rofs/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b63ff000-b6400000 rw-p 00005000 07:00 80089      /rofs/usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b6400000-b6401000 r-xp 00000000 07:00 78567      /rofs/usr/lib/gconv/ISO8859-1.so
b6401000-b6403000 rw-p 00000000 07:00 78567      /rofs/usr/lib/gconv/ISO8859-1.so
b6403000-b6404000 r--p 00000000 07:00 75426      /rofs/usr/lib/locale/en_US.utf8/LC_NUMERIC
b6404000-b6405000 r--p 00000000 07:00 75496      /rofs/usr/lib/locale/en_US.utf8/LC_TIME
b6405000-b64e5000 r--p 00000000 07:00 75428      /rofs/usr/lib/locale/en_US.utf8/LC_COLLATE
b64e5000-b64e6000 r--p 00000000 07:00 75497      /rofs/usr/lib/locale/en_US.utf8/LC_MONETARY
b64e6000-b64e7000 r--p 00000000 07:00 75430      /rofs/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b64e7000-b64e8000 r--p 00000000 07:00 75447      /rofs/usr/lib/locale/en_US.utf8/LC_PAPER
b64e8000-b64e9000 r--p 00000000 07:00 75460      /rofs/usr/lib/locale/en_US.utf8/LC_NAME
b64e9000-b64ea000 r--p 00000000 07:00 75498      /rofs/usr/lib/locale/en_US.utf8/LC_ADDRESS
b64ea000-b6529000 r--p 00000000 07:00 75425      /rofs/usr/lib/locale/en_US.utf8/LC_CTYPE
b6529000-b652e000 rw-p b6529000 00:00 0 
b652e000-b657d000 r-xp 00000000 07:00 79536      /rofs/usr/lib/libgcrypt.so.11.2.3
b657d000-b657f000 rw-p 0004e000 07:00 79536      /rofs/usr/lib/libgcrypt.so.11.2.3
b657f000-b6582000 r-xp 00000000 07:00 79548      /rofs/usr/lib/libgpg-error.so.0.3.0
b6582000-b6583000 rw-p 00002000 07:00 79548      /rofs/usr/lib/libgpg-error.so.0.3.0
b6583000-b6592000 r-xp 00000000 07:00 79655      /rofs/usr/lib/libtasn1.so.3.0.9
b6592000-b6593000 rw-p 0000e000 07:00 79655      /rofs/usr/lib/libtasn1.so.3.0.9
b6593000-b6594000 rw-p b6593000 00:00 0 
b6594000-b65fe000 r-xp 00000000 07:00 79542      /rofs/usr/lib/libgnutls.so.13.3.0
b65fe000-b6604000 rw-p 0006a000 07:00 79542      /rofs/usr/lib/libgnutls.so.13.3.0
b6604000-b661a000 r-xp 00000000 07:00 79620      /rofs/usr/lib/libsasl2.so.2.0.22
b661a000-b661b000 rw-p 00015000 07:00 79620      /rofs/usr/lib/libsasl2.so.2.0.22
b661b000-b661c000 r-xp 00000000 07:00 101239     /rofs/lib/libkeyutils-1.2.so
b661c000-b661d000 rw-p 00001000 07:00 101239     /rofs/lib/libkeyutils-1.2.so
b661d000-b6624000 r-xp 00000000 07:00 79593      /ro

MPlayer interrupted by signal 6 in module: unknown
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.Any ideas?

BTW, I'm trying to run a matroska file that has H.264 video, AAC 5.1 audio and A-SS styled (font and color) subtitles (A-SS is also what gets censored above at the first output quote).

Thanks!

---

### Post by shirilover on 2007-12-09
Try using -vo gl2 or after running gmplayer, open the preferences and select gl2 from the Video tab.

---

### Post by KeeperOS on 2007-12-10
Well, you were correct. Using gl2 it did work, but at an inconceivable performance hit. I have an Athlon 64 X2 6000 MHz and 2GB of DDR2 800 and I STILL could not play it full screen!!!

I mean, come on, I have a relatively powerful card.
However under Device Manager it states:
> Device: RV570 [Radeon X1950 Pro](meaning, it does recognize it)
BUT under Device Type AND Capabilities it simply says "Unknown"...

What CAN I do anyway?

---

### Post by erginemr on 2007-12-11
Hello there,

The following two threads describe the same problem:

[http://ubuntuforums.org/showthread.php?t=356128](http://ubuntuforums.org/showthread.php?t=356128)

[http://ubuntuforums.org/archive/index.php/t-220757.html](http://ubuntuforums.org/archive/index.php/t-220757.html)

In the light of the above threads, I can propose you to do the following:

1. First please check out that your ATI driver has been enabled in your "/etc/X11/xorg.conf" file. 

There should be a line that says: 
```
...
Driver "fglrx"
...
```


2. You can also check if you are using your graphics card to the full extent, with the following command from the console:
```
glxinfo | grep rendering
```


If it says something like "Direct Rendering: No", then it means the 3D capabilities of your card is not used.

3. Finally, please try the solution proposed in one of the above threads:

```
sudo aticonfig --overlay-type=Xv
```

which, supposedly, should resolve this issue.

Good Luck.

---

