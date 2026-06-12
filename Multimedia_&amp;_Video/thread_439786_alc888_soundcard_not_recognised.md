---
title: "alc888 soundcard not recognised"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by prolapsedisk on 2007-05-11
I might be having problems with this. Sound, etc. works fine, but the messages i get from qjackctl and lscpi is this


00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 2a47
        Flags: bus master, slow devsel, latency 64, IRQ 20
        Memory at fbff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

And qjackctl audio interfaces read as

hda ati sb
alc883 (Analog)

and asoundconf list
Names of available sound cards:
SB

But i have a realtek alc888 onboard sound instead according to my mobo maker, so is there anyway to get my soundchip recognised? The reason i ask is that pure data through alsa generates quite a bit of xruns and I'm wondering if it will affect any of the other apps i plan to run.

---

