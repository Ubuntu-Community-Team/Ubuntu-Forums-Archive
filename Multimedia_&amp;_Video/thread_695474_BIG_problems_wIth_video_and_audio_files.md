---
title: "BIG problems wIth video and audio files"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by nebu on 2008-02-13
I am having some problems with playing audio and video files in Ubuntu......

when i play the video in mplayer...... i get an error message of which i have attached a screenshot

when i play the video or audio in VLC/Totem..... the screen goes black and white and just stalls...... in vlc..... the movie continues to play but the window becomes in black and white....... i have attached screenshots of these....

Rhythmbox just closes every time i click on play

when i try to play the smae  video file with mplayer from the terminal..... it works just fine sometimes and does not worka at all other times!!!

here is what i get when it does not work.....

```
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.60GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Taare Zameen Par.divx.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  720x336  12bpp  23.976 fps  531.8 kbps (64.9 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 325.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 32000 Hz, 2 ch, s16le, 80.0 kbit/7.81% (ratio: 10000->128000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================

```

i really need help with this!!!:confused::confused::confused::(:(:(

---

### Post by luisromangz on 2008-02-13
The black and white effect may be because of compiz. When compiz thinks a certain window is frozen, because high cpu use, it desaturate its colors by default.

Maybe the other problems are compiz related too, you should try to play that files while compiz is not running.

---

### Post by nebu on 2008-02-13
tried it after urning compiz off...... i am getting the same problem......

---

### Post by nebu on 2008-02-13
bump.......



i have noticed that the mplayer works from the terminal mode when i run it before running any other software for playing videos...... but afterwards it does not work

---

### Post by nebu on 2008-02-19
bump...

---

