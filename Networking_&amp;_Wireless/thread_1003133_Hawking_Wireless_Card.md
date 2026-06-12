---
title: "Hawking Wireless Card"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Mathurin1968 on 2008-12-05
I installed the Hawking wireless card with the RT73 drivers per this link --
[http://sudan.ubuntuforums.com/showthread.php?t=848445&highlight=hawking+hwug1](http://sudan.ubuntuforums.com/showthread.php?t=848445&highlight=hawking+hwug1)

However, when I restart it the wireless card doesn't work anymore and then when I run networking restart here are some of the errors I get --
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14


No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Unless I run the drivers all over again and reinstall the card it doesn't want to work.  

Any thoughts?

---

### Post by gedit on 2008-12-05
That is an interesting development. Actually, I believe that shouldn't even be happening. I would try to re-install and see what happens. If there is no DHCPOFFER and no lease information provided, then it's either the router's problem or it's your wireless card. Sorry I couldn't help further. :/

---

### Post by Mathurin1968 on 2008-12-05
When I try to reinstall I get the following error --SIOCSIFFLAGS: Operation not permitted

---

### Post by Mathurin1968 on 2008-12-05
Installing ndiswrapper seems to work!

---

