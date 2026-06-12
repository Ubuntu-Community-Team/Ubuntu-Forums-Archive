---
title: "New Install, Can't get on internet"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by Cruton502 on 2009-07-30
Hey guys, new Linux user here.  I just did an install from the livecd and I can't connect to my router via ethernet.  The icon in the top right says that I'm not connected.  In the network tools it shows that I'm not getting an IP address (I have the ethernet setting to DHCP).  I logged into my router from a different machine and my router can see the ubuntu machine and it says that it has also assigned it an IP.  For some reason the ubuntu machine won't show that it has been assigned an IP.

I could really use some help please.

The LAN chip on my motherboard is a VIA VT6308.

Because I am new to Linux, please give me explicit instructions on what to do.  I know how to get to the terminal

---

### Post by lisati on 2009-07-30
When you click on the icon, are you able to select any network to connect to?

---

### Post by Cruton502 on 2009-07-30
I can click on "Auto eth0"  When I click on it, it shows the connecting animation for about a minute and then gives me a pop up window saying that I'm disconnected.  

I found a command in a similiar thread and here are the results of it.  I hope it helps:

```
derrick@oem-desktop:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: 190 Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 01
       serial: 00:30:1b:80:58:83
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:5e:c2:af:93:04
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

the "network DISABLED" line kinda stands out

---

### Post by Cruton502 on 2009-07-30
Here is another piece of code that might help:

```
derrick@oem-desktop:~$ dmesg | grep via-rhine
[ 1248.522782] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[ 1248.522795] via-rhine: Broken BIOS detected, avoid_D3 enabled.
```

---

### Post by Crafty Kisses on 2009-07-30
What are the results of the following?
```
route
```

---

### Post by Cruton502 on 2009-07-30
Here are the results:

```
derrick@oem-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
derrick@oem-desktop:~$
```

And that was it.

---

### Post by itsamebuddich on 2009-07-30
Hi Crouton, have you seen this posting in the forum?  This seemed to help this beginner user as well:

[http://ubuntuforums.org/showthread.php?t=1227471](http://ubuntuforums.org/showthread.php?t=1227471)

---

### Post by Cruton502 on 2009-07-30
> **itsamebuddich said:**
> Hi Crouton, have you seen this posting in the forum?  This seemed to help this beginner user as well:

[http://ubuntuforums.org/showthread.php?t=1227471](http://ubuntuforums.org/showthread.php?t=1227471)

I just took a look at it.  My router is connected to the internet (hence I'm able to post this).  My router can see the ubuntu box and the router reports that it has assigned the computer an IP, but in the 'network tools' app in ubuntu, it shows that it has not received an IP assignment

---

### Post by Loosewheel on 2009-07-30
This is some pretty crazy stuff.....I see a lot of people with similar problems.

Cruton502, did you try to Right Click on NetworkManager icon, (upper right), and see if 'Enable Networking' is checked? And the 'Edit Connections...', ?

---

### Post by Cruton502 on 2009-07-30
Ya, 'Enable Networking' is checked and I can click on 'Edit Connections.'

When editing the Auto eth0 connection, I have 'connect automatically' checked, MTU automatic, IPv4 settings are set to DHCP.

---

### Post by Loosewheel on 2009-07-30
What do you get when you run 'dhclient' in a terminal?

Run: sudo dhclient

---

### Post by Cruton502 on 2009-07-30
Here is what I get:

```
derrick@oem-desktop:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted
derrick@oem-desktop:~$ 
```

ummm, I do believe I'm logged in as administrator :)

---

### Post by Loosewheel on 2009-07-30
sorry 'sudo dhclient'

---

### Post by Cruton502 on 2009-07-31
Here is what adding sudo got me:

```
derrick@oem-desktop:~$ sudo dhclient
[sudo] password for derrick: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/86:e0:db:55:ad:8c
Sending on   LPF/pan0/86:e0:db:55:ad:8c
Listening on LPF/eth0/00:30:1b:80:58:83
Sending on   LPF/eth0/00:30:1b:80:58:83
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
derrick@oem-desktop:~$ 
```

---

### Post by Cruton502 on 2009-07-31
Guys, thanks for your help but I think I'll need to give up on this machine.  I tried to install WinXP on it to test out the ethernet (because I haven't used this machine in a while) and the computer would shut down at the beginning of the install.  The computer has done this to me a couple of times even when I'm in the bios settings.  I think the problem may have to be with my hardware.  I'll have to try out linux later when I get some more funds to try and fix the machine.

Thanks again for the support!

---

