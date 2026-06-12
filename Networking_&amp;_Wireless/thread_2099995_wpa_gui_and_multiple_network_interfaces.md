---
title: "wpa_gui and multiple network interfaces"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by percivjr on 2012-12-31
I normally use the internal wireless card on my netbook but occasionally need to connect via ethernet or an external USB wireless card.

I've removed Network Manager and can switch between network interfaces via some crude scripts I've knocked up which use ifup/ifdown and then restart wpa_gui.

What I would really like to do is to be able to hotplug the ethernet or USB wireless card and use the "Adapter" dropdown on wpa_gui to select the network interface. But wpa_gui only ever seems to show the first interface from /var/run/wpa_supplicant.

Does anybody know if wpa_gui will work in this manner and, better still, can share the relevant working configuration.

Many thanks.

---

