---
title: "gmplayer suddenly taking long to start"
date: 2008-08-02
forum: Multimedia Software
---

### Post by dakal on 2008-08-02
All of a sudden (no, I really don't know what I might have done to cause it), gmplayer is taking a really long time to start. The console-based mplayer doesn't have the same problem, and enabling verbose output doesn't really provide a clue. It was just before the notices about no joystick or LIRC found, so I disabled those in ~/.mplayer/config since I don't have either anyway, but that didn't help.

~/.mplayer/config: ```
nojoystick=1
nolirc=1
```
```
MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 12, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1600x1200 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports layers.
[x11] Using workaround for Metacity bugs.
[x11] Detected wm supports NetWM.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Detected wm supports FULLSCREEN state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
(approximately 10 second pause here...)Adding filename <file> && pathname <path>
get_path('codecs.conf') -> '<home>/.mplayer/codecs.conf'
(continues normally and starts playback...)
```
Since I fairly regularly play media files one by one, this delay is seriously annoying. Any suggestions for what to try would be greatly appreciated.

---

### Post by dakal on 2008-08-02
Never mind. Whatever the issue was, it seems to have resolved itself.

---

### Post by arsenic23 on 2008-08-02
Just in case your curious, I had this same problem a while ago and it ended up being something to do with Gnome screensaver.  I forget what setting I had to tweak to fix it though.

---

### Post by mc4man on 2008-08-02
It's the 'stop xscreensaver' in preferences -> misc, if it's ck.ed a 10 sec. or so delay in opening.
doesn't affect smplayer if stop screensaver is ck.'ed in it's options

---

