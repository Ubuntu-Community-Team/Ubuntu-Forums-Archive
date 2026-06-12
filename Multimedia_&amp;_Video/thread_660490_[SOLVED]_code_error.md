---
title: "[SOLVED] code error?"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by buccaneere on 2008-01-06
[HTML]Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv>        select video output driver ('-vo help' for a list)
 -ao <drv>        select audio output driver ('-ao help' for a list)
 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>  play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <position>   seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)[/HTML]


[HTML]chuckacer@chuckb-laptop:~$ mplayer -fs /home/chuckb/Desktop/moviescp HaM.tsp

MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Turion(tm) 64 Mobile Technology MK-36 (Family: 15, Model: 76, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/chuckb/Desktop/moviescp.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Seek failed


Playing HaM.tsp.
File not found: 'HaM.tsp'
Failed to open HaM.tsp.


Exiting... (End of file)[/HTML]

I can get the file to play, without the control console, through GUI (a bug?)

From CLI, I get the above return...

Help?

---

### Post by yabbadabbadont on 2008-01-06
```
mplayer -fs "/home/chuckb/Desktop/moviescp HaM.tsp"
```
or
```
mplayer -fs /home/chuckb/Desktop/moviescp\ HaM.tsp
```
:D

---

### Post by buccaneere on 2008-01-06
> **yabbadabbadont said:**
> ```
mplayer -fs "/home/chuckb/Desktop/moviescp HaM.tsp"
```
or
```
mplayer -fs /home/chuckb/Desktop/moviescp\ HaM.tsp
```
:D

YUP!
I just figured it out - syntax error.

I went with mplayer -fs /home/chuckb/Desktop/moviescp/HaM.tsp

Good call yabbs.......

---

### Post by buccaneere on 2008-01-08
Still a problem here...

[HTML]mplayer -fs /home/chuckb/Desktop/moviescp/HaM.tsp[/HTML]

This command opens a file in the 'play' window, but without the control console. Rt click in the screen gives no options. A dead end.



But...

When I open MPlayer from Apps/sound and video, I get the two MPlayer windows (screen, and control console), but open a file/browse lists only 'supported' files. 

If I click 'all files', it lists the video files. When I highlight and click 'open', it returns 'Error opening/initializing the selected video_ out (-vo) device. Another dead end.

Help?

---

### Post by yabbadabbadont on 2008-01-09
What kind of file is it?

You might try installing transcode and then running:
```
tcprobe -i /home/chuckb/Desktop/moviescp/HaM.tsp
```
to see if it can be identified.  If nothing else, it may print out some useful error messages.

---

### Post by buccaneere on 2008-01-10
> **yabbadabbadont said:**
> What kind of file is it?

You might try installing transcode and then running:
```
tcprobe -i /home/chuckb/Desktop/moviescp/HaM.tsp
```
to see if it can be identified.  If nothing else, it may print out some useful error messages.

It's a video - MPEG2. Rips as .tsp from 'dishreceiver'. I'll give transcode a try. I'm sure I'm missin' somethin' simpler than that tho'...

---

### Post by yabbadabbadont on 2008-01-10
It is probably encrypted or has some other form of DRM attached.

---

### Post by buccaneere on 2008-01-10
> **yabbadabbadont said:**
> It is probably encrypted or has some other form of DRM attached.

Hi Yabba...

Manimal347 said somthin' that made me start thinkin' (*it hurts too*:lolflag:)......

Again, in summation...

GUI launch starts both windows of the player, but the file won't open that way...

CLI launch starts only the file, with out the control window (console).

That's what a bug is. Right?

---

### Post by yabbadabbadont on 2008-01-10
No.  That is the normal behavior for mplayer.  GUI -> two windows, CLI -> video window only.  mplayer's inability to play the file means that either the file is encrypted/protected in some way, or you do not have the proper codecs installed in order to decode that format.  That is why I suggested tcprobe.  It is a means of trying to determine if it is just a missing codec (which can probably be fixed), or encryption/DRM (which probably can't).

---

### Post by buccaneere on 2008-01-10
HTML Code:

mplayer -fs /home/chuckb/Desktop/moviescp/HaM.tsp

This command **opens a file in the 'play' window**, but without the control console. Rt click in the screen gives no options. A dead end.


I'm not understanding why CLI execution plays the file, but not GUI...........

---

### Post by buccaneere on 2008-01-10
This is the terminal log from CLI execution, and playing the file (cut off at last four lines of file beginning to play)

[HTML]chucknb@chucknb-desktop:~$ mplayer -fs /media/D/HaM.tsp
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/D/HaM.tsp.
TS file format detected.
VIDEO MPEG2(pid=6946) AUDIO MPA(pid=6947) NO SUBS (yet)!  PROGRAM N. 0
VIDEO:  MPEG2  544x480  (aspect 2)  29.970 fps  15000.0 kbps (1875.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 544 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 20000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 544 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 544x480 => 640x480 Planar YV12  [fs]
A:22689.1 V:22689.9 A-V: -0.773 ct: -0.030  12/ 10 ??% ??% ??,?% 3 0 
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
A:22689.4 V:22690.2 A-V: -0.719 ct: -0.058  20/ 17 41%  7%  4.2% 3 0 
demux_mpg: 30000/1001fps NTSC content detected, switching framerate.
Warning! FPS changed 23.976 -> 29.970  (-5.994005) [4]  7%  4.2% 3 0 
A:22692.3 V:22692.7 A-V: -0.449 ct: -0.297  97/ 88 16%  3%  3.4% 3 0 
demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
A:22693.0 V:22693.3 A-V: -0.302 ct: -0.355 112/102 15%  2%  3.4% 3 0 [/HTML]

---

### Post by buccaneere on 2008-01-11
> **buccaneere said:**
> HTML Code:

mplayer -fs /home/chuckb/Desktop/moviescp/HaM.tsp

This command **opens a file in the 'play' window**, but without the control console. Rt click in the screen gives no options. A dead end.


I'm not understanding why CLI execution plays the file, but not GUI...........

bumpin here.......

---

### Post by buccaneere on 2008-01-12
mplayer -fs /home/chuckb/Desktop/moviescp/HaM.tsp

This command opens a file in the 'play' window, but without the control console. Rt click in the screen gives no options. A dead end.


I'm not understanding why CLI execution plays the file, but not GUI...........

Anybody???

---

