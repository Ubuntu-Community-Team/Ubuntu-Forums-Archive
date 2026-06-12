---
title: "Can't boot from Mythbuntu installation disk"
date: 2014-09-21
forum: Mythbuntu
---

### Post by Adam_Jacobs on 2014-09-21
I am trying to do a clean install of Mythbuntu 14.04 on a system with brand new hard disks.

I have downloaded the ISO image, and have tried making both a bootable USB stick and a bootable DVD. I have not been able to boot from either.

When I try booting from the DVD, I get a message saying "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". I'm pretty sure there's nothing wrong with the DVD. I have checked the md5 sums and they are OK. And yes, I am aware of the difference between burning an ISO image (which is what I did) and simply copying the .iso file to the disk (which I didn't).

More convincingly if I put the disk in a different machine it can boot from it, so I guess if there was some subtle trick I needed to make it bootable, then I did that OK too.

I also tried booting from an old bootable CD on the machine I'm trying to use, and that was OK. Is it possible that some motherboards can boot from CD but not from DVD? The motherboard in question (a Gigabyte GA-M78SM-S2H) is the best part of 6 years old.

Is this something I can maybe fix by tweaking some BIOS settings?

Alternatively, is there a way I can get some kind of minimal version of Ubuntu installed from a CD, and then add the MythTV bits once I've got Ubuntu working? I'd kind of hoped to do the Mythbuntu install, but I guess installing MythTV on top of a minimal Ubuntu system would work too, yes? What kind of minimal system would I want to install? Would it be the Ubuntu server version?

---

### Post by Adam_Jacobs on 2014-09-22
OK, well I did indeed manage to load Ubuntu server from a CD, to which I added first Unity and then MythTV. It's mostly, but not completely, working. Will start separate threads for the things that don't work.

---

### Post by khPWXxF on 2014-09-23
It is a DVD capable drive, not an older CD only model?
Phil

---

### Post by Adam_Jacobs on 2014-09-23
Yes, it can certainly read DVDs in the normal course of events. But it seems that it can't boot from them. Or at least it couldn't boot from the Mythbuntu DVD.

---

