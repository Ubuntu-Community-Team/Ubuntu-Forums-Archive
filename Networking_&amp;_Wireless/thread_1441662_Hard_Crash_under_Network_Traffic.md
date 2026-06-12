---
title: "Hard Crash under Network Traffic"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by Joshisfloyd on 2010-03-29
I am experiencing full lock ups (no keyboard, mouse, ssh etc...) when attempting to pull large amounts of data off my server (running Karmic server) to my ASUS 1201n netbook. I am currently under Lucid Beta 1, but I can reproduce the crash under Karmic on my machine also. All my networking currently is wired, so the problems with the realtek driver for my laptop should not matter. The problem is most pronounced under XBMC where it will lock the entire computer as soon as I attempt to navigate to any media screens. This has actually digressed, as it used to only effect XBMC, and I was able to kill the process from the command line. The wired card on this notebook identifies under ethtool as an Atheros Gigabit card, but only lists speeds up to 100 megabit, regardless of the full gigabit infrastructure around it.

One final quirk: I can pull media fairly reliably with VLC, but not with totem, rhythmbox, or any other program. Streaming music or video with any of these programs will result in an immediate lock-up.

Any help would be very much appreciated, and I can supply any data, such as the ethtool output, that would be necessary.

---

