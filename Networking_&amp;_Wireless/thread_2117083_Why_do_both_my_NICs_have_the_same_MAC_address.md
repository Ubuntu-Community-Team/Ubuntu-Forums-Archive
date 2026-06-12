---
title: "Why do both my NICs have the same MAC address?"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by deltatux on 2013-02-17
Hi guys,

So I just installed Ubuntu 12.10, everything's going great, except for my two NICs, for the first day, I was configuring my NICs so that they can both become bonded together so that they can both be used. I used balance-rr and it worked great. The next day I rebooted the machine, things got AWOL for some reason. It no longer used both my network interfaces since it lost "eth1" and now for some reason even though I unbonded the two NICs, both of them have the same MAC address even though my /etc/udev/rules.d/70-persistent-net.rules file have them defined separately (original stock Ubuntu detected file):

```

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:ed:6e:55", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.6/0000:06:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="50:e5:49:e6:1e:64", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

However, whenever I check ifconfig, it spits it out like this:
```

eth0      Link encap:Ethernet  HWaddr 50:e5:49:ed:6e:55  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:feed:6e55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:412 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:177126 (177.1 KB)  TX bytes:46240 (46.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71861 (71.8 KB)  TX bytes:71861 (71.8 KB)

rename3   Link encap:Ethernet  HWaddr 50:e5:49:ed:6e:55  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:feed:6e55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3093 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3379067 (3.3 MB)  TX bytes:566750 (566.7 KB)
          Interrupt:20 Memory:f7f00000-f7f20000 

```

Here was the original bonding configuration:
```

auto eth0
iface eth0 inet manual
bond-master bond0

auto eth1
iface eth1 inet manual
bond-master bond0

auto bond0
allow-hotplug bond0
iface bond0 inet dhcp
       bond-mode balance-rr
       bond-miimon 100
       bond-slaves eth0 eth1

```

The two NICs are my onboard NICs on my GIGABYTE GA-Z77X-UD5H motherboard.

Does anyone have any ideas why this happens? Any potential solutions would be greatly appreciated.

Many thanks,
deltatux

---

