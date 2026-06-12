---
title: "not getting an IP"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by chipperi on 2009-02-22
Please be patient I have been using Linux for 1 day. I am not up to par on the tech speak yet. 

I installed Umbuntu on an old Dell I had laying around. It seem to be working perfectly, with the exception that I cant seem to get an IP, so I can't connect. 

Apparently the system sees and has installed my NIC however I cant ping alpha or numeric addresses.

My Router sees the machine as it is showing it under dhcp clients.

I am baffled. Below is some info that you may be able to use. 

> 
dell@Dell:~$ ifconfig 
eth0
eth0
Link encap:Ethernet  HWaddr 00:06:5b:48:ab:ed          
UP BROADCAST MULTICAST  MTU:1500  Metric:1          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0          
TX packets:1 errors:0 dropped:0 overruns:0 carrier:1          
collisions:0 txqueuelen:1000           
RX bytes:0 (0.0 B)  TX bytes:60 (60.0 B)          
Interrupt:11 Base address:0x2800 


Heres what I get in network when I lshw

 
*-network
description: Ethernet interface
product: 3c905C-TX/TX-M [Tornado]
vendor: 3Com Corporation
physical id: c
bus info: pci@0000:02:0c.0
logical name: eth0
version: 78
serial: 00:06:5b:48:ab:ed                
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=3c59x latency=64 maxlatency=




A little fruther down there is this one as well.


*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: aa:22:06:ac:7a:d3
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Iowan on 2009-02-22
You won't offend anyone (worth offending) if you ask for more clarification of tech speak... sometimes it rolls off the keyboard unnoticed. What happens if you try **sudo dhclient** (from a terminal)?

Does the router show the machine as having an IP address?

---

### Post by chipperi on 2009-02-22
Here you go. and I was wrong. the router cannot see the dell. I was looking at the wrong thing.

> dell@Dell:~$ sudo dhclient
[sudo] password for dell: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/aa:22:06:ac:7a:d3
Sending on   LPF/pan0/aa:22:06:ac:7a:d3
Listening on LPF/eth0/00:06:5b:48:ab:ed
Sending on   LPF/eth0/00:06:5b:48:ab:ed
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.

No working leases in persistent database - sleeping.
dell@Dell:~$

---

### Post by bgates on 2009-02-22
That does seem intriguing.

In the router config, does anything look off about this client?

In the router config, are there any other clues?  For example, is the range of IP addresses large enough that it has an address left for this client after leasing to its other clients?  Usually, by default they have a range of about 254 addresses, but it's possible to manually limit it to only a few.

---

### Post by chipperi on 2009-02-22
there are 100 avalible IP adresses only 3 are used (my computer, wifes laptop, and the phone router.) I have all security features turned off. I even tested the patch cord to make sure it's good. Going to plug direct to the modem in a little while to see what happens.

Just for giggles I tried pinging 127.0.0.1 like you would in windows to see if the card responded and it did.

---

### Post by bgates on 2009-02-22
127.0.0.1 is for all operating systems :)

Plugging it direct to the modem will be a good start.  If that does not work and get your external IP from the cable company, then we need to troubleshoot the hardware.  Is the light on, on the network interface card?  Are any other operating systems still installed on this machine and do they get an IP if booted?  Do you have any other network interface cards lying around that you can try in the machine?  Do you have an icon on the top right of the panel that looks like two computers?  I believe that network card should be recognized, but if there is a problem with the driver then there are some downloads available for it.

If it does work plugged in to the modem but is not getting DHCP lease from the router, then it's just some communication problem between the Dell and the router.  Have you already tried to reboot the router and then reboot the Dell while it's wired to the router?

---

### Post by chipperi on 2009-02-22
What can I say other than DUH and DOH!!! The Pins in the nic are worn out and werent making contact with the cable. I had to hold the cable in a certian spot to get it to make contact. I am usually the Smart A$$ who asks "did you plug it in?"

---

