---
title: "Almost have DVD playback working"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by kammat on 2007-05-20
I've been working on installing Ubuntu for a friend on an old laptop of hers, and I've gotten almost all the kinks worked out besides DVD playback.  I've installed all the needed files as advised by the sticky and a few other posts I found, but I keep running into one showstopper.

Hardware:  Gateway Solo 5150 laptop, with the Solo 5000 series DVD drive, Pentium 2 at 300 MHz, 128 MB RAM (soon to be upgraded), 30GB HD.  I also have a ZV-DVD PCMCIA card which supposedly has a hardware decoder available, but I have come up empty finding any drivers for it under linux.

As mentioned, followed the instructions in the multimedia support sticky, and also went over the instuctions in the user support wiki.  The drive recognises the DVD fine.  When gxine tries to play the movie, though, it gets ready to play it back, resizes the screen, then crashes out.  Invokes from the command line, I get the following:

```
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
libdvdnav: Using dvdnav version 1.1.4 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: ROOMATES
libdvdnav: DVD Serial Number: 2e5aa017
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/frarochvia/.dvdnav/ROOMATES.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000192
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000202
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000321
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002101da
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002101df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00210c50
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00210c55
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 742 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Does anyone have any ideas what I may have missed, or if I'll even be able to get the DVD player running?  Thanks!

---

