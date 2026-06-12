---
title: "Wake on Lan/Wan"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by theone964 on 2012-01-04
Hi i'm running a Ubuntu 10.10 box, and i'd like to turn it on remotely (through the internet).
I setup the box to work perfectly and it does when I send the WOL command from within the network, it doesn't matter if the pc has been off for 5 minutes or 5 hours. However when I try to send the WOL command from outside my network (cellphone's internet) the pc only turns on if it's recently been on (impossible to time, but works when i try within 5 minutes of turning it off).

So my issue is; Why is my PC only able to Wake-on-Wan when it's recently been turned off. I'd like to be able to turn if on from anywhere in the world at anytime not just 5 minutes from when it's been off.

The mobo i'm using is Biostar TA890GXB-HD if that helps or makes a difference.

Thank You

---

### Post by Lars Noodén on 2012-01-04
Wake-on-LAN generally does not work outside your local area network.  Can you use your router as a stepping stone and launch WOL from it instead?

---

### Post by theone964 on 2012-01-04
My Buffalo WZR-HP-G300NH router has a WOL feature that I can to turn on my pc but I would like to be able to do it without using the router. That way i can turn on my pc with 1 click from my Droid X using the "WoL Wake on Lan Wan" app

---

### Post by iditude on 2012-01-06
I had that problem before. It's related to the ARP table on your router... Basically, your router stores the IP and MAC addresses of everyone on your network. But that table is usually refreshed after 5/10mn. The only way would be to force your router to keep record of your machine (you can do that with custom firmwares like dd-wrt, see here: [http://www.dd-wrt.com/wiki/index.php/WOL](http://www.dd-wrt.com/wiki/index.php/WOL))

Also, you can try forwarding port 9 (UDP) not to your internal IP (like 192.168.1.XXX) but to the broadcast address (i.e. 192.168.1.255). Please note that it's rare that a router will allow you to do that...

Hope this helps

Best

EDIT: just checked, your router seems compatible with dd-wrt: [http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)

---

