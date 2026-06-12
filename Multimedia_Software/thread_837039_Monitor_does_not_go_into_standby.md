---
title: "Monitor does not go into standby"
date: 2008-06-22
forum: Multimedia Software
---

### Post by HyperHacker on 2008-06-22
I have 2 monitors connected to an Nvidia GeForce 6200 OC: an LG L226WA connected to DVI, and an NEC 90GX2 connected to D-SUB. They're set up as Twinview in nvidia-settings, with the LG the primary display (though I tried having the NEC be primary too)
When I try to put them in standby using "xset dpms force (off/standby/suspend)", the LG does it fine, the NEC just shows a "no signal" message that remains until I turn them back on. In Windows it would show this message, then go into standby after a few seconds, but in Xubuntu it just keeps the message on the screen.
I suspect the NEC is not being told to stand by, due to X seeing the two as one big display (nvidia-settings shows both as being screen #0) and isn't smart enough to do it on its own.

Also, using XScreensaver, the monitors don't go into standby after 20 minutes like I've set in the power management control panel. The screen saver just keeps running.

---

