---
title: "rythmbox randomly crashing"
date: 2009-01-01
forum: Multimedia Software
---

### Post by csc2ya on 2009-01-01
I'm running Ubuntu Ultimate 1.8 (based on Hardy Heron). I had to reinstall recently after replacing a failing HDD. I usually listen to music in rhythmbox while i'm doing other things on my laptop.

However recently, rhythmbox has started crashing randomly.

There is nothing I can do which will reproduce the crash other than playing music off of my HDD, as it can happen at any time.

I have run rhythmbox in debug mode and I got the following just before the last time it crashed which was when I took it off of pause mode:

```
(23:41:40) [0x8e7e7d8] [perform_seek] rb-player-gst-xfade.c:1189: leaving paused stream file:///home/administrator/Music/Alex%20K%20Vs%20Plummet%20-%20Damaged%20Donk%20Mix.mp3 unlinked
(23:41:40) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/administrator/Music/Alex%20K%20Vs%20Plummet%20-%20Damaged%20Donk%20Mix.mp3, 146:208(1)]
(23:41:40) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/administrator/Music/Alex%20K%20Vs%20Plummet%20-%20Damaged%20Donk%20Mix.mp3, 146:208(1)]
(23:41:40) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/administrator/Music/Alex%20K%20Vs%20Plummet%20-%20Damaged%20Donk%20Mix.mp3, 146:208(1)]
(23:41:41) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/administrator/Music/Alex%20K%20Vs%20Plummet%20-%20Damaged%20Donk%20Mix.mp3, 146:208(1)]
(23:41:41) [0x80dc408] [tick_cb] rb-shell-player.c:3223: tick: [file:///home/administrator/Music/Alex%20K%20Vs%20Plummet%20-%20Damaged%20Donk%20Mix.mp3, 146:208(1)]
(23:41:41) [0x80dc408] [stop_sink] rb-player-gst-xfade.c:2598: stopping sink

```

---

### Post by khelben1979 on 2009-01-01
You could reinstall the program or... compile it yourself from source code.

[Rhytmbox on Sourceforge.net]("http://rhythmbox.sourceforge.net/download.html").

---

### Post by ubudog on 2009-01-01
Yeah just try reinstalling the program.

---

### Post by csc2ya on 2009-01-01
Reinstalling it didn't seem to help earlier, but touch wood, it doesn't appear to be doing it now.

I didn't think of it earlier, but I did have a virtual machine running in virtualbox earlier doing an OS install which was causing high loads, so that may be the reason for it, and now I think of it, it was last night when I was installing another one that the problem started.

I'll have to see if it does it at all later on while leaving the virtual machine's powered off.

Thanks for trying to help:)

---

