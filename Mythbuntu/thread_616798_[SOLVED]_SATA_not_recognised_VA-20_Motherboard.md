---
title: "[SOLVED] SATA not recognised VA-20 Motherboard"
date: 2007-11-18
forum: Mythbuntu
---

### Post by neilneil2000 on 2007-11-18
I have just installed Mythbuntu 7.10 and during the install process I chose the manual partitioning method and set up the system to install on to an IDE hard drive.

In the partitioning window I could see all my drives (two IDE & two SATA).

The install went without any problems but when I loaded mythbuntu for the first time I noticed that the SATA drives weren't being mounted.

I am very confused!

The output from lsmod | grep sata is:

sata_via               12548  0
libata                125168  2 ata_generic,sata_via

I am using an ASUS VA-20 motherboard.

Please help

Neil

---

### Post by ubnewbie2 on 2007-11-18
> **neilneil2000 said:**
> I have just installed Mythbuntu 7.10 and during the install process I chose the manual partitioning method and set up the system to install on to an IDE hard drive.

In the partitioning window I could see all my drives (two IDE & two SATA).

The install went without any problems but when I loaded mythbuntu for the first time I noticed that the SATA drives weren't being mounted.

I am very confused!

The output from lsmod | grep sata is:

sata_via               12548  0
libata                125168  2 ata_generic,sata_via

I am using an ASUS VA-20 motherboard.

Please help

Neil

Can you mount them manually?  If so, just add them to fstab so they will mount at boot time.

---

### Post by neilneil2000 on 2007-11-27
Yeah thanks, I didn't think to try that!  I am a bit new to this Linux thing you see!

I have now "fstabbed" them and all is well!

Thanks!

---

