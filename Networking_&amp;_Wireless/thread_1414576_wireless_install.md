---
title: "wireless install"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by ESimard on 2010-02-23
Hi, absolute ubuntu newbe here.  I want to install a D-Link DWL-G122 rev A2 wireless USB adaptor.  The adaptor does connect to the router correctly on other Windoes machines.  From this I assume the router and adaptor are ok.  

Using ubuntu 9.10 I plugged the adaptor in and got a connection message saying it was connected to the router.  Looking at the "connection information" the ip address is way out of line, as if DHCP didn't set them correctly.

How do I proceed from here to find the problem?
Thanks in advance
_Ernie

---

### Post by mörgæs on 2010-02-24
How does the connection work with wire?

---

### Post by ESimard on 2010-02-24
Wire connection works perfectly.  No encryption is enabled only MAC address filtering and I say the adaptor does connect correctly with a Windoze machine, so I assume the router and the adaptor are configured correctly.
_Ernie

---

### Post by mörgæs on 2010-02-24
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by ESimard on 2010-02-24
Thanks that pointed me in the right direction.  All I had to do was change the Mode in the connection manager from AdHoc to Infrastructure.

---

