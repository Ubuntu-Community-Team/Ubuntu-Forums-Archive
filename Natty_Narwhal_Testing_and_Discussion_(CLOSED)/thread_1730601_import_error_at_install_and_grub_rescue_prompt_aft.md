---
title: "import error at install and grub rescue prompt after install natty beta 2"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by artifex on 2011-04-16
I would like to try Natty beta 2. When installing near the end it writes out that some import error happens and details are in /var/log/syslog file. When I reboot my system I get grub rescue prompt. Then I boot from Natty Live CD and found that /boot/grub have only one file (gfxblacklist.txt) and have no /boot/initrd file.

When I install grub from Live CD as Ubuntu help describe I get the /boot/grub files but still do not have the initrd file. The system starts up with a little help at grub prompt but this is not normal.

I made a clean install not an upgrade.

Why is it happen and how to solve? Is it a bug or feature?

---

### Post by drs305 on 2011-04-16
> **artifex said:**
> When I install grub from Live CD as Ubuntu help describe I get the /boot/grub files but still do not have the initrd file. The system starts up with a little help at grub prompt but this is not normal.

I don't know why initrd.img is missing, but if you are in a normal installation you can try to make it with:
```
sudo update-initramfs -u
```

---

