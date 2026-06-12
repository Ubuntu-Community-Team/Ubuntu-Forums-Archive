---
title: "No stereo sound until I reload alsa"
date: 2010-01-06
forum: Multimedia Software
---

### Post by stuart.camenson on 2010-01-06
Hey guys,

I am using a generic sound card (I don't know what type it is or how to find out unfortunately) that I installed after I blew out the sound card that was integrated into my motherboard.  Sound Preferences tells me that is is a VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller.

Here's the problem.  When I initially boot up the computer, sound only plays out of the right channel.  It does this no matter what sound I play, no matter what program I play it through.  However, as soon as I open a terminal and type in ```
sudo alsa force-reload
``` it works perfectly with stereo and everything.  Anything I can do to avoid having to type the command in all the time?  Anyone know what causes this?

Thanks!

---

