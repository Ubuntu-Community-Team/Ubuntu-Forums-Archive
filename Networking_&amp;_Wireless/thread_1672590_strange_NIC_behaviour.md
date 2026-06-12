---
title: "strange NIC behaviour"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by kevinwincott on 2011-01-21
Hi

When I turn my PC on and login there is no network connection, ifconfig only shows the loopback interface, lspci shows the hardware. If i restart networking via /etc/init.d/networking restart the connection doesnt come back. If i restart the PC then all is OK.

What would cause this behaviour?

---

### Post by grahammechanical on 2011-01-21
What do you mean?

> there is no network connection

Do you see a network manager icon? Have you set your connection to Automatically Connect? Your wireless adapter could be switched off either by software or in hardware. Is Network Manager in the list of Startup Applications?

Regards.

---

### Post by kevinwincott on 2011-01-24
Hi

This is a wired connection, I see the icon but it has the red ! through it, when I click to configure an interface there are non listed. If I reboot the machine the interfaces are listed OK. Network manager is in the list of startup applications

---

