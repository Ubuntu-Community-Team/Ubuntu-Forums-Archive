---
title: "Can't record from Line In"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by gpenguin on 2007-07-31
Hello,

  I'm running Fiesty Fawn (XUbuntu) on an HP/Compaq D530C with an added Aureal Vortex au8820 card.  I can't seem to record using Line In...only mic.

I've tried 'arecord' and 'audacity'...neither work.  Though to be honest, I'm not sure how to use 'arecord', but 'audacity' I'm proficient.  My challenge is actually simple, when selecting the Recording device via the I/O tab, I have 3 options: OSS: /dev/dsp; ALSA: Aureal Vortex au8820:adb(hw:0,0); and ALSA: front.

I'm assuming 'front' are the front ports of the internal sound system.  Interestingly enough when I select 'OSS: /dev/dsp' or "ALSA: Aureal..." for my Playback device, both come through the Vortex card.  So my guess is any option with 'front' is irrelevant.

Nevertheless, how can I get the 'Line In' recognized/used.  How can I debug this?

Thanks!

--gpenguin

---

### Post by gpenguin on 2007-07-31
SOLVED!

Simple really...select the 'Line In' as the capture device.  The problem lied in the tools I was using.  Audacity had no way of making that selection.  xfce4-mixer has no way of doing that.  However, once I launched alsamixer(gui)...*then* I could select 'line in' as the capture source and bingo!

Hopefully someone will find this useful.

--gpenguin

---

