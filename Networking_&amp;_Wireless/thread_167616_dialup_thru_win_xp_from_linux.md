---
title: "dialup thru win xp from linux?"
date: 2006-04-28
forum: Networking &amp; Wireless
---

### Post by StuartZ on 2006-04-28
How do I set my ubuntu box to access the dialup connection on my XP box?I have internet connection sharing enabled on my XP and have the two connected thru a router.  I am able to share files thru SMB, but have not been able to find any help in a couple of forums on the dialup issue.  --Newbie

---

### Post by Slim Odds on 2006-04-28
Is your linux box set to use DHCP? If not, you need a static IP address and to set your default gateway to use the windows machine. This is typically 192.168.0.1

If you use DHCP, it should set that up for you automatically.

You may also want to enable "On Demand" dialing for the dialup adaptor. Or maybe not.

---

### Post by StuartZ on 2006-04-28
I set my default gateway to 192.168.2.123 (XP's ip address) and got a timed out error on the browser.  I redid setting up a network on the XP to enable others to connect thru it, disabled the 3rd party firewall, the XP's firewall was automaticly enabled when setting up network, and still have the same problem.  I can ping 192.168.2.123 from the linux box, but cannot get to the internet.

---

### Post by Slim Odds on 2006-04-29
[quote=StuartZ]I set my default gateway to 192.168.2.123 (XP's ip address) and got a timed out error on the browser. I redid setting up a network on the XP to enable others to connect thru it, disabled the 3rd party firewall, the XP's firewall was automaticly enabled when setting up network, and still have the same problem. I can ping 192.168.2.123 from the linux box, but cannot get to the internet.[/quote] 
When you enable Internet Connection Sharing on Windows XP (or 2k), it forces your ethernet port to address 192.168.0.1

If yours is something else, then either you don't have ICS enabled or you somehow have it forced to another address. You need to check your setting again.

Note that ICS also enables a DHCP server on the WIndows box that will allow your linux machine get it's IP address and gateway from DHCP.

---

### Post by StuartZ on 2006-04-29
[QUOTE=Slim Odds]When you enable Internet Connection Sharing on Windows XP (or 2k), it forces your ethernet port to address 192.168.0.1

If yours is something else, then either you don't have ICS enabled or you somehow have it forced to another address. You need to check your setting again.

Note that ICS also enables a DHCP server on the WIndows box that will allow your linux machine get it's IP address and gateway from DHCP.[/QUOTE]


Thank you for your replies.  I got to go to work now. I will try 192.168.0.1 later.

---

### Post by StuartZ on 2006-05-06
I have my windows box set at the 192.168.0.1 with internet sharing with dhcp enabled on both my Linux and Win boxes but the Linux is having problem finding the proxy connection automaticaly.   I can manually set the address, but what sould the port be.

---

