---
title: "No Operating system after bad shutdown (system recovery)"
date: 2008-06-03
forum: Mythbuntu
---

### Post by thusgaard on 2008-06-03
Last night I lost power during a planned shutdown of my muthbuntu. Now it won't boot. The machine just delivers a short message telling me no operating system is avaliable. 

How do I recover from here?

My foundation is a 7.10 upgradet to 8.04, all avaliable updates have been installed. 

J;-)

---

### Post by klc5555 on 2008-06-04
I'm no expert on this, but someone needs to start. I'd say it depends on your system configuration.

If your recordings are safe on a second hard disk, along with a recent (and reliable) mythconverg backup, recovery can be as simple as wiping the boot hard disk, reinstallation, and restoring mythconverg from the recent backup on the second disk. Total recovery time --about 20 minutes. This was what I did last time my local power company decided to do line maintenance in the middle of the night and toasted my installation with power ripples and brownouts.

If everything is on one hard disk, (or perhaps in one partition on one hard disk) then life becomes more difficult. 

A first step might be to use the installation CD as a bootdisk to see if your root partition and can be booted from and mounted. If it can, then, (after first of all making a mythconverg backup assuming very recent regular backups beyond the default once-weekly ones don't exist) repair work on the installation can begin.  Hopefully mythconverg will be uncorrupted or you have a recentish backup accessible; otherwise saving the installation might be more time-consuming than it's worth.

If your root partition can't be booted from and mounted from a bootdisk, then appropriate measures would depend on just how badly things on the drive are determined to be toasted. :(

Hopefully others will chime in on this too.

Good luck.

---

