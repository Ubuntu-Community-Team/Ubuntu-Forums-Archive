---
title: "Using wifi without installing nvidia"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by karlhm76 on 2009-04-18
Hi All,


I'm running Gutsy and this seems like a fairly standard request:

How can I use my wireless card restricted module without installing the nvidia restricted module? Is it even possible?

I have a system with a DLink (Atheros) wireless card, and an Nvidia 7600GS graphics card.

I'm using the latest Nvidia drivers I downloaded from Nvidia and compiled into a module myself.

The nvidia driver works great and fast, far better than nvidia-glx-new but the only problem is, if I have the nvidia-kernel-common package installed my system decides there is some huge conflict and starts in failsafe graphics mode.

however, to remove the nvidia package, I also lose the restricted drivers which means my wireless stops working. :confused:

---

### Post by karlhm76 on 2009-04-18
Hi all, this was solved

I downloaded the latest madwifi code from madwifi-project.org and compiled it.

No sooner had I typed make, sudo make install and sudo modprobe ath-pci into a command prompt, network manager picked up the old wireless connection and connected.

Its great when things work..

however: what's the rationale behind having the wifi driver dependent on the nvidia driver?!?

---

