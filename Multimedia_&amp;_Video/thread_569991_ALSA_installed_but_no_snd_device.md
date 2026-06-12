---
title: "ALSA installed but no snd device"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by jrlii on 2007-10-07
A while back I installed the ALSA drivers for my Echo Layla (They were compiled under Ubuntu 6.06.) and now playback works fine. 

However, I finally got around to trying to record with first Ardour and then Audacity and met with no success.

When I start Qjacktl, jackd fails to start. When I open the Setup window in qjacktl everything looks pretty normal, except the interface pull down is greyed out.

Working through the sound guide, everything looks good 'till I try to find the snd device, which fails. 

The Layla is listed as a "multimedia device" Here is the paragraph:

01:0a.0 Multimedia controller: Motorola DSP56301 Digital Signal Processor (rev 02)

        Subsystem: Echo Digital Audio Corporation Layla rev.0

        Flags: bus master, medium devsel, latency 192, IRQ 5

        Memory at e7010000 (32-bit, non-prefetchable) [size=64K]


The Echo mixer is there, as is the ALSA mixer.

As I said, Audacity can play back existing files, as can Totem and Ogle, but qjacktl can't seem to see an audio interface and Audacity can't seem to find the inputs.

Any notion as to what is going on?

Thanks in advance!

---

### Post by jrlii on 2007-10-07
PS - Gnome-alsamixer can't find it either.

---

