---
title: "System sound and multimedia sound on seperate sound cards"
date: 2008-07-21
forum: Multimedia Software
---

### Post by mliungman on 2008-07-21
Hi!

Bear with me on this one...

I have two sound cards: one integrated on the motherboard and one PCI Ensonic Sound Blaster 128 card. I prefer the PCI card for quality reasons, and have chosen it to be my default for all sounds. After the last update of Hardy Heron, all sound was directed through the integrated card instead. I followed the steps in LordRaidens thread [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449"), and edited /etc/modules to load my PCI card. I did not, however, do the "Saving Sound Settings" steps before rebooting.

Now, the admin account has "Detect automatically" as default choice in the Sound Management and uses my PCI card for all sounds. The remaining accounts on the PC must have the PCI card as default choice, and then only multimedia sounds come from the PCI card, while system sounds go through the integrated card.

I have checked that all user accounts belong to the audio group in /etc/groups, and I have not found any .asoundrc file in the main account's /home directory.

Questions:
Will following the "Saving Sound Settings" steps make the system sound go through my PCI card?
If not, how do I get my PCI card to handle ALL sounds?

Thanks

Martin

---

