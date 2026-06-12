---
title: "Restarting Intel graphics driver without reboot or logging out?"
date: 2013-12-31
forum: Multimedia Software
---

### Post by Ranko Kohime on 2013-12-31
So, as of late I've been having issues with my Intel-based laptop.  In addition to the HDMI port not working, (UI completely freezes when plugged in, and unfreezes when unplugged), which I suspect is a hardware issue, I've had instances where the desktop becomes slow.  It is exactly like viewing the desktop through a VNC connection, actually.  Things draw in slow motion, YouTube videos are stop-motion, etc.

Reboot obviously fixes the latter issue.  As well, merely logging out and logging back in again will accomplish the same, as doing so causes the X server to restart.  However, I run a LOT of applications, and restarting them all and getting back into my work flow can take as much as half-an-hour.

So to my question, is there any way to just restart the graphics driver, without restarting the whole session?  Alternatively, a "screen" (tmux)-like solution, wherein the applications are run inside of a sandbox, would probably work for me as well.  I'm aware of Xephyr, but I would suspect that it would crash upon losing connection with the X server.

---

