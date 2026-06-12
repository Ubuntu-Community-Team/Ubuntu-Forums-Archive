---
title: "NVidia SLI"
date: 2009-10-14
forum: Multimedia Software
---

### Post by KozyMatt on 2009-10-14
I'm using an M3N-78 Pro motherboard with onboard NVidia GeForce 8300 and a NVidia GeForce 8400 GS plugged into it.

[IMG]http://kozynetwork.net/files/NVidia8300.png[/IMG]
[IMG]http://kozynetwork.net/files/NVidia8400GS.png[/IMG]

As you can tell by the screenshots, the onboard card has memory (shared from RAM). I'm really looking to get use out of it.

The motherboard supports Hybrid SLI but I understand that there is no support from NVidia for Hybrid specific features such as power saving.
However, I'm more interested in the performance boost. Would it be possible to configure it to act like a regular SLI setup?

Using Ubuntu 9.04


~Kozy

---

### Post by KozyMatt on 2009-10-15
bump

---

### Post by KozyMatt on 2009-10-16
bump

---

### Post by hadi2 on 2009-12-30
hi 
have you ever tried enabling the multigpu function of nvidia-xconfig ?
sudo nvidia-xconfig --multigpu=On

---

### Post by tnt533 on 2010-04-07
You're not going to be able to do SLI with two adapters that are not the same model, video ram amount, ect, ect. So using your pci-e adapter and on-board adapter in SLI is just not doable.

As for using both adapters in other ways? That might be possible.

---

