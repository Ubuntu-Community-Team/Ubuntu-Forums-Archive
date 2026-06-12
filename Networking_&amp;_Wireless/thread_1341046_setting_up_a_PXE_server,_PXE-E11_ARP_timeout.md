---
title: "setting up a PXE server, PXE-E11: ARP timeout"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by wiresnips on 2009-11-29
I'm trying to get some flavor of linux installed on my old p1120. It's a very problematic machine to boot, so I'm setting up a PXE server (at least it can boot from there).

Started with a clean install of Ubuntu 9.04 and followed [these instructions]("https://help.ubuntu.com/community/PXEInstallMultiDistro"). Everything went smoothly, but the boot sticks with a "PXE-E11 ARP timeout" message and gives up.

Syslog shows DHCPDISCOVER, DHCPOFFER, DHCPREQUEST, DHCPACK to and from the right mac address.

Looking for thoughts, insights, some way to diagnose... I'm not good with networks, so I don't know how to proceed.

---

