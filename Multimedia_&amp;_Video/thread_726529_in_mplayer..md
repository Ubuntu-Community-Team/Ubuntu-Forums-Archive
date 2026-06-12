---
title: "*** in mplayer."
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by ferrelas on 2008-03-16
Edit: 4ss == a s s ; as in the sub-fotmat (damn censor)

I've installed mplayer using sudo apt-get install mplayer (or whatever). When I use the -4ss option for playing a .mkv-file with 4ss-subtitles, mplayer dies with this message as soon as it tries to render any subs:

```
MPlayer interrupted by signal 11 in module: decode_video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

What should I do to get it to work?

---

### Post by yabbadabbadont on 2008-03-16
Check for an existing bug at launchpad.net.  If you find one, add your information to it.  If there isn't one, create one.  :)

You might also search the mplayer mailing list archives to see if anyone else is having the same issue.

---

### Post by shirilover on 2008-03-16
You should also use the -embeddedfonts switch when viewing stylized subtitles.

---

### Post by ferrelas on 2008-03-17
> **yabbadabbadont said:**
> Check for an existing bug at launchpad.net.  If you find one, add your information to it.  If there isn't one, create one.  :)

You might also search the mplayer mailing list archives to see if anyone else is having the same issue.

How should I create a bug report? And also, isn't there a possibility that it might be something other than mplayer that is causing the problem?


I know that I should run 4ss in conjunction with embeddedfonts, but it doesn't change anything and is kinda pointless since mplayer crashes on sub rendering anyway.

---

