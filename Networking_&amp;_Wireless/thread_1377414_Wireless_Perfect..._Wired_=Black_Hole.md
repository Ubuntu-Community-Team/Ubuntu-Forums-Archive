---
title: "Wireless Perfect... Wired =Black Hole"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by cavan on 2010-01-10
Ok, Like everyone that posts on this forum, I am a complete newbie when it comes to ubuntu.   I was finally tired of vista locking up and decided to scrap it and load ubuntu 9.10.  Overall it is awesome.   Wireless works perfectly, no video card issues 10000 times faster than vista, the best solution I ever did.  But for some reason when I plug a network cord in and turn off wireless I have no connectivity.  I have a Toshiba Satellite a205-s5800 and it seems like there is no clear area to find out information on it.
 
Any ideas?

---

### Post by adam814 on 2010-01-10
A little more information might help.  Could you post the output of "sudo lshw -C network"?

---

### Post by cavan on 2010-01-10
*-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:9d:dc:81
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=half firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: irq:30 memory:f0000000-f0003fff ioport:2000(size=256)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:9b:24:9e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.201 multicast=yes wireless=IEEE 802.11bg


Wireless works fine... but wired network will not connect

---

### Post by adam814 on 2010-01-10
Hmm...nothing too weird there.  How about the output of "ifconfig eth0" and "route -n"?

---

### Post by cavan on 2010-01-18
brad@brad-laptop:~$ ifconfig eth0
  eth0      Link encap:Ethernet  HWaddr 00:a0:d1:9d:dc:81  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:16
    brad@brad-laptop:~$ route -n
  Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
  192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
  169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
  0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by cavan on 2010-01-18
still for some reason the network cables do not connect me to the internet, just wireless... I have tried the stupid stuff like switching network cables and ports on the switch and still nothing.

---

### Post by adam814 on 2010-01-18
For starters you don't have an IP address on your eth0 interface.  Are you using DHCP or static IP on your network?  How are you connected exactly?

---

### Post by Iowan on 2010-01-18
Check Network Manager applet - there should be an "auto eth0" or something similar. See if it is set to "Connect automatically". 

Another option would be to try (from a terminal): ```
sudo dhclient eth0
```

---

### Post by cavan on 2010-01-18
I attach through a normal DHCP router.  I have one workgroup switch connected to a Wireless Router to a cable modem.

When I do: dhclient eth0
I get:

Internet Systems Consortium DHCP Client v3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhcpclient.leases:  Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

---

### Post by adam814 on 2010-01-18
You have to run dhclient as a superuser.  Try:
```
sudo dhclient eth0
```

---

### Post by cavan on 2010-01-18
Ok doing dhclient eth0   gets me this:


Internet Systems Consortium DHCP Client V3.1.2
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
   
  Listening on LPF/eth0/00:a0:d1:9d:dc:81
  Sending on   LPF/eth0/00:a0:d1:9d:dc:81
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
  No DHCPOFFERS received.
  No working leases in persistent database - sleeping.

---

### Post by adam814 on 2010-01-18
Well, you're definitely not getting an IP assigned from the router.

Have you tried connecting directly to the router to eliminate a switch fault as the problem?  Sometimes they do fail or act just erratically enough to cause trouble.

If you still can't get an IP from your router after connecting directly to it and power-cycling the router we can go from there (probably running wireshark on the interface and seeing what's going on with your network traffic).

---

### Post by cavan on 2010-01-19
I have tried to plug the laptop directly into the router, and the cable modem in ports that I know work.  I have also tried different network cables, and 3 different networks and still I can not get the wired connection to work.   Wireless works great, but thats it.

---

### Post by adam814 on 2010-01-19
If wireless works great I suppose that rules out router or cable modem failure and using different cables probably rules out a bad cable.

Could you post the output of "dmesg"?

---

### Post by cavan on 2010-01-26
That is way too long to post.

---

### Post by adam814 on 2010-01-26
> **adam814 said:**
> If wireless works great I suppose that rules out router or cable modem failure and using different cables probably rules out a bad cable.

Could you post the output of "dmesg"?

Sorry for the confusion.  I just meant the last 10 lines of it or so.

---

