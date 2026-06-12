---
title: "MPlayer won't play dvdnav://"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by nakko on 2007-01-15
I am able to run ```
mplayer dvd://
``` and get the somewhat desirable result of watching the main title of a DVD disc. I cannot watch any other titles, I can't get to the DVD menu! The same problem exists for VLC as well.

```

nakko@n64:~$ mplayer -v dvdnav://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/nakko/.mplayer/codecs.conf'
Reading /home/nakko/.mplayer/codecs.conf: Can't open '/home/nakko/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' 'dvdnav://'
init_freetype
get_path('font/font.desc') -> '/home/nakko/.mplayer/font/font.desc'
font: can't open file: /home/nakko/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/nakko/.mplayer/input.conf'
Can't open input config file /home/nakko/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 60 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('.conf') -> '/home/nakko/.mplayer/.conf'

Playing dvdnav://.
get_path('sub/') -> '/home/nakko/.mplayer/sub/'
[file] No filename
Failed to open dvdnav://.

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)
nakko@n64:~$

```

Here's what VLC tells me:```
nakko@n64:~$ vlc
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: FERGULLY_16X9_1
libdvdnav: DVD Serial Number: 2B87784C
libdvdnav: DVD Title (Alternative): FERGULLY_16X9_1
libdvdnav: Unable to find map file '/home/nakko/.dvdnav/FERGULLY_16X9_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000475
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000619
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000154c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000016f0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00001721
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000060c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x001c2609
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001c27ad
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x001e93c3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x001e9567
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
Segmentation fault (core dumped)
nakko@n64:~$ 

```

Any idea why I can play DVD video, but not from the main DVD menu? I didn't have this problem in Dapper, but now I am running Edgy AMD64.

---

### Post by el-sio on 2007-01-15
Hi ! 
I have the same problems with VLC (reading files but menus unaccessible), but gxine reads DVDs without problems !

Have you tried easyubuntu ? It's a GUI that helps you install all the needed codecs and applications to read non free formats.

You should also try this tutorial [http://ubuntu-tutorials.com/2006/12/14/how-to-enable-dvd-playback-ubuntu-510-6061-610/]("http://ubuntu-tutorials.com/2006/12/14/how-to-enable-dvd-playback-ubuntu-510-6061-610/")

good luck...

---

### Post by imon9 on 2007-01-15
not sure if this helps, but as i have read from mplayer documentation, release of new mplayer might or might not incoporate dvdnav://... so u can use dvd:// instead

however, if u just type dvd:// it will automatically play the first track, which in many case is something else other then menu or movie itself...(eg: some advertisement)

so what u can do is to specify which track to play

do it by typing dvd://1 
that means play track 1

dvd://2 
that means play track 2 ...and so on

what i don't get to do, is to choose language track :(
but there are also option to choose sound channel
u can read those in the documentation

hope this help...tell me if it does :)

---

