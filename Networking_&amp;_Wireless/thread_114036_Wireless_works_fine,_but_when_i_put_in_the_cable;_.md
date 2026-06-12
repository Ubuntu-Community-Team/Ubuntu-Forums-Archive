---
title: "Wireless works fine, but when i put in the cable; nada"
date: 2006-01-07
forum: Networking &amp; Wireless
---

### Post by stiankarlsen on 2006-01-07
Here's the deal, on my HP laptop, I have a wireless cards, which detects the signal from our router immediatly, and connects just fine to the net, but when I take a cale from the same router, and put it into the laptop, it just wont connect to the internet..

any idea on how to solve this?

---

### Post by harisund on 2006-01-07
What exactly do you mean it won't connect to the internet? Does the wireles stop working? How do you go about configuring it? 

If you are currently on wireless and want to switch to wired, there are some commands you can use. Lets assume you have wlan0 as your wireless device and eth0 as your ethernet device. And you are currently connected to the wireless. In order to switch of wireless and move to wired, I would try

ifconfig wlan0 down
ifconfig eth0 down
ifconfig eth0 up
dhclient eth0

If what I said didn't make any sense to you, please do post so, and I will walk you through what you want.

---

### Post by stiankarlsen on 2006-01-07
I get this from dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 17182
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:0f:b0:05:be:46
Sending on   LPF/eth0/00:0f:b0:05:be:46
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.20.32.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


no go

need some more help, thank you

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=stiankarlsen]I get this from dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 17182
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:0f:b0:05:be:46
Sending on   LPF/eth0/00:0f:b0:05:be:46
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.20.32.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


no go

need some more help, thank you[/QUOTE]

Did you try the steps in the wired Ethernet troubleshooter?
[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")

---

