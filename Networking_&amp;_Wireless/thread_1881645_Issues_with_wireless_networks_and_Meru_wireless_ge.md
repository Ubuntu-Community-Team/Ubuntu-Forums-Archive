---
title: "Issues with wireless networks and Meru wireless gear?"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by Roasted on 2011-11-15
I've been tinkering around with newer releases of Ubuntu lately. We're currently running an array of 11.04 machines without any issue. I fired up 11.10 on my machine and noticed one of our buildings acting weird. After some pinpointing, this is the basic synopsis of what we're seeing (I'm noting the desktop environment with each listing since I was seeing slightly different results on each):

[LIST]
[*]Ubuntu 11.10 - Unity - Wireless networks simply never show up in network manager.
[*]Ubuntu 11.10 - Gnome Shell - Wireless networks either don't show, or often come up as "unknown" in the SSID.
[*]Ubuntu 11.10 - Unity - Going through network settings to manually connect to the SSID works fine.
[*]Ubuntu 11.10 - Gnome Shell - Going through network settings to manually connect to the SSID works fine.
[*]Fedora 16 - Gnome Shell - Simply never shows any SSIDs within this particular building at all.
[/LIST]

Other notable facts:
[LIST]
[*]Fedora 16 - Linux 3.1.x.x Kernel
[*]Ubuntu 11.10 - Linux 3.0.x.x Kernel
[/LIST]

This was tested on a Lenovo Thinkpad with a Realtek wireless card as well as a Toshiba laptop with an Atheros wireless card. 

The only other common denominator is the fact we're using Meru wireless in this building these issues exist at. In other buildings where we're utilizing Aruba, the issue is not seen. I don't see the issue in any other areas either, such as at home with a standard Linksys router, Motorola router, Netgear router, etc. 

Considering previous versions of Ubuntu worked fine and the newest one is acting up, along with Fedora 16, I have to wonder if it's a kernel issue since both distros are 3.0 or 3.1. Coupled with the fact we've tried different laptops and two different wireless card, it kind of points in that direction.

Has anybody else seen this and/or heard of a fix?

---

