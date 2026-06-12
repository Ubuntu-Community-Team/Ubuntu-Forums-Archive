---
title: "low sound volume for mp3 playback on Toshiba Satellite A505 laptop"
date: 2009-09-28
forum: Multimedia Software
---

### Post by website.reader3 on 2009-09-28
I have a problem with low volume on mp3 playback.  This is a recurring issue as I noticed rereading old postings.  I did try some of the suggested fixes, including setting the options snd-hda-intel model=toshiba in the alsa-base.conf file, but nothing has worked so far to restore normal volume to a mp3 playback from Totem.

I did notice that padevchooser was NOT installed, so I had to do that and it provided more information on the hardware.

My Toshiba Satellite A505-S6970 is using the 

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff1e
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d8400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

according to lspci -v.

I am currently using the Pulse Audio Soundserver as my choice for almost all Sound settings under the System preferences sound menu selector

Any ideas?  The system sounds are loud, they come through very well but I need more volume from the mp3 software.

- Randall

---

