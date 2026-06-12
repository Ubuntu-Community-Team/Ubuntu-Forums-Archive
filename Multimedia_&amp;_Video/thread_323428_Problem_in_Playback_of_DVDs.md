---
title: "Problem in Playback of DVDs"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by Canis familiaris on 2006-12-22
Hi there,
Whenever I try to playback a DVD by gxine, mplayer, vlc in Ubuntu (both in GNOME and KDE), the program terminates unexpectedly. In Kaffeine the DVD plays but I could only hear the audio, the video is ](*,) mismatched and and random colours appear.
The MP3, and VCD playback is fine.

In fact when I run gxine in terminal and play dvd I receive the following error after termination:

l> irc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
libdvdnav: Using dvdnav version 1.1.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: 600 anni Universit  Torino
libdvdnav: DVD Serial Number: 2F668E01
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/anurag/.dvdnav/600 anni Universit&#65533;Torino.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000018b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000fcd2
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 463 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Please help[-(

---

### Post by darrenm on 2006-12-22
Hello

What graphics card are you using?

---

### Post by Canis familiaris on 2006-12-22
It is SIS 620 in a Pentium III with 256 MB of RAM.

---

### Post by darrenm on 2006-12-22
Ah, sorry I don't have much experience of SIS in Linux.

I'm sure the problem is to do with the video card. You could try changing the shared memory size in the BIOS?

---

### Post by Canis familiaris on 2006-12-22
Yes, you are spot on the fact that it is a video card problem. 
Increasing my shared memory atleast prevent crashing of vlc, gxine, etc. However the video output is churpy and random lines appear.
My Problem was solved by using[ GeeXBox ]("http://geexbox.org/") Linux OS
It plays DVD even in my OC perfectly.
Thanks Anyways

---

### Post by darrenm on 2006-12-22
I would check which X driver Geexbox is using then compare to Ubuntu's.

It may be using the wrong X driver, you could do a dpk-reconfigure xserver-xorg to change it.

---

### Post by Canis familiaris on 2006-12-22
The driver Ubuntu detects is all right.
In fact when I used to use Windows, the same problem was there of choppy video barring the additional pink bar which appears while playing now in Ubuntu. In fact sometimes the DVD (1 out of 50 chance),  plays the DVD :confused: but only with an inferior frames per second and choppy sound -> same problem I used to have in Windows XP.
Probably my RAM modules are incompatible with my PC. (When I use Windows XP I can see few weird dots and even games do not run especially after my PC underwent a RAM upgrade):-k 
I think GeeXBox, plays it well due to dedicated resources for Multimedia.

---

