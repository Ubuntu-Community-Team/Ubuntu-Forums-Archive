---
title: "display 1 VGA out has no driver?"
date: 2012-02-18
forum: Multimedia Software
---

### Post by bludshot on 2012-02-18
I'm trying to hook up my laptop to my TV via the VGA out, but there's no signal.

Settings Displays shows only 1 display, my laptop's screen. Xrandr also shows only 1 display and no VGA out.

lshw -c video shows display:0 and for configuration: it says "driver=i915 latency=0"

But, for display:1 it says "UNCLAIMED", and for configuration: it says only "latency=0", ie: it shows no drivers for it.

Am I right in assuming that the reason ubuntu sees no VGA out on my laptop is because it has no driver for it?

If so, how do I fix this?


Thanks!

---

