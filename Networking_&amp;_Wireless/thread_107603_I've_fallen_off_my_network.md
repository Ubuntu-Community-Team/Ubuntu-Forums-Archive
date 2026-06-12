---
title: "I've fallen off my network"
date: 2005-12-23
forum: Networking &amp; Wireless
---

### Post by dc2447 on 2005-12-23
Hi - yesterday my workstation at home fell of the network.  It was configured to use a static IP on the onboard SIS NIC.  After several reboots etc I reconfigured eth0 to use dhcp, still no luck with getting an IP.

In a final act odf deperation I ended up adding two new PCI NICS but Ubuntu doesn't like those either.

Have tried different cables etc but no luck.  Any suggestions? 

> davidcam@vader:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:0b.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
0000:00:0c.0 Ethernet controller: Yaskawa Electric Co.: Unknown device 0885 (rev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
davidcam@vader:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:5B:A8:91:02
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:279 dropped:0 overruns:0 frame:562
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:7560 (7.3 KiB)
          Interrupt:19 Base address:0xd400

eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1219 (1.1 KiB)  TX bytes:1219 (1.1 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

davidcam@vader:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
auto eth0

iface eth1 inet dhcp
davidcam@vader:~$ sudo dhclient eth0
Password:
There is already a pid file /var/run/dhclient.pid with pid 8869
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:11:5b:a8:91:02
Sending on   LPF/eth0/00:11:5b:a8:91:02
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by bscbrit on 2005-12-24
Well, for one thing it didn't find any DHCP!

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

is that the address of your DHCP - 255.255.255.255?

The hardware address for eth1 looks highly suspicious 00:00:00:00:00:00!

Have you tried starting from scratch using a guide such as this one?
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-ing](http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-ing)

Check that your NIC is recognise and the driver is installed.  
Give it an IP address.  Either fixed (my preferences on small systems) or DHCP.
See if you can ping your NIC
See if you can ping your gateway
Set up DNS
Set if you can ping [www.google.com](www.google.com)
You're good to go.

---

### Post by bscbrit on 2005-12-24
By the way, if you have a firewall I'd switch it off until you have got your network running - I've made that mistake a few times!

---

### Post by dc2447 on 2005-12-24
Sorry, perhaps I wasn't clear.

My onboard car was working fine as appears to be recognised by the kernel, the latter two nics aren't recognised which is very strange as they are Linksys and netgear NIC's that I have used under Redhat on a 2.4 kernel.

---

### Post by Lambert on 2005-12-24
With your nic in run this command

sudo lshw -C network

You should get output like this.

*-network DISABLED
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:02:8a:29:46:9c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       [B]configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10


[/B]The configuration line, want to check to see if a driver is loaded to the device. If not it won't have the driver= part in the line.

---

### Post by dc2447 on 2005-12-24
Thanks Lambert - output below
> 
davidcam@vader:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: 91
       serial: 00:11:5b:a8:91:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sis900 driverversion=v1.08.08 Jan. 22 2005 duplex=full link=no multicast=yes port=MII speed=100MB/s
       resources: ioport:d400-d4ff iomemory:cffdc000-cffdcfff irq:19
  *-network:1 DISABLED
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 00
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=off broadcast=yes driver=natsemi driverversion=1.07+LK1.0.17 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: Yaskawa Electric Co.
       vendor: Yaskawa Electric Co.
       physical id: c
       bus info: pci@00:0c.0
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list


---

### Post by Lambert on 2005-12-24
Did you set up the sit0 interface and do you use this?

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by dc2447 on 2005-12-24
[QUOTE=Lambert]Did you set up the sit0 interface and do you use this?

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/QUOTE] No, it must have been configured by the installer.

When I installed Kubuntu the onboard NIC was detected fine, I gave it a staic IP address and it worked well until this week but now it won't even DHCP

---

### Post by Lambert on 2005-12-24
try this

```
sudo ip tunnel del sit0
```

now see if you can get your network working again.

---

### Post by dc2447 on 2005-12-24
[QUOTE=Lambert]try this

```
sudo ip tunnel del sit0
```

now see if you can get your network working again.[/QUOTE]

ioctl: Operation not permitted

---

### Post by bscbrit on 2005-12-24
Lambert, I hope you don't mind me lurking, I'm learning as much as the OP on this one. Thanks

---

### Post by Lambert on 2005-12-24
I'm getting ready to sign off . I currently believe the first thing that needs to happen is to get rid of  sit0 interface. (It will always show up when running ifconfig but it should be no data after or underneath it) You can google around for sit0 using surrounding keywords such as delete interface, bring down sit0, remove sit0 etc...

---

### Post by bscbrit on 2005-12-24
i have already googled - most enlightening.  Thanks again and season's greetings.

---

### Post by dc2447 on 2005-12-24
[QUOTE=Lambert]I'm getting ready to sign off . I currently believe the first thing that needs to happen is to get rid of  sit0 interface. (It will always show up when running ifconfig but it should be no data after or underneath it) You can google around for sit0 using surrounding keywords such as delete interface, bring down sit0, remove sit0 etc...[/QUOTE]

Well I am back online.  I tried booting the system using a Live Kubuntu CD, I ended up with basically the same config albeit without the sit0 but no IP.

I then rebooted the system again and magically it *just works* - even with a sit interface.

I suspect this workstation is flakey.

---

### Post by bscbrit on 2005-12-24
I'm pleased to hear that it has been resolved.  I'm sorry that my help earlier on was not up to the mark - but I have learned from this thread and I have made notes to help me in the future.  Its a pity, though, that we might never know why the fault occurred, but I'm sure that you will be content with not knowing providing your system is working.

---

### Post by dc2447 on 2005-12-24
I suspect that there was a hardware issue rather than a debian issue, what concerns me more is the fact that Ubuntu didn't recognise the pci cards I added and that in general debian networking is a lot less clear than redhat based distro's

---

