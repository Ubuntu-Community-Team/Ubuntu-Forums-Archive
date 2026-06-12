---
title: "Samba performance on virtual box"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by ofnuts on 2011-08-01
I have a WinXP virtual box and have setup a Samba server to have it use directly a couple of directories on the Linux side. The Samba performance is definitely better than the built-in shared folders of the virtualbox, but there is nothing to write home about either: transfer seem to top at around 3Mbyte/sec.

The machine is a laptop (Core i5 CPU (M520@2.40GHz) and a 7200RPM HDD) running Kubuntu 10.04.

The Samba share uses a dedicated "host-only" network adapter. There is an iptable-based firewall to which i added the required 4 statements to let the Netbios traffic go through (without them nothing works...)

So, given the hardware, are the 3MB/s a decent figure? And if not, what should I aceeive, and where can I look improve on the current numbers?

---

### Post by ofnuts on 2011-08-04
Answering to myself.... yes we can... After enabling a second processor in the guest XP the figures above have been improved 2x-3x.

---

