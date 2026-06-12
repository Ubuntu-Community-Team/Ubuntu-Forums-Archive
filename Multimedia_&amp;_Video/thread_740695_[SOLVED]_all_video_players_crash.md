---
title: "[SOLVED] all video players crash"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by scragar on 2008-03-31
I'm running gutsy on a 64 bit system with compiz disabled.

Whenever I try to play a video it always crashes(only exception appearing to be flash video, which plays fine), format is irrelevant(tested using mkv, mpg and avi). these are the outputs:

VLC```
scragar @ [06:56:37 on Mon Mar 31]
~/ $ vlc
VLC media player 0.8.6c Janus
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Value in failed request:  0x3c00006
  Serial number of failed request:  85
  Current serial number in output stream:  86
```
mplayer```
scragar @ [06:57:16 on Mon Mar 31]
~/ $ gmplayer
MPlayer 2:1.0~rc1-0ubuntu13.2+medibuntu1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing ///home/scragar/Desktop/file.avi.
AVI file format detected.
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1046.2 kbps (127.7 kbyte/s)
Clip info:
 Software: transcode-1.0.2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Xv: could not grab port 131
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
[ws] Error in display.  0.269 ct:  0.000   1/  1 ??% ??% ??,?% 0 0              
[ws]  Error code: 2 ( BadValue (integer parameter out of range for operation) )
[ws]  Request code: 140
[ws]  Minor code: 19
[ws]  Modules: flip_page
```
totem```
scragar @ [06:57:13 on Mon Mar 31]
~/ $ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 98 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

please help.

---

### Post by kayel_justice on 2008-03-31
I'm Having A problem too.......It seems avi files wont play with Visual Effects set to custom. When it's on normal it will play..

 Can anyone help?

Thanks

---

### Post by scragar on 2008-03-31
[http://ubuntuforums.org/showthread.php?t=612564](http://ubuntuforums.org/showthread.php?t=612564) <-- they discuss your problem there.

I DO NOT HAVE COMPIZ ENABLED AND STILL GET THIS PROBLEM.
sorry for the caps, but clearly the guy above missed it, despite the fact it was in my first sentence.

can anyone help?


EDIT: doesn't matter, fixed it by switching back to the default graphics instead of the envy one.

---

### Post by gloscherrybomb on 2008-05-12
This problem isn't solved! Does anybody have a proper fix for this? I have the identical issues as the orginial poster. Seems to be something to do with XV and the FGLRX driver. I have had it working, but not sure what has now stopped it working.

---

