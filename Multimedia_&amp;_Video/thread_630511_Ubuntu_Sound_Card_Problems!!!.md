---
title: "Ubuntu Sound Card Problems!!!"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by iamkidd on 2007-12-03
I have an interesting situation with going on with my Ubuntu computer.  I have the latest version of Ubuntu installed.  I have 2 sound cards on my computer:  one that is attached to my motherboard and a much nicer PCI one (some kind of Audiology ZS2 or something like that)  I have all of my speakers connected to the PCI card.  Sometimes, at random, when I boot up my computer, I’ll have no sound at all – nothing.  Sometimes I can reboot it and the sound will come back.  Sometimes it doesn’t.  Someone suggested that I disable the motherboard’s sound card in the system BIOS and that might solve the problem.  Does anyone know what’s going on or can suggest a quick fix for this?  Keep in mind I’m fairly new to the Linux desktop.

Thanks!

Jason

---

### Post by kyphi on 2007-12-03
That poor computer of yours must be getting terribly confused about which sound device to load.

Go into the BIOS and disable your on-board sound chip.  That way your computer will use the Creative Audigy sound card (much better sound output).

Don't forget to plug your speakers into the card outputs.

---

