---
title: "NIC works in Fedora, not in Ubuntu"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by lyam_kaskade on 2005-12-28
Alright, very strange problem. 

Network Card: Marvell Yukon Gigabit Ethernet Controller
Wireless Card: Intel/Pro Wireless 2200 802.11B/G LAN Card
Asus Z71V

I have three partitions setup: Ubuntu Breezy, Fedora Core 4, and Windows XP

I started with Ubuntu. The network card worked fine. After installing Fedora Core 4, the network card worked in Fedora.
Then when I reboot into Ubuntu, I can no longer get a DHCP lease. Windows XP tells me that a network cable is unplugged.
Upon rebooting into Fedora, the card works fine again (I am posting from Fedora atm).

To make the situation more confusing, I can fix the problem by connecting to a wireless network. Afterwards the Network Card works in Ubuntu again. 
Unfortunately, I no longer have a wireless network to connect to.

The network here consists of a D-Link router attached to my laptop and my sister's desktop computer running Windows XP. Please ask if any additional information is required.
Thanks.

---

### Post by darth_vector on 2005-12-28
in the file /etc/network/interfaces do you have two lines like

```
auto eth0
iface eth0 inet dhcp
```

?? if not, you should.

can you post the output of:

```
route -n
ifconfig
cat /etc/network/interfaces
```

---

### Post by lyam_kaskade on 2005-12-28
cat /etc/network/interfaces:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp

route -n :
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface



ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:11:D8:EA:8E:29
          inet6 addr: fe80::211:d8ff:feea:8e29/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:184625 (180.2 KiB)  TX bytes:184625 (180.2 KiB)


Those were for Ubuntu.
Here are the results in Fedora:

no /etc/network/interfaces file

route - n:
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:11:D8:EA:8E:29
          inet addr:192.168.0.116  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feea:8e29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:965 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:746375 (728.8 KiB)  TX bytes:142630 (139.2 KiB)
          Interrupt:11 Memory:feafc000-0

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4415284 (4.2 MiB)  TX bytes:4415284 (4.2 MiB)

                          


---

### Post by darth_vector on 2005-12-29
ok. how many network cards are on the machine? if only one then you should get rid of the line that says

iface eth1 inet dhcp

then type do the following:

sudo ifconfig eth0 192.168.1.2
sudo route add default gw 192.168.1.1

and see if that works



if you have two network cards, then maybe eth1 is the one that is connected. this would explain why you are not getting an IP via DHCP. to correct this, add

auto eth1

or swap over the cable.

let us know how that goes.

---

### Post by lyam_kaskade on 2005-12-29
> then type do the following:

sudo ifconfig eth0 192.168.1.2
sudo route add default gw 192.168.1.1

and see if that works

Unfortunately, this doesn't work.

Also, I'm not sure if I made this clear, but eth1 is the wireless ethernet card mentioned in my first post.

---

