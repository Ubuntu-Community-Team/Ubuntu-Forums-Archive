---
title: "Remove and Re-insert wireless card"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by Deedub on 2009-01-23
I have an AirCard that works fine if inserted before bootup. My problem is it is right next to my DVD drive and it overlaps the door. I have to remove the AirCard to access my DVD. When I re-insert the card it is not recognized. Is there a command I can run to re-initialize the card? Otherwise  have to reboot my system.

Thanks

---

### Post by Deedub on 2009-01-26
> **Deedub said:**
> I have an AirCard that works fine if inserted before bootup. My problem is it is right next to my DVD drive and it overlaps the door. I have to remove the AirCard to access my DVD. When I re-insert the card it is not recognized. Is there a command I can run to re-initialize the card? Otherwise  have to reboot my system.

Thanks
Sorry, am I in the wrong place? Is this a noob question?

---

### Post by puppywhacker on 2009-01-26
the question is not very common. And the problem can be anywhere.

you could try running
**/etc/init.d/networking restart**

This reconfigures the network interfaces, maybe the interface just looses its configurations

---

### Post by Deedub on 2009-01-27
> **puppywhacker said:**
> the question is not very common. And the problem can be anywhere.

you could try running
**/etc/init.d/networking restart**

This reconfigures the network interfaces, maybe the interface just looses its configurations
I ran that. No go. When I boot the device it's recognized before the "Reading files for boot" msg. The system sees it as ppp0. Was looking into if it is a hotplug issue but still have not been able to initialize while in the system. Any ideas? Thanks for the reply.

---

