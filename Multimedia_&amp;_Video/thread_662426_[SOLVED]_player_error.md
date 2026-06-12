---
title: "[SOLVED] player error?"
date: 2008-01-08
forum: Multimedia &amp; Video
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

### Post by buccaneere on 2008-01-09
This is what is return**ing** on the command line, when I execute the first option that I described in the first post.

I copied only the 'return' from until the video is playing - last 8 lines.

The solution to the second option described in post 1, is in the 'return', before that...

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
A:22693.0 V:22693.3 A-V: -0.302 ct: -0.355 112/102 15%  2%  3.4% 3 0 
[/HTML]

---

### Post by buccaneere on 2008-01-10
Any takers???

---

### Post by manimal347 on 2008-01-10
I thought I had a solution (You probably know how MPlayer likes to default to incorrect video out devices upon installation), but after looking over your terminal log (thanks for posting that!), you ARE using the normal "xv" driver, and the video DOES appear to be decoding. Judging by your very sage sigline, I sense you've already RTFM's and STFW to death, so I'm really not sure what to suggest. Perhaps check Launchpad if you haven't already? You're running Edgy, though, so I'd think (hope?) fatal bugs would have been patched by now, if they exist. Does the MPlayer mailing list offer any support for Ubuntu-maintained packages? Sorry I can't be of more help.

------
An  MPlayer sidenote....

 I see you're running MPlayer with Alsa. MPlayer runs better, and is slightly faster too, in OSS mode. You'll need the "oss-compat" package for this.

---

### Post by buccaneere on 2008-01-10
> **manimal347 said:**
> I thought I had a solution (You probably know how MPlayer likes to default to incorrect video out devices upon installation), but after looking over your terminal log (thanks for posting that!), you ARE using the normal "xv" driver, and the video DOES appear to be decoding. Judging by your very sage sigline, I sense you've already RTFM's and STFW to death, so I'm really not sure what to suggest. Perhaps check Launchpad if you haven't already? You're running Edgy, though, so I'd think (hope?) fatal bugs would have been patched by now, if they exist. Does the MPlayer mailing list offer any support for Ubuntu-maintained packages? Sorry I can't be of more help.

------
An  MPlayer sidenote....

 I see you're running MPlayer with Alsa. MPlayer runs better, and is slightly faster too, in OSS mode. You'll need the "oss-compat" package for this.

Yeah - thanks for takin' a look there manimal.

I'm still too newb to know if it's a bug, or if it's a simple setting that I'm missin', although I'm believin' it's the latter.

...OR...

maybe even a package that didn't load by default... That's a lead - gotta' read some more...




EDIT: I think you have helped here manimal. As I think on that (see the smoke:lolflag:), I'm feelin' more sure that's what it is - a not-yet-loaded package, that starts the console when the CLI is used to start the app!!! How do I find this out???

Again...

CLI launch starts the player window, and the file, but not the console. 

GUI launch starts both player window, and control console window, but can't be used to start the file...

I addressed that without even realizing it - I tried (dumb me): [HTML]MPlayer [COLOR="Red"]Movie Player[/COLOR] xxx xxx xxx[/HTML] instead of: [HTML]MPlayer xxx xxx xxx[/HTML] ...which of course didn't work:rolleyes:

Cross yer' fingers.* And yer eyes, yer legs, yer hair, yer teeth!!!!!* Will get back.........................................

---

### Post by buccaneere on 2008-01-11
> **buccaneere said:**
> Yeah - thanks for takin' a look there manimal.

I'm still too newb to know if it's a bug, or if it's a simple setting that I'm missin', although I'm believin' it's the latter.

...OR...

maybe even a package that didn't load by default... That's a lead - gotta' read some more...




EDIT: I think you have helped here manimal. As I think on that (see the smoke:lolflag:), I'm feelin' more sure that's what it is - a not-yet-loaded package, that starts the console when the CLI is used to start the app!!! How do I find this out???

Again...

CLI launch starts the player window, and the file, but not the console. 

GUI launch starts both player window, and control console window, but can't be used to start the file...

I addressed that without even realizing it - I tried (dumb me): [HTML]MPlayer [COLOR="Red"]Movie Player[/COLOR] xxx xxx xxx[/HTML] instead of: [HTML]MPlayer xxx xxx xxx[/HTML] ...which of course didn't work:rolleyes:

Cross yer' fingers.* And yer eyes, yer legs, yer hair, yer teeth!!!!!* Will get back.........................................

Again...

CLI launch starts the player window, and the file, but not the console. 

GUI launch starts both player window, and control console window, but can't be used to start the file...

How do I get the control console AND the movie?

---

### Post by buccaneere on 2008-01-12
> **buccaneere said:**
> Again...

CLI launch starts the player window, and the file, but not the console. 

GUI launch starts both player window, and control console window, but can't be used to start the file...

How do I get the control console AND the movie?

Again...

CLI launch starts the player window, and the file, but not the console.

GUI launch starts both player window, and control console window, but can't be used to start the file...

How do I get the control console AND the movie?

---

