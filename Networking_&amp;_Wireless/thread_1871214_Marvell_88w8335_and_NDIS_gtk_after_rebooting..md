---
title: "Marvell 88w8335 and NDIS gtk after rebooting."
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by and1bskbl72 on 2011-10-28
I installed the windows drivers for this pci networking adapter using the ndis tool. When it is installed after a few seconds it is recognized and working. However, after reboot it is not recognized but is still installed in ndis. The solution for now is to uninstall that driver and reinstall it and it works again. I have tried adding sudo modprobe -m but I need some direction on how to get it to run after reboot so I don't have to uninstall and install each time.

01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

Running 11.10


Thank you

---

