---
title: "Zyxel P-2812 crashes when connecting with 802.11n from Ubuntu"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by karlstad on 2013-06-14
Hi

As the title says, my Zyxel P-2812 router crashes and needs to be rebooted if I try to connect to it from Ubuntu. This only happens when 802.11n is enabled, thoug. So when I disable it with modprobe, everything is all good and fine. When I boot into Windows 7, 802.11n works perfectly fine from there.

Any ideas on why? Are the iwlwifi drivers still unstable when it comes to 802.11n, or what? :(

Hardware info:

       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-23-generic firmware=18.168.6.1 ip=192.168.10.184 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:f4900000-f4901fff

I'm on a Lenovo Thinkpad T430. Bought in January.

---

### Post by sanderj on 2013-06-14
If you can remotely crash a router, it's a bug in the router. Did you contact your ISP or router reseller ... oh, wait: Zyxel ... nice products, but no support at all: what you have is what you get (WYHIWYG)

That means: use a workaround (assuming you already update the Zyxel firmware)

---

### Post by karlstad on 2013-06-14
I am in touch with my ISP regarding the router. I don't have the rights to update the firmware, and I sort of hope it's a firmware bug rather than a Linux bug.

It's just weird that it only happens with Ubuntu and not when using Windows.

---

### Post by sanderj on 2013-06-16
> **karlstad said:**
> 
It's just weird that it only happens with Ubuntu and not when using Windows.

Hardware manufacturers often only test against mainstream, so Windows. 

EDIT:

And, after the deal is done, there's no financial drive anymore to improve / bug-fix anything.

---

