---
title: "VLC 1.0.2 won't play XVID files"
date: 2009-10-27
forum: Multimedia Software
---

### Post by prickee on 2009-10-27
Video file runs in Mplayer but my default player is VLC.


FYI

777@CoSmos:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for 777: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

777@CoSmos:~$ vlc /home/777/Downloads/XYZ.HDTV.XviD-FQM.avi
VLC media player 1.0.2 Goldeneye
[0x907e140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  103
  Current serial number in output stream:  104




Output from Mplayer through terminal:

AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1005.8 kbps (122.8 kbyte/s)
Clip info:
 Software: transcode-1.0.4
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
=========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 



Thanx

---

### Post by vinutux on 2009-10-27
Try this...in vlc > tools > preferences > Video > Output | Change output to X11 , if it failed try other options on that drop down menu.......

---

### Post by prickee on 2009-10-29
I tried that and VLC opens then closes/crashes...the previous edition of VLC worked fine so I guessing it's wise to go back to last edition hmmmm....

---

