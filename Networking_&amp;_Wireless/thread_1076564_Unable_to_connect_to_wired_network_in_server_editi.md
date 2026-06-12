---
title: "Unable to connect to wired network in server edition"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by Defib on 2009-02-21
So I installed 8.10 sever edition on to my hp pavilion a320n and everything went smoothly until the part where it tried to DHCP to my router using a wired connection (I can do it wirelessly, but I want a hardline)

Here's how my network is set up

Modem -> Belkin F5D7230-4 v6000 -> Linksys NR041 4-Port Router -> HP a320n

If anyone can help me set up a wired connection that would be great! 

Ps. I have to work from 15-23 EST

---

### Post by Iowan on 2009-02-21
Post results of **ifconfig**. Contents of */etc/network/interfaces* file might be useful on server edition.

---

### Post by Defib on 2009-02-21
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:552 (552.0 B)  TX bytes:552 (552.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:09:5b:b4:1f:00  
          inet addr:192.168.2.150  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:feb4:1f00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:128893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:179601265 (179.6 MB)  TX bytes:3683240 (3.6 MB)
```



```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet static
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
        address 192.168.2.150
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1

```

When I do ifup eth0 this returns:
```

Ignoring unknown interface eth0=eth0.
```

---

### Post by Iowan on 2009-02-22
Add the following to your */etc/network/interfaces* file: ```
auto eth0
iface eth0 inet dhcp

```

---

### Post by Defib on 2009-02-22
```
sudo ifup eth0
eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
```

After added that to /etc/...

---

### Post by Iowan on 2009-02-22
Did you try **/etc/init.d/networking restart** after changing the file?

---

### Post by Defib on 2009-02-22
```
 * Reconfiguring network interfaces...                                          Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
 * if-up.d/mountnfs[wlan0]: waiting for interface eth0 before doing NFS mounts
eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                         [ OK ]
```

---

### Post by Iowan on 2009-02-23
Cabling issue?  Server doesn't seem to recognize eth0. Post results of **sudo lshw -C network**.

---

### Post by Defib on 2009-02-23
```
  *-network DISABLED      
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth1
       version: a1
       serial: 00:00:6c:4c:f7:d0
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:09:5b:b4:1f:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.150 multicast=yes wireless=IEEE 802.11-b
```

Then I did sudo ifup eth1

```
Ignoring unknown interface eth1=eth1.

```

in /etc/.... changed to eth1

sudo ifup eth1

```
Listening on LPF/eth1/00:00:6c:4c:f7:d0
Sending on   LPF/eth1/00:00:6c:4c:f7:d0
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

---

### Post by Iowan on 2009-02-23
Try **/etc/init.d/networking restart** again after changing */etc/networking/interfaces* to eth1.  I've seen threads where router refused to offer DHCP address - but don't remember most common solution.  One *potential* cause is MAC filtering by the router.

---

### Post by Defib on 2009-02-23
Hmmm, it still produced the same results. And there's no MAC filtering, I reset the router just to make sure.

PS - Thanks so much for the help!

---

### Post by Iowan on 2009-02-23
I did a forum search on "working leases" and found several threads.  One mentioned a bad connector (a cable could also be faulty), another mentioned firewall issues.  A third mentioned a router that just wouldn't play nice (or a router that had no available leases left). I doubt you've used up all leases in the address pool  - but wouldn't hurt to check.  Whist there, write down address pool range - in case you must resort to a static address.  Another option might be a static lease (handy for a server, anyway).  First, verify that the hardware (cables, router ports, etc.) are working.

---

### Post by Defib on 2009-02-23
Ok. Checked the Cables with my working laptop and it's all good. Booted up a livecd to check the hardware and that all checks out. So it's not the hardware.

Range
192.168.2.2
192.168.2.99

100 is already taken. 
I would like the server to be 192.168.2.150, as that's what all the ports are fowarded to.

---

### Post by Iowan on 2009-02-24
Does your router offer the option to set up static (fixed) leases?

---

### Post by Defib on 2009-02-25
Yes it does. I have one set up with my desktop (Vista for iTunes)

---

### Post by Iowan on 2009-02-26
Try setting up one for your server.

---

### Post by Defib on 2009-03-02
So I attempted to set it up just like my wireless, but with 192.168.2.151

then this came up...

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
SIOCDELRT: No such process
 * if-up.d/mountnfs[wlan0]: waiting for interface eth1 before doing NFS mounts


```

And lost all connections...

I'm rebooting it right now.


Ok I'm back in...

Here's the file
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet static
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
        address 192.168.2.150
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
auto eth1
iface eth1 inet static
        address 192.168.2.151
        netmask 255.255.255.0
        gateway 192.168.2.1

```

I tried a bunch of stuff, ended up that eth1 was changed to eth2...

changed it again in /etc/...

```
$ sudo ifup eth2
Ignoring unknown interface eth2=eth2.
```

And now it timed out again...

---

