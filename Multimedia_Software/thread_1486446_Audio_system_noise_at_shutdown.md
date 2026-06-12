---
title: "Audio system noise at shutdown"
date: 2010-05-17
forum: Multimedia Software
---

### Post by njsharp on 2010-05-17
Briefly: Horrible noises from the amplifier at shutdown.  NOT experienced with same HW when shutting down WXP MCE.

HW: Dell Dimension 9150, 2Gb, SATA 2 500Gb HD, 3.2GHz dual
MM: 5.1 analogue output to Logitec amp
SW: now U10.04 64bit BUT always same problem whatever release

I'm thrilled FINALLY to have obsoleted WXP MCE having at last managed to configure MythTV (loaded on top of U10.04).  However, still annoyed by this:

When I shut down Windows Media Center using the complete shut down option (ie, turn off PC not just stop MC) it all goes to sleep quietly, depsite the fact that the amplifier is still on.  If I shut down Ubuntu, (doesn't matter whether I have run and shut MythTV or not run it at all), there is a horrible crackle and thump noise from the amplifier just as the PC turns itself off.

I'd love to stop that.  Anyone know what does it, and whether it can be suppressed?  Let me know if you want any further evidence or tests.  I may need complex tests spelt out for me!

I wanted to tell you what sound modules I am using, but I see that at 10.04:

SYSTEM>PREFERENCES>SOUND

no longer offers choices indicating pulse, alsa, oss etc so I don't know, other than to note that Myth offered:
audio output device: "ALSA:default" and I added
speaker configuration: 5.1

I don't recall making any other choices elsewhere in the system, so it is whatever the default is.  Anyway, this phenomenon has occured after pure Ubuntu installs with no Myth at all.

---

