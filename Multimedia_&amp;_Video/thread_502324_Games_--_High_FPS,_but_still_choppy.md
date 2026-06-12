---
title: "Games -- High FPS, but still choppy??"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by xer0kill on 2007-07-16
I don't understand this at all! I've tried Tremulous and OpenArena and they both show my FPS staying right around 90, yet they both run very choppy. This is in single player mode even! I just got this new card working finally, but it's obviously not working optimally. Both games run beautifully in XP...

My new card: GeForce 7600GT, 256MB

It took me forever to get the driver working for the card, I had to reinstall Ubuntu. Then with a fresh install, I opened up Restricted Drivers Manager and enabled the NVidia driver. What should I do? Should I try Envy, attempt some sort of manual install, or what?

Is there any way at all to tell what version of the driver I have installed so I know what needs to be done? This video card stuff is the only thing that's given me any trouble with Ubuntu! Maybe someone knows what to do... ?

---

### Post by xer0kill on 2007-07-16
I seem to have mostly fixed the issue. I went ahead and used Envy. It said my drivers were up to date all ready, but it created a shortcut for the "NVIDIA X Server Settings" application. So I opened that program and here's what I did:

under "X Screen 0" --> OpenGL --> enable Sync to VBlank.

The performance is now on par with it running under XP. Just thought I'd post this in case anybody else is having the same issue.

---

