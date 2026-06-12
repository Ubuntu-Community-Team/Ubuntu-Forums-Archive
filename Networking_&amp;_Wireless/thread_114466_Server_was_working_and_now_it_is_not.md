---
title: "Server was working and now it is not"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by frantic211 on 2006-01-08
Hello,
I have a Counter Strike Server Installed on an old computer.  Everything was working fine until lastngiht I restarted it and then shut it down.  Today I cannot ping it or anything else on the network, although ALL other computers are working fine.

When I run mii-tool I get:
No MII transceiver present!

When I run ifconfig I get:
...
inet6 addr: fe80::fdff:ffff:feff:ffff/64
...

I cannot ping anything including the loop back (127.0.0.1).

I looked at a lot of different forums and I have 2 computers on the network both have the same info in the configureation files.  The 2 comps are as follows: 
1.) Ubuntu Desktop - Everything works fine
2.) Ubuntu Server with ssh and the CSS Server installed and that it. - Everything did work fine until today.

I tried to reinstall ubuntu, but during the installation it said the DHPC could not be reached.  Both lights on the card and the router are on.

Whats the problem?
ANy help is great
Thanks,
Matt

---

### Post by cwaldbieser on 2006-01-08
[QUOTE=frantic211]Hello,
I have a Counter Strike Server Installed on an old computer.  Everything was working fine until lastngiht I restarted it and then shut it down.  Today I cannot ping it or anything else on the network, although ALL other computers are working fine.

When I run mii-tool I get:
No MII transceiver present!
[/QUOTE]

Well, based on the troubleshooter, I would say that Ubuntu thinks there is something wrong at the physical level.  Can you switch NICs with another computer to verify if the problem is with the hardware?

---

