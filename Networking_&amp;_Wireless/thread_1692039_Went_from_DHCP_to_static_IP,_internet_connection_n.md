---
title: "Went from DHCP to static IP, internet connection now unreliable"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by Kiamo on 2011-02-20
Hello,
I have 40 machines, 39 running Ubuntu 10.10 Server 64bit and 1 running Ubuntu desktop 32bit (with network manager uninstalled).  All of these machines have 1-4 public static IP addresses assigned, but were formerly using 1 DHCP-assigned address on a local network.  After switching the machines to static IPs, the network connection is extremely unreliable. The machines can always ping and talk to each other (local switched LAN), but accessing the internet usually only works for a few minutes, then ceases.

I believe I have narrowed it down to the machine configs, as we have a Mac and a DLink router running off the same switch with the same static config, and they have been working non-stop just fine.

Here is some configuration from a 1-IP machine:


**/etc/network/interfaces:**
# The loopback network interface
auto lo
iface lo inet loopback

# Network interfaces

auto eth0
iface eth0 inet static
	address 38.100.###.###
	netmask 255.255.255.128
	gateway 38.100.###.###


**route -n:**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
38.100.###.###  0.0.0.0         255.255.255.128 U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         38.100.###.###  0.0.0.0         UG    100    0        0 eth0

**/etc/resolv.conf**:
nameserver 8.8.8.8
nameserver 8.8.4.4

Have also tried using ISP-provided DNS with no better success (those are the Google DNS addresses).

**ifconfig** (showing errors, dunno why):
eth0      Link encap:Ethernet  HWaddr 1c:75:08:##:##:##  
          inet addr:38.100.###.###  Bcast:38.100.###.###  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76 errors:55 dropped:0 overruns:0 frame:55
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6214 (6.2 KB)  TX bytes:5218 (5.2 KB)
          Interrupt:18 




Does anyone have any ideas to try? I've run out of ideas here. For side-notes, the connection is a direct fiber line, which I am using via the Mac to post this. I have tried disabling ipv6 on a machine just to see with no luck. Also tried removing dhcp3-client, no luck there, either.

---

