---
title: "wireless loaded, but no internet"
date: 2006-02-07
forum: Networking &amp; Wireless
---

### Post by elp on 2006-02-07
As a new-b I used ndiswrapper to install my HP laptop wireless broadcon4306.
it shows it in system, admin, network with available wireless networks using I use SBC yahoo dsl (2wire.com) with wep key8300103966, when I activate the wlan0 I can not get connected to internet. route -n shows nothing.
when I use the wire connection all is OK. please help........thanks

---

### Post by jasmuz on 2006-02-07
Once your card is loaded did you try doing this?

$ sudo iwconfig wlan0 essid name_of_AP (the name you found by using iwlist wlan0 scan) 
$ iwconfig wlan0 enc <key> (fill out your WEP key (if you have one)) 
$ sudo dhclient wlan0 (gets a dynamic IP adress)

---

### Post by elp on 2006-02-07
thanks jasmuz for quick reply.

as a new-b I did this:

elp7@ubuntu:~$ sudo iwconfig wlan0 essid 2WIRE966
elp7@ubuntu:~$ sudo iwconfig wlan0 enc <8300103966>
bash: syntax error near unexpected token `-1'
elp7@ubuntu:~$ sudo iwconfig wlan0 enc 8300103966
elp7@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:5f:77:47
Sending on   LPF/wlan0/00:90:4b:5f:77:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
:-#

---

### Post by beowulf on 2006-02-08
I am having a similar problem:

Hardware:
    Dell Inspiron B120
    Dell 1370 Wireless card (Mini PCI, I think, Broadcom chipset)

OS: Breezy Badger 5.10

I'm using the Windows driver for the NIC with ndiswrapper.  I found that the version of ndiswrapper that I could get with apt-get didn't work, so I got the sources and compiled the latest version.  Now the wireless light on the laptop goes on (good!), the adapter (wlan0) appears in ifconfig and in the network pannel applet (good!), but I still cannot communicate using the wireless (bad).  

Doing a little more investigation, I found that the laptop is sending packets into the wireless ether and replys are being sent.  I can see them in a sniffer on the wireless network AND if I run tcpdump on the laptop I can see the dhcp requests and replys.

So it appears that the packets make it out, the replys come back, but for some reason they don't make it up the stack.  The behavior is the same if I configure a static IP address (except that it's not trying to get a DHCP lease).

Any help anyone could offer would be much appreciated.

---

