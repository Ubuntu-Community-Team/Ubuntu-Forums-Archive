---
title: "Belkin F5D8011 Notebook PCMCI Wireless Card Not Working"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by kgolfer on 2009-08-03
Hello,

I am bit new to linux and it's setup.  I have a new Belkin N1 MIMO notebook wireless card (Part# F5D8011), which I am trying to use to connect to my wireless network.  I have a linksys N wireless router, and I can easily connect using windows, but in Linux I am not having any luck.  I can view my network using KNetworkManager, but it doesn't connect.  I am using WPA2.  I have tried using WICD in place of KNetworkManage, and I can't even view any networks with it.  When I plug the card in, the power led turns on, and then within a second, it turns off.

Here is my lspci output:
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
        Subsystem: Belkin Device 8011
        Flags: bus master, 66MHz, medium devsel, latency 168, IRQ 18
        Memory at 84000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

I would really appreciate if someone could help.  Thanks.

---

