---
title: "Router/DHCP/Ethernet Woes"
date: 2005-02-14
forum: Networking &amp; Wireless
---

### Post by jmather on 2005-02-14
I recently installed Umbutu on my laptop (Compaq presario 1528).  For the life of me I can not get a DHCP address from my D-Link di-624 router.  My ethernet card is recognized and I get an active link on my router. I can ping localhost and I have tried using a static IP and this still does not work.

Next step I took an old computer with an old compaq nic and installed umbutu and I had the same problem.  (all of these connections have been made by wire)

If I do an ifup I get "no dhcp...." messages....

Has anyone else had troubles with this router? 

any suggestions?


thanks.....

---

### Post by Strider on 2005-02-14
Did you verify that your router is configured to give out a DHCP address?  Does DHCP work on any other operating system?  If you can assign a static IP, go ahead and see if you can ping any of your other network nodes... the dlink  or another workstation on the same LAN.

---

### Post by bob k on 2005-02-15
[QUOTE=jmather]I recently installed Umbutu on my laptop (Compaq presario 1528).  For the life of me I can not get a DHCP address from my D-Link di-624 router.  My ethernet card is recognized and I get an active link on my router. I can ping localhost and I have tried using a static IP and this still does not work.

Next step I took an old computer with an old compaq nic and installed umbutu and I had the same problem.  (all of these connections have been made by wire)

If I do an ifup I get "no dhcp...." messages....

Has anyone else had troubles with this router?

any suggestions?


thanks.....[/QUOTE]

You have to have a router that can act as a DHCP server on the lan side and if you are using retail broad band it has to be a DHCP client on the wan side to pick up the ISP config. Usually there is an option on the lan side to use the ISP DHCP defaults. Some have an option where you can config the options on the lan side to static address such as DNS servers which I use, as my isp's DNS is to far away and there are faster and closer DNS servers in my area on the metro ring I'm on.

Bob

---

### Post by jmather on 2005-02-15
Thanks for all of your comments....I figured it out...it was actually the ethernet cable.....LAME! :?   Anyways...sorry about that....but the strangest part about it is that the cable worked with Windows and an old Red Hat version (8.0).  Is there some kind of setting in newer Kernels that perhaps monitors packet loss on dhcp requests?

---

