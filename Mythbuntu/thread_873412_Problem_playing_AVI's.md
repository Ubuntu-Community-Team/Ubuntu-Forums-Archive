---
title: "Problem playing AVI's"
date: 2008-07-29
forum: Mythbuntu
---

### Post by rnelson0 on 2008-07-29
I have some files that SEEM to be AVI's, but I'm having a lot of trouble getting them to play.

Here are my results when I try to open it with some of the gui media players.

mplayer: stays blank, acts like its thinking, then "No Stream Found" dialog

VLC: the time bar scrolls along, but not video or audio

xine: Error dialog saying there is no demuxer plugin blah blah blah. something interesting in the trace... "video_out_xv: ignoring broken XV_HUE settings on NVidia cards.


When I try from the command line, this is what I get:

mplayer:

```

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing file.avi.
MPEG-ES file format detected.
parse_es: could not sync video stream!
parse_es: could not sync video stream!
Video: Cannot read properties.
No stream found.

```

vlc: window pops up. this is on the console:
```

[00000289] main playlist: nothing to play
[00000289] main playlist: stopping playback

```
xine: nada... just xine copyright info.

I've been pulling my hair out over this one. It seems no one else has a problem playing it.

Not only that, but this is on a fairly new Hardy Mythbuntu install. So I really haven't tweaked anything.

Any ideas?

---

### Post by Trollslayer on 2008-07-30
Have you tried Mplayer? If the stream isn't formatted correctled that copes better.

---

### Post by nasha on 2008-07-31
It seems to think that your so called avi is an mpeg stream file... Try a file that you know has a native avi format, and see if this eliminates the problem.
If it does, then is the video encoding of the file that is the issue.

---

### Post by nickrout on 2008-07-31
try ffmpeg -i FILENAME, which chould tell you what container and codecs are in it.

I have seen this, eg, on files that bittorrent hasn't actually finished downloading!

---

### Post by Ptero-4 on 2008-07-31
Can you check if you have all the restricted codecs, the mplayer error message seems to indicate something like that, also if you're using a NVidia check if your using xv in your players and compiz. xv, compiz and nvidia drivers doesn't mix together and in this case you need to either replace xv (search in the forums for info about this) or turn compiz off before using the players.

---

