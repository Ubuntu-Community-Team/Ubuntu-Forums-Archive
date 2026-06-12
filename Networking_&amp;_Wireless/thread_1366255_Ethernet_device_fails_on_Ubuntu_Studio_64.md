---
title: "Ethernet device fails on Ubuntu Studio 64"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by democritus74 on 2009-12-28
I am running a dual-boot machine with Ubuntu 9.10 32-bit & Ubuntu Studio 9.10 64-bit.  My network card is an on-board nVidia MCP55 ethernet chip, revision a2.

My Ubuntu 9.10 32-bit partition can access the internet.  My Ubuntu Studio 9.10 64-bit cannot.

Under Ubuntu Studio ifconfig lists just the loopback interface.  When I use the Network utility under System->Preferences I can see my current ethernet device listed.  When I press the "Configure" button for this device I get an error message stating the device does not exist.


I have run the System Testing tool, lsmod, lspci, and lshw on both partitions to find out any differences.  I noticed that for Ubuntu Studio 9.10 64-bit lshw lists the ethernet Bridge as disabled.

Can someone please help me find out why I cannot use the ethernet device under Ubuntu Studio 9.10 64-bit?  The same hardware works perfectly fine under Ubuntu 32-bit.

---

