---
title: "Wired network problem: Intel 82579V on Intel Cold Lake DH67CL"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by -=DD=- on 2011-03-21
Hi to All.

I have new installation of Ubuntu 10.04 LTS.
Network (wired) is not working.

```



student@student-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4a (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
03:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)

student@student-desktop:/etc/network$ lshw -c net
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:fe500000-fe51ffff memory:fe528000-fe528fff ioport:f080(size=32)

student@student-desktop:/etc/network$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)




```

as i understand OS doesn't see the Ethernet adapter.
i was already [here]("http://ubuntuforums.org/showthread.php?t=1635325") and updated my BIOS- it doesn't help :(
What should i do? (except running in circles ?)

---

### Post by -=DD=- on 2011-03-22
Last thin which i did was editing /etc/network/interfaces
 i added: 
```
auto eth0
iface eth0 inet dhcp
```

```
student@student-desktop:/etc/network$ sudo /etc/init.d/networking restart
[sudo] password for student: 
 * Reconfiguring network interfaces...                                                                                                                       Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
```

HELP!

---

### Post by -=DD=- on 2011-03-22
Solved [here]("http://forums.fedoraforum.org/showthread.php?t=257676") by installing [this]("http://sourceforge.net/projects/e1000/files/e1000e%20stable/1.2.20/")

---

### Post by Michi Müller on 2011-08-12
Hi guys,
 
I have the same problem. The PCI network adapter is working but not the one on the mainboard.
 
```
michael@server:/$ sudo lshw -c net
[sudo] password for michael:
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:fe700000-fe71ffff memory:fe727000-fe727fff ioport:f060(size=32)
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:00:cb:62:0b:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.178.200 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:e000(size=256) memory:fe600000-fe6000ff
michael@server:/$

```
 
I tried to install the driver from your link ([http://forums.fedoraforum.org/showthread.php?t=257701](http://forums.fedoraforum.org/showthread.php?t=257701)), but it still doesn't work. Is there anything i can post to get a hint to solve my problem?
 
Regards...

---

### Post by shrikel on 2011-10-09
Worked great for me, thanks.

@Michi - did you update [e1000]("http://sourceforge.net/projects/e1000/files/e1000%20stable/8.0.30/") too, as the README instructs?

---

### Post by mouseclone on 2012-01-05
> **-=DD=- said:**
> Solved [here]("http://forums.fedoraforum.org/showthread.php?t=257676") by installing [this]("http://sourceforge.net/projects/e1000/files/e1000e%20stable/1.2.20/")

This worked like a champ. 

Save
Extract
cd to src dir in term
make install
modprobe -r e1000e; modprobe e1000e

Now, how do we get this into bug tracker to get this working in the 12.04 release.

---

### Post by hariharangopal on 2012-08-19
Ya its working fine for me... I have DH67CL and installed Ubuntu 12.04... I have no problem in it... When compared to Windows, browsing is fast in Ubuntu 12.04

---

