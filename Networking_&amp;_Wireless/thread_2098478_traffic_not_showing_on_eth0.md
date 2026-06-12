---
title: "traffic not showing on eth0"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by Lem0nHead on 2012-12-26
hello
this doubt is related to virtualisation, but for now I'm more interested on why there's apparently a problem with the physical network

so here's how I reproduce the problem:
```
# ovs-vsctl add-br br0
# ovs-vsctl add-port br0 eth0
# ifconfig eth0 0
# dhclient br0
```

(so far everything is working, br0 is my bridge and eth0 is on it)

then I just start a VM:
```
# virsh start base_template
```

and everything breaks

**while I'm interested in solving this virtualisation problem, currently I'm more interested on why I can't make it work right away after it happens.**
Here's what I do:
```
# ovs-vsctl del-br br0
# ifconfig eth0 0
# ip route add 0.0.0.0 dev eth0
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         255.255.255.255 UH    0      0        0 eth0
# ifconfig
eth0      Link encap:Ethernet  HWaddr b4:b5:2f:50:d6:f7  
          inet6 addr: fe80::b6b5:2fff:fe50:d6f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1278934 errors:0 dropped:0 overruns:0 frame:0
          TX packets:572585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1102300317 (1.1 GB)  TX bytes:84371939 (84.3 MB)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:322604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:207478908 (207.4 MB)  TX bytes:207478908 (207.4 MB)
# dhclient -v eth0
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/b4:b5:2f:50:d6:f7
Sending on   LPF/eth0/b4:b5:2f:50:d6:f7
Sending on   Socket/fallback
DHCPREQUEST of 172.x.x.188 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 172.x.x.188 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPREQUEST of 172.x.x.188 on eth0 to 255.255.255.255 port 67
DHCPOFFER of 172.x.x.188 from 172.x.x.1
DHCPACK of 172.x.x.188 from 172.x.x.1
```

while running dhclient, I've setup tcpdump in another terminal (I tried dhcpdump also, with the same results):
```
# tcpdump -qn -i eth0
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes

```


the mistery is: during about 2 minutes, the dhclient is supposedly sending requests and not getting an answer (tcpdump is dead quiet)... then it just starts getting answers. Here are the first tcpdump captures after it does, until the first real internet answer (from 8.8.8.8, that I left pinging):
```
20:55:44.053537 IP6 :: > ff02::16: HBH ICMP6, multicast listener report v2, 1 group record(s), length 28
20:55:44.085680 IP 0.0.0.0.68 > 255.255.255.255.67: UDP, length 300
20:55:44.088165 IP 172.x.x.1.67 > 255.255.255.255.68: UDP, length 313
20:55:44.101529 IP 172.x.x.188 > 224.0.0.22: igmp
20:55:44.193643 IP 172.x.x.188.5353 > 224.0.0.251.5353: UDP, length 53
20:55:44.300145 IP 172.x.x.188.5353 > 224.0.0.251.5353: UDP, length 330
20:55:44.332462 IP 172.x.x.188.5353 > 224.0.0.251.5353: UDP, length 221
20:55:44.366680 IP6 fe80::7921:945:5c04:7765.546 > ff02::1:2.547: UDP, length 108
20:55:44.394136 IP 172.y.y.254.1985 > 224.0.0.2.1985: UDP, length 20
20:55:44.472393 ARP, Request who-has 172.x.x.1 tell 172.x.x.1, length 46
20:55:44.550127 IP 172.x.x.188.5353 > 224.0.0.251.5353: UDP, length 330
20:55:44.772260 ARP, Request who-has 172.x.x.1 tell 172.x.x.1, length 46
20:55:44.800889 IP 172.x.x.188.5353 > 224.0.0.251.5353: UDP, length 330
20:55:44.937542 IP6 :: > ff02::1:ff50:d6f7: ICMP6, neighbor solicitation, who has fe80::b6b5:2fff:fe50:d6f7, length 24
20:55:45.001687 IP 172.x.x.188.5353 > 224.0.0.251.5353: UDP, length 300
20:55:45.024802 00:e0:7b:d9:b1:a3 > 01:00:81:00:01:00 SNAP Unnumbered, ui, Flags [Command], length 46
20:55:45.025624 00:e0:7b:d9:b1:a3 > 01:00:81:00:01:01 SNAP Unnumbered, ui, Flags [Command], length 46
20:55:45.185453 ARP, Request who-has 172.x.x.1 tell 172.x.x.188, length 28
20:55:45.185892 ARP, Reply 172.x.x.1 is-at 00:15:17:0b:19:ec, length 46
20:55:45.185903 IP 172.x.x.188.62638 > 192.168.207.10.53: UDP, length 39
20:55:45.185911 IP 172.x.x.188.62638 > 192.168.207.11.53: UDP, length 39
20:55:45.185916 IP 172.x.x.188.62638 > 192.168.206.10.53: UDP, length 39
20:55:45.189239 IP 172.x.x.188.15241 > 192.168.207.10.53: UDP, length 35
20:55:45.189261 IP 172.x.x.188.15241 > 192.168.207.11.53: UDP, length 35
20:55:45.189271 IP 172.x.x.188.15241 > 192.168.206.10.53: UDP, length 35
20:55:45.190027 IP 192.168.207.10.53 > 172.x.x.188.15241: UDP, length 51
20:55:45.190250 IP 172.x.x.188.23166 > 192.168.207.10.53: UDP, length 33
20:55:45.190506 IP 192.168.206.10.53 > 172.x.x.188.15241: UDP, length 51
20:55:45.190529 IP 172.x.x.188 > 192.168.206.10: ICMP 172.x.x.188 udp port 15241 unreachable, length 87
20:55:45.191983 IP 172.x.x.188.46815 > 69.171.241.10.443: tcp 0
20:55:45.194125 IP 172.x.x.188.5353 > 224.0.0.251.5353: UDP, length 53
20:55:45.197275 IP 192.168.207.10.53 > 172.x.x.188.23166: UDP, length 70
20:55:45.197869 IP 172.x.x.188.59200 > 74.125.130.125.443: tcp 0
20:55:45.207010 IP 172.x.x.188.34599 > 192.168.207.10.53: UDP, length 23
20:55:45.208677 IP 192.168.207.10.53 > 172.x.x.188.34599: UDP, length 98
20:55:45.208953 IP 172.x.x.188.58170 > 192.168.207.10.53: UDP, length 23
20:55:45.209827 IP 192.168.207.10.53 > 172.x.x.188.58170: UDP, length 98
20:55:45.277622 IP 172.x.x.136.49489 > 172.x.z.255.8612: UDP, length 16
20:55:45.277929 IP 172.x.x.136.63020 > 224.0.0.1.8612: UDP, length 16
20:55:45.305013 IP 172.x.x.188 > 8.8.8.8: ICMP echo request, id 30671, seq 1, length 64
20:55:45.315544 IP 8.8.8.8 > 172.x.x.188: ICMP echo reply, id 30671, seq 1, length 64
```

