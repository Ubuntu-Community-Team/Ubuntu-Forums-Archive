---
title: "My Movie wont play in any movie player!"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by jrmink on 2007-09-26
Seriously...All these programs not working and messing up is starting to bother me.  ANYWAYS.....

I am trying to play the following movie file

Type AVI Video

Size 349.7 MB

MIME type video/x-msvideo

When I load it up with Totem Movie player and xine both freeze

and when I run mplayer with it I get a fatal error about wideo output.  My nvidia driver is installed I dont know why NONE of my video players are working.  I am mad that I cant watch prison break.  Please someone help me.

---

### Post by Jose Catre-Vandis on 2007-09-26
Um, you have installed all the video codecs, w32codecs etc? If not search for restricted formats installation.

If so, try opening gmplayer (which is the gui version of Mplayer, listed as Mplayer Movie Player under Sound andVideo), right click on the window, choose preferences, choose video tab, and select xv, click OK, and try movie in either mplayer or gmplayer. Work now?

---

### Post by jrmink on 2007-09-26
Now the gmplayer doesnt even load.  At times like this you just want a working movie player...

I have to go to system monitor to shut them down.

---

### Post by rsambuca on 2007-09-26
I think you have bigger problems with your installation than the video playing.  These types of freezes shouldn't be happening.  I would suggest starting one of the  players from a terminal so that you can see any error messages.

---

### Post by jrmink on 2007-09-26
This is when I try to run gmplayer

> larry@larry-desktop:~$ gmplayer
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 1800MHz (Family: 15, Model: 0, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/larry/Downloads/Prison Break S03E02 Season 3 Episode 2 HDTV XviD.avi.
AVI file format detected.
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  986.2 kbps (120.4 kbyte/s)
Xv: could not grab port 158
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
Also my gmplayer CRASHED too.  Still these thing are driving me nuts.  Im out of blank cds so I cant burn a new install cd either. Dangit.

When I run gxine nothing happens at all and I mean nothing.  Yes when I run gxine in the terminal nothing happens.  Wierd huh?


I also get this when trying to run my movie through the command line with mplayer

> Playing /home/larry/Downloads/prisonbreak_3_2.avi.
AVI file format detected.
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  986.2 kbps (120.4 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Xv: could not grab port 158
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================

Im guessing and note I AM GUESSING as I am new to ubuntu, but would removing all of my movie programs and then reinstalling help?  How would I even go about that?

I guess the easiestttt thing to do would be to burn a new live ubuntu cd but I would rather not go look around for more blank cds forever.

---

### Post by jrmink on 2007-09-27
Resolved...kinda

Well since no one had a solution I installed xubuntu and I am going to test it out.  I am also going to revert back to ubuntu dapper drake because fiesty obviously is not stable and has too many bugs.

Cherio

---

