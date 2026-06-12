---
title: "Green Screen when playing under VLC, MPlayer, Totem"
date: 2011-02-20
forum: Multimedia Software
---

### Post by SleepWalkerX on 2011-02-20
Playing video gets me a green screen.  This appears to be an overlay problem (as if I try to take a screen shot then it looks fine).

If I play a video in VLC 1.1.4 (repo version) I get the green screen with default options.  If I go into the Preferences and uncheck "Accelerated Video Output (Overlay)" or manually specify X11 for my output module then it plays fine.  

However, this also occurs for MPlayer and Totem, which is annoying because I set electricsheep for my screensaver.  Its kinda odd because it just started occuring and I can't for the life of me remember what change I made.

I'm also running xorg-edgers so I'm grabbing the latest radeon driver.  However, I've been updating from xorg-edgers for a bit and haven't noticed a new update.  

I haven't been able to pinpoint this problem.

---

### Post by SleepWalkerX on 2011-02-20
Yeah it was an xorg-edgers update.  :(

---

