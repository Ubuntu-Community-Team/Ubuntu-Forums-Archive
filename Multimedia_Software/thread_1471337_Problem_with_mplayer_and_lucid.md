---
title: "Problem with mplayer and lucid"
date: 2010-05-03
forum: Multimedia Software
---

### Post by dave.lawrence on 2010-05-03
I upgraded to lucid this weekend and all seems good apart from video playback with mplayer.  vlc and ffplay are faultless, but mplayer stutters and pops and fizzles for a few seconds, showing VERY broken video and then drops back to command line.  During it's brief life it seems to show a whole raft of attempted key presses, many are control sequences.  Complete stdout/stderr dump below.

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
fglrx 2:8.723.1-0ubuntu3

Any ideas greatfully received!

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test1.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  528x300  24bpp  25.000 fps  1472.4 kbps (179.7 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 528 x 300 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.76:1 - prescaling to correct movie aspect.
VO: [xv] 528x300 => 528x300 Planar YV12 
A:   0.1 V:   0.0 A-V:  0.099 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 ^[[J^MNo bind found for key 'C'.                         
A:   0.2 V:   0.0 A-V:  0.129 ct:  0.004   2/  2 ??% ??% ??,?% 0 0 ^[[J^MNo bind found for key '^L'.                         
A:   0.2 V:   0.1 A-V:  0.090 ct:  0.008   3/  3 ??% ??% ??,?% 0 0 ^[[J^MNo bind found for key '^N'.                         
A:   0.2 V:   0.1 A-V:  0.060 ct:  0.012   4/  4 ??% ??% ??,?% 0 0 ^[[J^MNo bind found for key 'N'.                         
No bind found for key '='.                         
A:   0.2 V:   0.2 A-V:  0.056 ct:  0.016   5/  5 ??% ??% ??,?% 0 0 ^[[J^MA:   0.6 V:   0.2 A-V:  0.382 ct:  0.020   6/  6 ??% ??% ??,?% 0 0 ^[[J^MNo bind found for key '^F'.                         
A:   0.6 V:   0.2 A-V:  0.343 ct:  0.024   7/  7 ??% ??% ??,?% 0 0 ^[[J^MNo bind found for key 'c'.                         
A:   0.6 V:   0.3 A-V:  0.313 ct:  0.028   8/  8 ??% ??% ??,?% 0 0 ^[[J^MA:   0.6 V:   0.3 A-V:  0.295 ct:  0.032   9/  9 ??% ??% ??,?% 0 0 ^[[J^M
  =====  PAUSE  =====^MNo bind found for key '^Z'.                         
Failed to increment property 'switch_program' by 0.000000.
No bind found for key '^\'.                         
No bind found for key '='.                         
big_values too large!
big_values too large!
Blocktype == 0 and window-switching == 1 not allowed.
big_values too large!
big_values too large!
big_values too large!
big_values too large!
mpg123: Can't rewind stream by 1026 bits!

Badly interleaved AVI file detected - switching to -ni mode...
A: 164.1 V:   0.4 A-V:163.739 ct:  0.036  10/ 10 ??% ??% ??,?% 1 0 0.91x ^[[J^M

Exiting... (End of file)

---

