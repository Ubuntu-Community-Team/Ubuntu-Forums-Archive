---
title: "PVR-350 + PVR-150 Driver issue?"
date: 2008-08-03
forum: Mythbuntu
---

### Post by Jaaxx on 2008-08-03
I have a Compaq Presario that I have setup with a PVR-350 and a Nvidia 6600 PCI-E.  This setup works flawlessly.

I then decided to add a PVR-150.  In the backend setup, the card is recognized and I can scan channels from it.  Also I can get video from mplayer.  However, after a reboot the card will no longer tune any channels either in Myth Setup or with mplayer.

Dmesg states it is using tuner=47.  I have tried forcing tuner=50 in modprobe.conf with no results.  

The PVR-150 was originally sharing an IRQ with the Nvidia card.  I shuffled the card several times to no avail.  Eventually I set the BIOS to non plug and play and now everything has it's own irq, but the problem remains.

This pattern is repeatable over appx 6-7 fresh installs.

Any ideas?

---