any hint is appreciated

thanks

---

### Post by Lem0nHead on 2012-12-27
I keep investigating this, following some new information

apparently the "link" goes down, like it's not detecting a physical connection on eth0 (ethtool reports no link), and this happens for EXACTLY 5 minutes!
```
Dec 27 11:59:38 lem0n NetworkManager[1068]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Dec 27 12:04:39 lem0n NetworkManager[1068]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]

Dec 27 12:09:18 lem0n NetworkManager[1068]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Dec 27 12:14:19 lem0n NetworkManager[1068]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]

Dec 27 12:18:41 lem0n NetworkManager[21081]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Dec 27 12:23:42 lem0n NetworkManager[23400]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]

```

a bit more log:
```
Dec 27 12:09:13 lem0n NetworkManager[1068]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Dec 27 12:09:13 lem0n kernel: [76308.073771] e1000e: eth0 NIC Link is Down
Dec 27 12:09:18 lem0n NetworkManager[1068]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Dec 27 12:09:18 lem0n NetworkManager[1068]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Dec 27 12:09:18 lem0n NetworkManager[1068]: <info> (eth0): canceled DHCP transaction, DHCP client pid 12444
Dec 27 12:09:18 lem0n avahi-daemon[1040]: Withdrawing address record for fe80::b6b5:2fff:fe50:d6f7 on eth0.
Dec 27 12:09:18 lem0n avahi-daemon[1040]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::b6b5:2fff:fe50:d6f7.
Dec 27 12:09:18 lem0n avahi-daemon[1040]: Interface eth0.IPv6 no longer relevant for mDNS.
Dec 27 12:09:18 lem0n NetworkManager[1068]: <info> DNS: starting dnsmasq...
Dec 27 12:09:18 lem0n NetworkManager[1068]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 27 12:09:18 lem0n kernel: [76312.666113] ADDRCONF(NETDEV_UP): eth0: link is not ready
(basically not happening here, then:)
Dec 27 12:14:19 lem0n kernel: [76613.105855] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
Dec 27 12:14:19 lem0n NetworkManager[1068]: <info> (eth0): carrier now ON (device state 20)
Dec 27 12:14:19 lem0n NetworkManager[1068]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 27 12:14:19 lem0n NetworkManager[1068]: <info> Auto-activating connection 'Wired connection 1'.
```

and info:
```
# hwinfo --netcard
13: PCI 19.0: 0200 Ethernet controller                          
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_1502
  Unique ID: rBUF.as9UkT3_us0
  SysFS ID: /devices/pci0000:00/0000:00:19.0
  SysFS BusID: 0000:00:19.0
  Hardware Class: network
  Model: "Intel Ethernet controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x1502 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x1495 
  Revision: 0x04
  Driver: "e1000e"
  Driver Modules: "e1000e"
  Device File: eth0
  Memory Range: 0xfe700000-0xfe71ffff (rw,non-prefetchable)
  Memory Range: 0xfe728000-0xfe728fff (rw,non-prefetchable)
  I/O Ports: 0xf040-0xf05f (rw)
  IRQ: 50 (24192 events)
  HW Address: b4:b5:2f:50:d6:f7
  Link detected: yes
  Module Alias: "pci:v00008086d00001502sv0000103Csd00001495bc02sc00i00"
  Driver Info #0:
    Driver Status: e1000e is active
    Driver Activation Cmd: "modprobe e1000e"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

---

### Post by Lem0nHead on 2013-01-04
so, little update...

I found a workaround for that and didn't mind anymore
but yesterday I was still curious and decided to try again, so I finally found out what happened... it's a security policy of my company

when I turned the VM on, its MAC address went through to eth0 (since I was bridging it with eth0), and there're some policy to shutdown your connection for 5 minutes when an unknown MAC address is detected

---

