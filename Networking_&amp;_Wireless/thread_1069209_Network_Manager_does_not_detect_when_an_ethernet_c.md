---
title: "Network Manager does not detect when an ethernet cable is plugged in after boot."
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by thefirstM on 2009-02-13
I am having a problem where if a boot my PC (a Dell Vostro 1500 running Kubuntu Jaunty x64 alpha) without an ethernet cable attached, and then attach one later, network-manager does not notice the connection or get an IP address.  I can manually force it to get an IP with "sudo dhclient eth0" or create a manual connection with the Network Manager plasmoid.  The ethernet device in question is a Broadcom 4401, using the b44 module.

---

