---
title: "Dynamic ip assigned when not needed"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2009-03-13
I have 4 pcs running from a Dlink g406T-router.
Number 1 (Ubuntu Intrepid) is used for mythtv and general internet use - wired connection.
Number 2 (Ubuntu Intrepid) is used solely for email - wired connection. 
Numbers 3 and 4 are netbooks (Xbuntu Intrepid) - wireless connected.

All use WICD instead of network manager.

I occasionally had problem with mythtv due to dynamic ip changing, so I decided to make 1 and 2 use static ip 192.168.1.2 and 192.169.1.3 and limited dynamic ips to range 192.168.1.10 to 192.169.1.20.

This solved all problems.

However I have noticed that a pc with a static ip is also assigned a dynamic ip. When all four pcs are on, the ips assigned are typically as follows
      PC 1 static 192.168.1.2
      PC 2 static 192.168.1.3
      PC 3 dynamic 192.168.1.12
      PC 4 dynamic 192.168.1.13
with 192.168.1.10 and 192.168.1.11 being assigned to the 2 static pcs.

Can someone explain why these duplicates exist.

---

### Post by theozzlives on 2009-03-13
are you using your router as DHCP?

---

### Post by peterthewolf on 2009-03-13
Yes router has both static and DHCP I assume DHCP is needed to deal with any laptops visiting including our own.

---

### Post by theozzlives on 2009-03-13
you sure you have the MAC right?

---

### Post by peterthewolf on 2009-03-13
Thanks Ozz for quick help.

Due to a power cut a few minutes ago the problem has cured itself and the duplicate dynamics have gone.

The router had never been switched off before so I guess that the router was trying to do what it used to do. Not a very scientific answer I admit.

---

