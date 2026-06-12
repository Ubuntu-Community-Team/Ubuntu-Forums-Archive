---
title: "Huge boot time after Natty beta upgrade"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Correnos on 2011-04-14
Yesterday I upgraded my main system with a BTRFS root from 10.10 to the Natty beta. Things have been mostly good after the upgrade, but a glaring issue is the massive boot time witnessed after the upgrade. The bootchart graph made after the upgrade is far too large to be attached here, but it shows fsck.btrfs taking up over three minutes (!) of boot time. I suppose that alone is not too alarming given the amount of data present, but what is aggravating is that this taking place *every boot*. Is there a way to disable fsck-on-boot altogether? I've tried adding nobootwait in /etc/fstab for my root partition, without effect.

---

### Post by lithopsian on 2011-04-15
Filesystem checking intervals are controlled on the filesystem itself.  Change fstab.  Seems like fsck with Btrfs is an issue for many people but not as bad s you have it.

---

### Post by Correnos on 2011-04-15
> **lithopsian said:**
> Filesystem checking intervals are controlled on the filesystem itself.  Change fstab.  Seems like fsck with Btrfs is an issue for many people but not as bad s you have it.

Thanks for the info. Do you know which tag should be added to fstab?

---

