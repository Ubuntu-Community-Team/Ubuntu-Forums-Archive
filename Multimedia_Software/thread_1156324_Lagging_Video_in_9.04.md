---
title: "Lagging Video in 9.04"
date: 2009-05-11
forum: Multimedia Software
---

### Post by ralewis on 2009-05-11
So this might have already been solved, but it's hard for me to search for because I'm not exactly why this problem is occurring.

So my Laptop is an Inspiron 2200 with an Intel integrated graphics card, running 9.04.

I've noticed recently that when I play flash videos in firefox, which run fine normally, and I do something to cause the notify-osd to pop up, or move my mouse over animated parts of a page (like the buttons on youtube), it causes the video part to lag, while the audio part remains fine.  In addition, the video tends to be laggy when I full screen it.

I attempted the same test with a video playing in VLC, but no lag occurred on the video portion.

I'm assuming this is a problem with the Flash player?  The strange part is, I don't remember having these lagging issues in previous versions of ubuntu.

---

### Post by concare on 2009-05-11
Hi, i have the same problem :(

---

### Post by psyke83 on 2009-05-12
Check out my guide. Your sluggishness is due to a combination of factors (regressions in driver's EXA acceleration code, and broken MTRR range setup).

Flash does not use XV output, so it is more CPU-intensive (which is why lagging is more noticeable in Flash compared to VLC, Totem, etc).

---

