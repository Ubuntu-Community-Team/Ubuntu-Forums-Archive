---
title: "network stopped working"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Gazoo2 on 2009-01-26
I had eth0 up and working running a server, I then installed a wireless card (pcmcia) and it seems to be working as my router see it, (WPA) but I am unable to TX/RX on it. As well my eth0 will not connect now. All my settings seem to be ok(I am rather new to linux).

When I type /etc/init.d/networking restart    I get an "invalid Argument"  
* stopping NTP server ntpd    

how would I begin to troubleshoot this if someone can help

Edit:   when I type "route -nee"  I get a 3 lines of info

192.168.1.0_______0.0.0.0 ..............
169.254.0.0_______0.0.0.0  ................
0.0.0.0___________192.168.1.1

I guess the first line should be  192.168.1.118  and the second line makes no sense and I think it shouldn't even be there, where would I edit this info and should my eth0 info be here as well if it was working?

---

### Post by Gazoo2 on 2009-01-26
this is the output from lshw -C ndiswrapper can anyone tell if the wireless card is set up right, I can see it logs on to the router but no traffic between the too

 *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:12:0e:08:5a:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+tnet1130 driverversion=1.52+Texas Instruments,06/17/200 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

