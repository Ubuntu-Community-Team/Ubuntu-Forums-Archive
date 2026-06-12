---
title: "problem with audigy 2 zs on edgy 64-bit"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by svurg on 2006-12-06
Greetings!

I'm having a heck of a time diagnosing a sound problem, and am hoping that someone here has run into something similar and can help.

I've got an ASUS K8V SE motherboard (VIA chipset, latest BIOS), Athlon-64 3200, Audigy 2 ZS, and am running Edgy 64 bit.

The system recognizes the sound card, and it works just fine in stereo mode after bootup (I haven't tried to deal yet with 5.1).

The trouble starts after I suspend (which I do to save power) and later resume.  From that point until I reboot, if I put any kind of load on the system, sound drops out and all I get is a continuous tone.

The same behavior occurs on Windows XP (which I have dual-booting on this system) -- fine on initial boot, useless after resume.  I've tried using different PCI slots -- same result.  I've also confirmed that the slot I have it in now (one from the bottom) is not shared with any other devices.

My searches have indicated that the issue may be PCI bus latency -- when I start pushing data from the hard drive across the bus, the sound card gets starved and can't maintain its sound data stream.  While there are some suggestions regarding changing some BIOS settings, nothing so far has worked for me.

Needless to say, I'm pretty frustrated.  If anybody has any ideas how I can resolve the issue, I'd be greatly appreciative.  Yeah, I could just shut down and reboot instead of suspend/resume, but I'd hate to give up the convenience.

Stumped,

Warren Madden

---

