---
title: "No more fullscreen in movie player?"
date: 2011-04-19
forum: Multimedia Software
---

### Post by *uu on 2011-04-19
Hello everyone,

today in the morning I upgraded several gstreamer related packages (I suspect from the [Gstreamer Developers PPA]("https://launchpad.net/~gstreamer-developers/+archive/ppa"); list and versions see below). Now I just noticed that in the Movie Player (Totem Movie Player 2.30.2 using GStreamer 0.10.32 (prerelease)), when viewing a video in full screen mode, the whole screen is filled with black as expected, but the video itself now remains at its original size in the center of the screen, it is not being resized to the size of the screen. This was not the case two days ago, and I suspect the gstreamer upgrade.

Does anyone have any pointers on this, before I file a bug report? As the Movie Player itself doesn't provide any further options on video scaling (yeah, what a nice GNOME philosophy...), there's not much I can do from within the GUI..

Anyone else experiencing this?

```
Upgraded the following packages:
gstreamer0.10-alsa (0.10.32-1~lucid1) to 0.10.32.2-1~lucid7
gstreamer0.10-plugins-bad (0.10.21-1~lucid1) to 0.10.21.2-1~lucid2
gstreamer0.10-plugins-base (0.10.32-1~lucid1) to 0.10.32.2-1~lucid7
gstreamer0.10-plugins-base-apps (0.10.32-1~lucid1) to 0.10.32.2-1~lucid7
gstreamer0.10-plugins-good (0.10.27-1~lucid2) to 0.10.28.2-1~lucid2
gstreamer0.10-plugins-ugly (0.10.17-1~lucid1) to 0.10.17.2-1~lucid2
gstreamer0.10-pulseaudio (0.10.27-1~lucid2) to 0.10.28.2-1~lucid2
gstreamer0.10-x (0.10.32-1~lucid1) to 0.10.32.2-1~lucid7
libgstreamer-plugins-base0.10-0 (0.10.32-1~lucid1) to 0.10.32.2-1~lucid7
```

---

### Post by *uu on 2011-05-03
This issue was magically "repaired" with the next update of some of the GStreamer related packages:

```
Upgraded the following packages:
gir1.0-gstreamer-0.10 (0.10.32.2-1~lucid2) to 0.10.32.3-1~lucid1
gstreamer-tools (0.10.32.2-1~lucid2) to 0.10.32.3-1~lucid1
gstreamer0.10-alsa (0.10.32.2-1~lucid7) to 0.10.32.3-1~lucid1
gstreamer0.10-plugins-base (0.10.32.2-1~lucid7) to 0.10.32.3-1~lucid1
gstreamer0.10-plugins-base-apps (0.10.32.2-1~lucid7) to 0.10.32.3-1~lucid1
gstreamer0.10-tools (0.10.32.2-1~lucid2) to 0.10.32.3-1~lucid1
gstreamer0.10-x (0.10.32.2-1~lucid7) to 0.10.32.3-1~lucid1
libgstreamer-plugins-base0.10-0 (0.10.32.2-1~lucid7) to 0.10.32.3-1~lucid1
libgstreamer0.10-0 (0.10.32.2-1~lucid2) to 0.10.32.3-1~lucid1
libgstreamer0.10-dev (0.10.32.2-1~lucid2) to 0.10.32.3-1~lucid1
```

I couldn't find any changelogs, though. No idea, if the update was at all related to the issue apparently only I experienced. But anyway, looks like everything is fine again now. :popcorn:

---

