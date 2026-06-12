---
title: "Server/router machine 'forgets' it's static ip when another computer is booted"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Oswald1 on 2010-01-09
Cheers,

I'm using an older laptop as a nfs-server and a router and what not so that it's connected to a cable modem from it's integrated network adapter and directly to my 'main' pc via a usb ethernet adapter.

My problem is that _almost_ everytime the main-pc is booted, the server forgets it's static ipv4 address and I have to set it manually to get things working again.

Here's what my /etc/network/interfaces looks like on the server at the moment:
```

auto lo
iface lo inet loopback

#auto eth0
mapping hotplug
        script grep
        map eth0


iface eth0 inet static
        address 192.168.0.1
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255

```

I added the mapping hotplug part as a random attempt to get things working to no avail.

Any ideas what might help out here?

TIA!


p.s. This might sound a tad silly, but I'm not sure whether I have a dhcp server running on the server machine, got a bit lost in the setup process. Might this cause some troubles?

---

### Post by slakkie on 2010-01-09
-edit- i'm wrong.

Have a look here: [https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

---

### Post by Oswald1 on 2010-01-09
ipcalc 192.168.0.0/24 gives:

```
Address:   192.168.0.0          11000000.10101000.00000000. 00000000
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   192.168.0.0/24       11000000.10101000.00000000. 00000000
HostMin:   192.168.0.1          11000000.10101000.00000000. 00000001
HostMax:   192.168.0.254        11000000.10101000.00000000. 11111110
Broadcast: 192.168.0.255        11000000.10101000.00000000. 11111111
Hosts/Net: 254                   Class C, Private Internet

```

Also /usr/share/doc/ifupdown/examples/network-interfaces suggests having 192.168.0.0 as network and 192.168.0.X as address. Am I missing something here, or why it's wrong to have them like that?

---

### Post by Iowan on 2010-01-09
Which address gets lost - the eth0 or the USB Adapter? 
I presume you mean **ifconfig -a** shows no IP address for eth0.

---

### Post by Oswald1 on 2010-01-09
eth0 is the usb-adapter.

ifconfig shows a ipv6 address for eth0 after booting the client but no ipv4 address.

ifconfig eth0 192.168.0.1 sets the address correctly.

---

### Post by Iowan on 2010-01-09
> **Oswald1 said:**
> eth0 is the usb-adapter.:confused: What is the "integrated network adapter" that connects to the cable modem?
(AKA post results of **lshw -C network**)

---

### Post by Oswald1 on 2010-01-09
Here's the output of
lshw -C network

```
  *-network               
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 41
       serial: 00:00:e2:5b:c5:68
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.1 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:80101000-80101fff ioport:7000(size=64)
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:26:82:6c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: eth2
       serial: 00:1a:9f:0b:08:44
       size: 100MB/s
       capacity: 1GB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88178 USB 2.0 Ethernet ip=213.243.180.230 link=yes multicast=yes port=MII speed=100MB/s

```

eth2 is the 'integrated network adapter'. Additionaly there is a wireless adapter which isn't used for anything.

---

### Post by Oswald1 on 2010-01-09
Here's additionally the output of ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:00:e2:5b:c5:68  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e2ff:fe5b:c568/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5217791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5994794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:950183478 (950.1 MB)  TX bytes:4175230243 (4.1 GB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:26:82:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x7040 

eth2      Link encap:Ethernet  HWaddr 00:1a:9f:0b:08:44  
          inet addr:213.243.180.230  Bcast:213.243.183.255  Mask:255.255.248.0
          inet6 addr: fe80::21a:9fff:fe0b:844/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17992388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2055796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1876857210 (1.8 GB)  TX bytes:267394489 (267.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:641634 (641.6 KB)  TX bytes:641634 (641.6 KB)

```



Also, my apologies for mixing things up. At a point of debugging things I swapped the interfaces! My pc is connected to the 'integrated interface' and the internet connection is at the usb adapter. So it's the integrated one that's acting up. Sorry!

---

### Post by Oswald1 on 2010-01-10
Perhaps these entries in the logs might give some hints to someone more knowledgeable? They appear once I boot the client pc. The entries starting at 13:34:04 appear once I manually set the ip address.


```
syslog:Jan 10 13:32:58 maikki kernel: [2217843.000518] e100: eth0 NIC Link is Down
syslog:Jan 10 13:32:58 maikki NetworkManager: <info>  (eth0): carrier now OFF (device state 3)
syslog:Jan 10 13:32:58 maikki NetworkManager: <info>  (eth0): device state change: 3 -> 2 (reason 40)
syslog:Jan 10 13:32:58 maikki NetworkManager: <info>  (eth0): deactivating device (reason: 40).
syslog:Jan 10 13:32:58 maikki avahi-daemon[839]: Withdrawing address record for 192.168.0.1 on eth0.
syslog:Jan 10 13:32:58 maikki avahi-daemon[839]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.1.
syslog:Jan 10 13:32:58 maikki avahi-daemon[839]: Interface eth0.IPv4 no longer relevant for mDNS.
syslog:Jan 10 13:33:00 maikki NetworkManager: <info>  (eth0): carrier now ON (device state 2)
syslog:Jan 10 13:33:00 maikki NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
syslog:Jan 10 13:33:00 maikki kernel: [2217845.000203] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
syslog:Jan 10 13:34:04 maikki avahi-daemon[839]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.1.
syslog:Jan 10 13:34:04 maikki avahi-daemon[839]: New relevant interface eth0.IPv4 for mDNS.
syslog:Jan 10 13:34:04 maikki avahi-daemon[839]: Registering new address record for 192.168.0.1 on eth0.IPv4.
```

---

### Post by Oswald1 on 2010-01-10
Hmm... I think I have fixed the problem now. I removed network-manager altogether and added 

auto eth2
iface eth2 inet dhcp

to /etc/network/interfaces

At least a couple of test boots went through with no problems.

---

