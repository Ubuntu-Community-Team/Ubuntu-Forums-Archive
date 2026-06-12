---
title: "HP Mini Wireless Support in 9.10"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by Crath on 2009-12-07
I see that a lot of people are having problems with this, and was hoping somebody might be able to point me in the right direction to help get mine fixed as well.  Neither my wired or wireless connections work since i did a fresh install of 9.10 desktop.  9.04 worked fine for both.  HP mini 1100.  I see people asking for "lshw -C network" and "sudo /sbin/ifconfig" so here is mine, right off the bat.

```
shane@minishane:~$ sudo lshw -C network
[sudo] password for shane: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:25:b3:41:6c:04
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)
```
```
shane@minishane:~$ sudo /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:b3:41:6c:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

Thanks sooo much! I will finally be able to do work again :P
ps: I open sys -> admin -> hardware drivers, and there are no drivers on the list

---

### Post by uncaspi on 2009-12-08
Please post the contest of

/etc/udev/rules.d/70-persistent-net.rules

since you wireless card didn't show up in /sbin/ifconfig

also please post contest of /etc/network/interfaces

Your wired connection should work if you run dhclient eth0

---

### Post by uncaspi on 2009-12-08
Also look in lsmod to see if your drivers are loaded. If not do sudo modprobe <your driver>

Restart networking sudo /etc/init.d/networking restart and use network manager to connect

---

### Post by Crath on 2009-12-08
> **uncaspi said:**
> Please post the contest of

/etc/udev/rules.d/70-persistent-net.rules

since you wireless card didn't show up in /sbin/ifconfig

also please post contest of /etc/network/interfaces

Your wired connection should work if you run dhclient eth0

/etc/udev/rules.d/70-persistent-net.rules```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:b3:41:6c:04", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

/etc/network/interfaces```
auto lo
iface lo inet loopback
```

which I changed to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

And then restarted networking, which didn't work. And, before I did that, I tried the command you suggested, but it kept searching 255.255.255.255 and never getting a dhcp response.

---

### Post by uncaspi on 2009-12-08
You should remove auto eth0 and iface eth0 inet dhcp again or else you could not use network manager.
Your wireless card doesn't show up in the rules file and you must probably edit it and assign eth1 or wlan0 to the MAC address of your card and then reboot to see the connections in network manager.

---

### Post by Crath on 2009-12-08
> **uncaspi said:**
> You should remove auto eth0 and iface eth0 inet dhcp again or else you could not use network manager.
Your wireless card doesn't show up in the rules file and you must probably edit it and assign eth1 or wlan0 to the MAC address of your card and then reboot to see the connections in network manager.

How can I get the MAC of the wireless, if I cant find it? I don't see it on any labels on the computer itself.

also, do you have any keywords i can search for or links to examples of how to add something, such as eth1 or wlan0 to my rules file? thanks!

---

