---
title: "No Flash audio on my CMI8788-based Razer AC-1 in 8.04 and 8.10"
date: 2008-09-18
forum: Multimedia Software
---

### Post by johnnynapalm on 2008-09-18
Like most people with a CMI8788 based card, I'm having issues with Firefox 3 and flash videos (no audio).  I have reinstalled the ALSA drivers, reinstalled Flash numerous times (tried both the newest version of 9 and the RC for 10), to no avail.

Maybe this is a bigger problem?  Soundcard detection is better in 8.10 (I use the entry for CMI8788-Digital, it's wired optically so that makes sense), but PulseAudio has never worked with either release.

Can you think of maybe something really simple I'm missing here?  Everything else is running nicely.  Thanks in advance.

---

### Post by markbuntu on 2008-09-18
Currently PulseAudio is only able to detect and use Device 0 on any sound card. This makes digital outputs, which are ususally Device 1 or Device 2 unavailable in PulseAudio. You can read more about that here:

[http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139)

---

