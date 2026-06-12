---
title: "Wireless problem"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by DanielGerep on 2011-03-26
Hi,

I'm new to Ubuntu and I'm using the version 10.04.

I'm using Acer  Aspire 4736z and I'm having a terrible problem.

I have to try for like 5 or 6 times before it really connects to my wireless and is very unstable.

And another thing is that sometimes my screen blinks.

Have someone been through this?

Thanks for any help.

ps: sorry, my English is not good

---

### Post by Dark_Stang on 2011-03-26
What kind of wireless card is in it? Acer isn't informative, they just list "Acer InviLink". If you don't know what kind of wireless card is in it, you'll find it listed by one of the following commands.
```
lspci
lsusb
```
lspci - This one lists PCI devices.
lsusb - This one lists *shock* USB devices.

---

### Post by DanielGerep on 2011-03-27
Hi Dark_Stang, thanks for your reply.

lspci returned:

04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)

lsusb returned:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15d9:0a33 Dexon Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Hope that helps, thanks =)

---

### Post by adam.webb on 2011-03-27
Sounds like the problem that some of us have been having with the latest updates...

---

### Post by Dark_Stang on 2011-03-27
I see a handful of reports that says this stopped working in recent updates. You may want to install the backported wireless drivers and see if that solves the problem. If you look under synaptic the package will be called something like...
linux-backports-modules-wireless-ubuntu_version-generic

---

### Post by DanielGerep on 2011-03-28
Ok Dark_Stang, I'll try "linux-backports-modules-wireless-ubuntu_version-generic" later and post the results here...

Have any idea about my video glitches? It keeps blinking from time to time.

Thanks!

---

### Post by TBABill on 2011-03-28
Not sure about the video issues, but in KDE you may find better results installing either the Gnome network manager or wicd rather than using the knetwork manager. With my Broadcom devices I could never connect at all with knetworkmanager.

---

