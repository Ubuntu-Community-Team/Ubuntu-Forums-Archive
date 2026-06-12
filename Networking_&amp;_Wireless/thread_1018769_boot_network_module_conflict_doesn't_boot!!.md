---
title: "boot network module conflict: doesn't boot!!"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by gionnico on 2008-12-22
Here the last message before it locks up.
It doesn't go on, but with recovery mode it starts normally.

I've just installed ubuntu 8.04.1

```

kernel: 8139cp 0000:03:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
kernel: 8139cp 0000:03:08.0: Try the "8139too" driver instead.

```

I've put 8139cp in /etc/modprobe.d/blacklist and 8139 in /etc/modules but nothing changed.

---

### Post by mpokrywka on 2008-12-22
> I've put 8139cp in /etc/modprobe.d/blacklist
I hope you put line "blacklist 8139cp" in that file.
Also invoke:
**sudo update-initramfs -k all -u**
to rebuild initrd - to include updated "blacklist" file.

To make booting more verbose (to see where the problem is),
when grub menu appears go to normal boot menu, press e (edit)
and remove "quiet" and "splash" from kernel command line.

---

### Post by gionnico on 2008-12-24
> **mpokrywka said:**
> I hope you put line "blacklist 8139cp" in that file.
Also invoke:
**sudo update-initramfs -k all -u**
to rebuild initrd - to include updated "blacklist" file.

To make booting more verbose (to see where the problem is),
when grub menu appears go to normal boot menu, press e (edit)
and remove "quiet" and "splash" from kernel command line.

Thanks, I didn't know the update thing.

---

