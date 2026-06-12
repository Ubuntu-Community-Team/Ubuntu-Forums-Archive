---
title: "I need to disable my integrated Ethernet device .what should i do ? eth0 permanently"
date: 2013-03-10
forum: Networking &amp; Wireless
---

### Post by jakkamgirish on 2013-03-10
I need to disable my integrated Ethernet device .what should i do ? eth0 permanently  . please tell me how to enable it in case if anything goes wrong :)

---

### Post by steeldriver on 2013-03-10
You could blacklist the driver (if you have no other devices that use the same driver). Or if you are using network-manager, mark it as an unmanaged-device using the device MAC.

The best option will depend on what version / flavor of Ubuntu you are running, and exactly why you want to disable the device.

---

### Post by Cheesemill on 2013-03-10
There may well be an option to disable it in your computers BIOS, I have that option on several of my machines.

---

### Post by mirearts KING SUNNY on 2013-03-10
BIOS: (if available) pheripherals > internal modem or LAN : SET TO DISABLE

or inside Ubuntu's network manager, delete the auto ethernet and deselect auto...

---

