---
title: "Odd NIC/DHCP Issue"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by atrocity on 2009-05-10
Upgraded from 8.10 to 9.04 today.  Computer has a100Mb NIC on the motherboard, but I haven't used it in years, instead preferring a separate gigabit card.  After the upgrade, the gigabit card didn't work (didn't obtain an IP) but the separate one did.

Edited the network configuration file to auth eth1 ahead of eth0 and the gigabit card worked, but here's where it gets really weird (and I don't know if this is really an Ubuntu issue):

My router (192.168.0.1) is set up to always give the Ubuntu machine the same IP.  But I also have a wireless access point set up at 192.168.0.50 and somehow Ubuntu--consistently--managed to get an IP address from there rather than from the main router!

I just wound up doing a static IP, but it seems pretty odd.  I'm not sure I'm even looking for help or advice at this point since I have a workaround, it just seemed like something worth mentioning.

Possibly it's related to the fact that the little network icon in Gnome has said for three Ubuntu versions now that I'm not even connected to a network and won't allow me to make any changes via the GUI...

---

