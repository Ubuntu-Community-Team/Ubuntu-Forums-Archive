---
title: "Bridging two networks"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by zx_sa on 2005-12-08
I need some help setting up my network. My machine's got two network interfaces. The first (which Kubuntu insists on calling eth1) is my onboard NIC which is connected to the work network and get's its IP via DHCP and is connected to the internet as well.

The second NIC is a PCI Realtek 8139 jobbie. This is connected by crossover cable to my laptop. Currently I've manually set its IP to 169.192.0.1 with netmask 255.255.0.0.

What I want is this: The laptop should be able to get an IP via DHCP and then be able to access the main network and internet.

So far I've looked at ipmasq but I just don't have a clue as to how to set this up.  Someone also said I should look at installing router software, but again I don't really know what to do. All I know is that this is possible because Mandriva did all this for me automatically.

Any ideas?

Regards,
ZX_SA

---

### Post by jasmuz on 2005-12-08
I recommend you use GUIDEDOG (wich is KDE based) & DNSMASQ, then you must route your packages from the PC to your lappy, thus there is no bridging.

Hope this helps.

---

### Post by jasmuz on 2005-12-08
I recommend you use GUIDEDOG (wich is KDE based) & DNSMASQ, then you must route your packages from the PC to your lappy, thus there is no bridging.

Hope this helps.

---

