---
title: "Choppy audio in after upgrade from edgy to feisty"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Jope on 2007-04-29
[Seems I had a stupid moment when typing in the subject, not "audio in" but "audio playing"]

I'm running Ubuntu on a Dell Latitude CSx (p3/500) laptop.

After upgrading to feisty, all media players + flash videos became very choppy.. The video plays ok, but the sound burps and squawks every few seconds.

Also if I play mp3s, they chop up.

No difference between alsa / oss drivers in VLC, for example.

Where should I continue looking?

---

### Post by __j__ on 2007-05-01
Choppy audio/video could be a timing problem. Has your system clock run slow or fast since upgrading?

I've had a timing issue with similar symptoms. When I was running 64-bit Edgy on my laptop (Dell Latitude D820, Core 2 Duo, Intel 945 chipset), I had to load the kernel with the "no_timer_check" and "notsc" parameters to keep the clock sane. The reasons for this were apparently fixed in Feisty, and these parameters needed to be omitted for proper timing once I upgraded.

Not sure if that helps, but I figured I'd throw it out there.

---

### Post by Jope on 2007-05-13
Hi, no clock issues here.

Cpu usage for VLC is at an amazing 1% and the load avg is 0.8 when playing.

Could the driver for this neomagic graphics chip be the problem..

---

