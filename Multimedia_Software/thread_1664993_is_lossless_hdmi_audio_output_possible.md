---
title: "is lossless hdmi audio output possible?"
date: 2011-01-11
forum: Multimedia Software
---

### Post by pharcycle on 2011-01-11
Hi guys,

simple question really - i've been looking at sound cards like the asus xonar hdav slim that can output the DTS-HD and other high resolution surround formats. It unfortunately doesn't look like alsa is going to support hdmi out on the asus card anytime soon so i'm curious if there are any supported cards available?


David

---

### Post by BicyclerBoy on 2011-01-11
The current generation nvidia video cards support HD audio with alsa 1.0.23.

The only app I know of that can take advantage is MythTV0.24+fixes.

---

### Post by pharcycle on 2011-01-12
Hi, 

thanks for the reply, I'm assuming that by current, this doesn't extend to the 9800GT that i presently have in my HTPC? 

Are we talking about the GT5xx then?

Regards.
David

---

### Post by BicyclerBoy on 2011-01-12
The market for hdmi audio is htpc.

The nvidia GT220,240,430 are all reported to do HDMI HD audio.
These are also the minimum recommended feature set C purevideo/vdpau.

All the 4xx & 5xx & ION2 are feature set C but do not know about HDMI audio.

---

### Post by pharcycle on 2011-01-12
Yeah it's for my htpc! Will look for feature set c, cheers

---

