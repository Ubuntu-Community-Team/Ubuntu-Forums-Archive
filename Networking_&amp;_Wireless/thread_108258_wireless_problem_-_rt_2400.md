---
title: "wireless problem - rt 2400"
date: 2005-12-25
forum: Networking &amp; Wireless
---

### Post by cloudy2 on 2005-12-25
I have been trying for hours to get by wireless network to work consistantly
in 5.10. I have an RT 2400 PCI card. The system is dual boot with Windows XP. The wireless card is my only means to connecting to the internet through Linux - there is no other kind of connection available on this particular machine. The connection works perfectly, every time, on windows. Most of the time it does not work on Ubuntu. Every once in a while it will but there seems to be no reason why when it doesnt, which is most of the time. There is currently no security, I took it off on the router to simplify this problem. 

Ive checked [http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-07.0031507315/view?searchterm=Network%20settings](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-07.0031507315/view?searchterm=Network%20settings)
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto) and tried what they suggested without any luck. 



Here is the output of "sudo ifup ra0":

There is already a PID file /var/run/dhclient.ra.pid with pid 0 
Internet Systems DHCP client V3.02
Copyright Internet Systems Consortium
All rights reserved

For info, please visit (a website)

sit 0 unknown hardware address Type 776
sit 0 unknown hardware address Type 776
Listening on: LPF/(a MAC address)
Sending on: LPF/(same MAC address as above)
Sending on Socket/Fallback

DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 3
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 4
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 11
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 11
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 9
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 14
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 8
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 1
No DHCP offers recieved
No working leases in persistant database, sleeping.

---

### Post by ubuntu_demon on 2005-12-31
I moved this thread to the networking section. Please don't post questions in the customization forum.

---

