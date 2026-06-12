---
title: "network-manager clobbering resolv.conf (again!)"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by shochatd on 2011-12-25
All of a sudden, DNS lookups were failing, and I found that /etc/resolv.conf was empty. And again, if I edit it, and put in some valid DNS server addresses, everything works again until network-manager does its thing again, and then once again, it is empty (except for the comment about network-manager). Last time this happened it was because my network interfaces were not "managed", but this seems to be different. I do have the up and down arrow indicator menu this time. In it, if I select Edit Connections..., I see 3 things: ifupdown(eth1), Wired connection 1, and ifupdwon(eth0). eth1 is the interface that is connected to my router. If I select ifupdown(eth1), Edit... is grayed out (why???). If I select Wired connection 1, Edit... is enabled, so I click on that. ipv4 settings tab has valid settings, including DNS. Why do I have both eth1 and "Wired connection 1"? By the way, /etc/NetworkManager/system-connections has only 1 file, called 'Wired connection 1'. If I restart network-manager, my resolv.conf is clobbered (only the comment). What is going on?
Thanks.
-- David

---

### Post by fdrake on 2011-12-25
try this :
connect the ethernet cable
and post "ifconfig"

then depenfing on the name of your interface do
```

echo "iface eth0 inet dhcp" | tee -a /etc/network/interfaces

```

restart NetworkManager and resolv.conf should bot change.

---

### Post by shochatd on 2011-12-25
Thanks for your reply. As I said, the working interface is eth1. Output of ifconfig talks about eth0, eth1, and lo. Note that I'm using static addressing on eth1, so I don't want DHCP. There is already an eth1 section in /etc/network/interfaces. That file has the following:
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

Also, 3 more with iface commented out. For eth2 (I don't have that many interfaces!), ath0 (what's that?) and wlan0 (??). Maybe I should try deleting those.

---

### Post by fdrake on 2011-12-25
> **shochatd said:**
> Thanks for your reply. As I said, the working interface is eth1. Output of ifconfig talks about eth0, eth1, and lo. Note that I'm using static addressing on eth1, so I don't want DHCP. There is already an eth1 section in /etc/network/interfaces. That file has the following:
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.6
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1

Also, 3 more with iface commented out. For eth2 (I don't have that many interfaces!), ath0 (what's that?) and wlan0 (??). Maybe I should try deleting those.

can you post output of:
```

ifconfig && route && lshw -c network

```
wlan0 is the wireless ususally, ath0, never heard before maybe is referung to "lo" ? you have too many net interfaces...

---

### Post by shochatd on 2011-12-25
> **fdrake said:**
> can you post output of:
```

ifconfig && route && lshw -c network

```

```

# ifconfig && route && lshw -c network
eth0      Link encap:Ethernet  HWaddr 00:18:f3:c8:d9:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:18:f3:c8:d9:1e  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fec8:d91e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54048001 (54.0 MB)  TX bytes:2590290 (2.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:342824 (342.8 KB)  TX bytes:342824 (342.8 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         Wireless_Broadb 0.0.0.0         UG    0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1
  *-network               
       description: Ethernet interface
       product: 88E8052 PCI-E ASF Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 21
       serial: 00:18:f3:c8:d9:1e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fa9fc000-fa9fffff ioport:c800(size=256) memory:fa9c0000-fa9dffff
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 14
       serial: 00:18:f3:c8:d9:1f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:21 memory:fa7fc000-fa7fffff ioport:a800(size=256) memory:fa7c0000-fa7dffff

```

---

### Post by shochatd on 2011-12-25
Here's something I didn't mention before, and may be important. I said before that if I click Edit connections... I see eth1, but Edit... is grayed out (so is Delete...). Here's the thing: If I hover the mouse over Edit..., I see the following:

  ***Authenticate to edit the selected connection***

So the obvious question is, HOW am I supposed to initiate this authentication?

---

### Post by drdos2006 on 2011-12-25
You may have to bond the two interfaces.....

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)
[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

regards

---

### Post by shochatd on 2011-12-25
It looks like I have found a solution. I simply deleted everything but lo from /etc/network/interfaces. From what I gather, that *allows* NetworkManager to handle the interfaces (that are not listed there). Then I restarted network-manager. Now, in the up/down arrow indicator eth0 and eth1 disappeared altogether. It now has Wired connection 1 which I've been able to edit all along (there is now Wired connection 2 in Edit connections... -- I suspect that's the one previously known as eth0, which is not connected to anything). But ifconfig still talks about eth0 and eth1. I guess the same hardware interface is known by different names depending on the tool? More important, now /etc/resolv.conf has exactly the DNS server addresses which are currently listed in the IPv4 settings tab for Wired connection 1 (instead of nothing at all). I imagine there are other solutions which are not to have Network Manager be involved at all. But I now having something that works, and it is letting NM do its thing.

---

### Post by fdrake on 2011-12-25
glad that you find a solution but is the /etc/resolv.conf still changing after a reboot? (it should since your interfaces file is empty and NetManager shoul be managing all of them) i think the problem was the gateway value! from your "route" command (i assume you are using the same router for both wifi and ethernet) is 192.168.1.0 but in the interfaces file is "192.168.1.1" .
Since the DNS server address is usually defined trough the gateway.

If you have a 
1. static IP address (like you needed)
2. DNS is working 

then you are all set . If not you may want to check those values.

---

### Post by shochatd on 2011-12-25
Yes, it works even after a reboot now. I figured it would because it was working after restarting network-manager, whereas before, that would always wipe out resolv.conf. Thanks for your help. You got me to pay attention to /etc/network/interfaces. As for routing, there had not been any problem with IP routing all along. The only thing that wasn't working was DNS (because there were no entries in resolv.conf).

---

