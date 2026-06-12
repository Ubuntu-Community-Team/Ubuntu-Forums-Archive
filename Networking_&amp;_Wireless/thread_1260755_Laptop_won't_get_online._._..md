---
title: "Laptop won't get online. . ."
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by Clove7 on 2009-09-07
For some reason, I can't get wireless to work. It recognizes the card, as far as I'm concerned the driver is installed out of the box, here is the results of lspci -v | less
 
```

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
     Subsystem: Hewlett-Packard Company Device 135b
     Flags: bus master, fast devsel, latency 0, IRQ 2299
     Memory at d4000000 (32-bit, non prefetchable) [size=4k]
     Capabilities: <access denied>
     Kernel drive in use: iwl3945
     Kernel modules: iwl3945

```It finds the networks fine, for some reason it just won't connect to them, and I don't know why.
 
When I click on the little wireless icon that's in the system tray, I can view the networks just fine. I changed the name off my router etc., it recognized it. I also removed the password, and just try to connect. . .but it won't. I'm not sure what else I have to do, I have no experience with using wireless in ubuntu :(.

---

### Post by Clove7 on 2009-09-07
Never mind, I FINALLY got it to work :).

---

### Post by dknezev on 2009-09-08
How did you get it to work, if you don't ming me asking coz I have a similar problem. I can view the wireless access point but I can't connect to it. 

Using Toshiba Satellite centrino with PRO/Wireless 2200BG ipw2200 driver.

---

### Post by Clove7 on 2009-09-08
> **dknezev said:**
> How did you get it to work, if you don't ming me asking coz I have a similar problem. I can view the wireless access point but I can't connect to it. 

Using Toshiba Satellite centrino with PRO/Wireless 2200BG ipw2200 driver.
Try removing the password at first, successfully connecting, and then adding the password back. For some reason, that did it for me. 
 
 
Now that I've got it working with gnome though, I installed KDE and switched over to it; and wireless won't work with KDE. Can anyone possibly help me out as to why it won't work with KDE but works with GNOME?

---

