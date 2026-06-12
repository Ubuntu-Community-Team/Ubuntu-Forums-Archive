---
title: "Booting problem with Mandriva"
date: 2008-06-26
forum: Mandriva/Mageia
---

### Post by archat68 on 2008-06-26
I downloaded "mandriva-linux-2008-one-KDE-cdrom-i586". I burned the CD at 4X speed. Also i checked the md5 checksum which indicates the download is o.k.


I tried Mandriva in LiveCD mode. It failed to boot.It stopped with a blank screen just after showing the message "Loading Linux kernel". I tried different options by changing resolution and also selecting noapic, acpi=off etc. without any effect.

Surprisingly Ubuntu booted at first try.

I also downloaded and tried livecd of Mint toady. Faced same problem. After the initial splash screen it shows "loading vmlinuz.." followed by "loading initrd..." and then just hangs.I've tried the compatibility mode also.

So which may be the problem here?
My config is :
Athlon dual core 4000
Jetway 680G motherboard (ATI 1200 series display driver)
2GB RAM
160GB PATA, 80GB SATA (divided in two NTFS partitions)
IDE DVD-RW

However, the Mandriva One CD and the Mint CD that I've downloaded work correctly on other computer with Intel chipsets. So, I think the problem is with my ATI display driver.Is it?

---

### Post by AdamWill on 2008-06-26
No, the problem is too early for it to be related to the graphics chip, most likely.

Which version of Ubuntu booted okay? Mint and Ubuntu are fairly similar, so it's surprising for Ubuntu to work and Mint to fail - trying to find what's different between the version of Ubuntu and the version of Mint you used seems like the most likely way to narrow down this problem. Good luck!

---

### Post by archat68 on 2008-06-27
I tried Ubuntu 8.04 and Mint 5.

---

### Post by AdamWill on 2008-06-27
Huh...well they're equivalent versions, I think.

Can you check what version of the kernel each distro uses? Mandriva uses 2.6.24.4 , during installation.

---

