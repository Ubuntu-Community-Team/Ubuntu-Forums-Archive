---
title: "PXE Boot will not launch"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by hankr on 2011-06-15
I am trying to get a PXE boot going, and all is fine, however the ethernet card will not come up. The kernel modules are installed, and I can see them in the boot log, however it gets stuck on 

eth0: no link during initialization
ADDRCONF(NETDEV_UP): eth0: link is not ready

During disk boot, this also happens twice, and finally on try 3 link comes up.

Any ideas? 

FWIW r8169 chipset

---

### Post by hankr on 2011-06-16
FYI, after trying the "boot to windows and fiddle the Wake on LAN after SHUTDOWN" fix that was mentioned elsewhere for the 8169 chipsets. Alas, this option wasn't even an option on latest windows.

It turns out I had to plug the mobo into a different switch and that fixed things. Yes, this was extremely odd, since the netboot actually WORKED to get and IP and the pxelinux kernel, and even the initrd and vmlinuz. However, it just wouldn't come back up.

Maddening waste of 4 hours of my life I am never getting back. Welll.... maybe. Next time I am trying a different cable/switch in the first 2 minutes of sleuthing.

---

