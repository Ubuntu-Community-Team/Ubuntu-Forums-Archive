---
title: "Intel Pro WIreless 3945 not working since 11.04 upgrade"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by Nubnut on 2011-04-30
When I attempt to connect through wireless it tries to connect then eventually gives "Wireless Connection now disconnected" message.

Output from lspci is:

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
        Subsystem: Dell Device 0201
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at efcf0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Intel Corporation Device 1021
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945

Any help with this greatly appreciated

Ronan

---

### Post by johnbuck on 2011-05-01
I have the same network hardware as you, similary also stopped working after upgraded to 11.04. For me is under NetworkManager indicate Device is not managed. The solution that works for me is 
[http://www.accretionlogistics.com/](http://www.accretionlogistics.com/)
Ubuntu 11.04 – Fix the Wireless “Device Not Managed”

---

### Post by Nubnut on 2011-05-04
Hi John,
I've just checked the network Manager.conf as you suggest and it was set to managed: false.

I've edited and resaved it and am now rebooting,...

Hoping this works....

And it does!!!! Thank you so much John.

Incidentally, you may be able to help me with another issue related to networking. I'm managing a large number of school Laptops running 10.04 LTS. These laptops were imaged from one base unit using clonezilla. I'm finding that some of these machines connect ok to the wifi network but then loose their ip addresses and will only reconnect on reboot,.... andy ideas??

Someone mentioned that there may be a conflict arising from the boot-up hardware probe creating a duplicat instance of the wifi card but am not sure where to start looking..

Thanks so much for your help John.

Ronan

---

