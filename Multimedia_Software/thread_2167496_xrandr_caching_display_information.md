---
title: "xrandr caching display information"
date: 2013-08-13
forum: Multimedia Software
---

### Post by princesshammer on 2013-08-13
I'm trying to connect a projector. The laptop screen + projector at native resolution exceeds what the video card can do, apparently (xrandr complains that 1600x1600 is the max). However I was able to get it to work once by disabling the laptop screen like so:

xrandr --output LVDS --off
xrandr --addmode DFP1 1280x720
xrandr --output DFP1 --mode 1280x720 --rate 60

That worked great for one session, but now whenever I plug in the projector the X session on the laptop locks up, and there's no video on the projector.

It behaves like something in the system is caching display information and applying it in a broken fashion when the projector is connected. I also note that "xrandr" lists DFP1 as "disconnected", so it's definitely remembering something.

Where is this cache stored, and how can I remove it?

---

