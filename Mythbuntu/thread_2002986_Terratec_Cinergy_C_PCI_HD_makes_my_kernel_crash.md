---
title: "Terratec Cinergy C PCI HD makes my kernel crash"
date: 2012-06-13
forum: Mythbuntu
---

### Post by Japsertje on 2012-06-13
Hi,

I've got a problem on my hands! I just got my new DVB-C tuner(Terratec Cinergy C PCI HD), and when I put it in my computer and turn my computer on it shows a kernel panic!

I'm using Ubuntu 12.04 and Mantis added to /etc/modules

So if anyone can help me I would be very happy ;)

---

### Post by alien878 on 2012-06-14
I have a Terratec Cinergy S2 PCI HD (similar driver) and it is working on 12.04.  I did not need to edit /etc/modules or install the drivers as it (finally, as of 12.04) works out-of-the-box.

Note that I have pinned the kernel as I have had problems with this card with various kernels in previous releases.  You might try an older 12.04 kernel (there was one released a couple of weeks ago that caused me headaches, so I backed it out and pinned it again).

Final note:  The IR support has been removed from the mantis drivers in the kernal for some reason.  I now have to use a separate USB IR receiver.

Cheers,

Allen

---

