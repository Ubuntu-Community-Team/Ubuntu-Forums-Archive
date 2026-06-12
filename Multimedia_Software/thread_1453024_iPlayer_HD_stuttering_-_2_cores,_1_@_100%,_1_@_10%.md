---
title: "iPlayer HD stuttering - 2 cores, 1 @ 100%, 1 @ 10%"
date: 2010-04-12
forum: Multimedia Software
---

### Post by UltraAnders on 2010-04-12
HD content skips a lot on iPlayer Desktop. Htop shows one core usage at 100%, with the other around 10%. Is there any way to get a better balance or is this a fundamental issue, e.g. Adobe AIR problem or video must be decoded sequentially?

Jaunty Jackalope 9.04
Core 2 Duo 6420
Asus P5B
2GB RAM
GeForce 8800 GTS 320MB

Cheers, Anders.

---

### Post by UltraAnders on 2010-04-13
Quick update, I installed iPlayer Desktop on Windows XP and HD content is smooth, with load distributed fairly evenly across both cores at ~65% usage.

---

### Post by UltraAnders on 2010-04-16
Thought I'd post a screen shot of HTop to demonstrate. iPlayer is running 7 different processes, with the top 2 using 45% & 35%. [IMG]http://www.andersharrison.com/pics/screenshot8.png[/IMG]
A helpful person on another forum pointed toward something called the affinity mask, can anyone advise on that?

As an alternative (although not widely applicable) solution, I've made a modest overclock on my CPU, getting it up from 2.16 to 2.4 GHz and it's stable. This has made a noticeable difference to HD playback, so I'm pushing the CPU on further.

---

### Post by cottfcfan on 2010-04-17
sounds like the usual Flash issues to me. Most of us have them.
When I watch BBC iPlayer in full screen its just about passable.
HD is an absolute no go.
This issue seems to have been addressed somewhat in the upcoming Lucid release.

---

### Post by UltraAnders on 2010-04-28
> **cottfcfan said:**
> sounds like the usual Flash issues to me. Most of us have them.
When I watch BBC iPlayer in full screen its just about passable.
HD is an absolute no go.
This issue seems to have been addressed somewhat in the upcoming Lucid release.Nice to know I'm not the only one in this boat. Looking forward to 10.04, should be very soon (tomorrow??). I have to watch it windowed because the iPlayer (and many other apps) seem to think my second monitor is larger than it actually is.

For info, 2.4 GHz (and some tight memory timings) seems to be the minimum for my setup to play HD. Dr Who is fine, Wonders of the Solar System still skips the odd frame on the big shots, e.g. Earth. Maybe there is a difference in resolution between the 2 programs?

---

