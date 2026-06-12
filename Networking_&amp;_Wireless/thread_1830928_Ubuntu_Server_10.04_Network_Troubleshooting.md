---
title: "Ubuntu Server 10.04 Network Troubleshooting"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by Cryovenom on 2011-08-22
I've got a server that I've been trying to get Ubuntu Server 10.04.01 LTS installed and running on and I've gotten incredibly close to having it work, but the Network is still giving me issues. 

The installer went off without a hitch (once I fixed some optical drive issues) and it has actually detected the "Intel Corporation 82576 Gigabit Network Connection (rev 01)" Dual-port onboard NIC which shows up when I run lspci. I statically assigned an IP, Subnet, DNS Server and Gateway to eth0 and things looked good. ifconfig showed that it was "UP", and I could ping localhost, but if I tried to ping anything on the LAN it said "Destination Host Unreachable".

Here's the ifconfig and lspci (snippet)

======== ifconfig ========
eth0      Link encap:Ethernet  HWaddr 00:25:90:2d:26:98  
          inet addr:172.30.1.75  Bcast:172.30.3.255  Mask:255.255.252.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:feb60000-feb80000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2048 (2.0 KB)  TX bytes:2048 (2.0 KB)

======== lcpci ========
...
02:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
02:00.1 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
...

I found a script on another forum that let me dump all my network info, so I'll post the results here. I'm really not even sure where to start. It correctly identifies the type of NIC it is, it's able to figure out its MAC address, and it appears to be "UP" but it won't TX/RX any packets at all.

Here's the dump of network info from that script I was talking about:

---

Mon Aug 22 10:53:40 EDT 2011
======== cat /etc/lsb-release ==========
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
======== uname -rvi =============
2.6.32-24-server #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 unknown
======== cat /etc/debian_version ==========
squeeze/sid
======== lsb_release -a ==========
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid
 

model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
model name    : AMD Opteron(tm) Processor 6128
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000
cpu MHz        : 800.000


======== free ==========
             total       used       free     shared    buffers     cached
Mem:       8191212     294972    7896240          0      10936      49364
-/+ buffers/cache:     234672    7956540
Swap:     12689400          0   12689400
 
======== ls -o /etc/rcS.d/ ==========
total 4
-rw-r--r-- 1 root 447 2009-09-07 14:58 README
lrwxrwxrwx 1 root  18 2011-08-19 09:06 S37apparmor -> ../init.d/apparmor
lrwxrwxrwx 1 root  17 2011-08-19 08:50 S55urandom -> ../init.d/urandom
lrwxrwxrwx 1 root  24 2011-08-19 09:06 S70screen-cleanup -> ../init.d/screen-cleanup
======== grep hosts: /etc/nsswitch.conf ==========
hosts:          files dns
======== grep -v '^#' /etc/resolv.conf ==========
search staffnet.com
nameserver 172.30.1.12
======== hostname --fqdn ==========
LNX-HOST-001.staffnet.com
======== cat /etc/hostname ==========
LNX-HOST-001
======== grep -v '^#' /etc/host.conf ==========
order hosts,bind
multi on
================ ifconfig -a ==============
eth0      Link encap:Ethernet  HWaddr 00:25:90:2d:26:98  
          inet addr:172.30.1.75  Bcast:172.30.3.255  Mask:255.255.252.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:feb60000-feb80000 

eth1      Link encap:Ethernet  HWaddr 00:25:90:2d:26:99  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:febe0000-fec00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2048 (2.0 KB)  TX bytes:2048 (2.0 KB)

============== route -n =================
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.30.0.0      0.0.0.0         255.255.252.0   U     0      0        0 eth0
0.0.0.0         172.30.1.19     0.0.0.0         UG    100    0        0 eth0
========== head -15 /etc/hosts ===========
127.0.0.1    localhost
172.30.1.75    LNX-HOST-001.staffnet.com    LNX-HOST-001

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
======== cat /etc/network/interfaces ==========
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 172.30.1.75
    netmask 255.255.252.0
    network 172.30.0.0
    broadcast 172.30.3.255
    gateway 172.30.1.19
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 172.30.1.12
    dns-search staffnet.com
======== cat /var/run/network/ifstate ==========
eth0=eth0
lo=lo
======== mii-tool -v eth0 ==========
eth0: no link
  product info: vendor 00:aa:00, model 57 rev 1
  basic mode:   autonegotiation enabled
  basic status: no link
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
=== dmesg | grep eth0 | grep -v SRC= ===
[    4.293222] igb 0000:02:00.0: eth0: (PCIe:2.5Gb/s:Width x4) 00:25:90:2d:26:98
[    4.293301] igb 0000:02:00.0: eth0: PBA No: ffffff-0ff
[    8.056823] ADDRCONF(NETDEV_UP): eth0: link is not ready
=== grep eth0 /var/log/messages | tail -10 ===
Aug 22 10:44:16 LNX-HOST-001 kernel: [    4.293222] igb 0000:02:00.0: eth0: (PCIe:2.5Gb/s:Width x4) 00:25:90:2d:26:98
Aug 22 10:44:16 LNX-HOST-001 kernel: [    4.293301] igb 0000:02:00.0: eth0: PBA No: ffffff-0ff
Aug 22 10:44:16 LNX-HOST-001 kernel: [    8.056823] ADDRCONF(NETDEV_UP): eth0: link is not ready
======== mii-tool -v eth1 ==========
eth1: negotiated 1000baseT-FD flow-control, link ok
  product info: vendor 00:aa:00, model 57 rev 1
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
=== dmesg | grep eth1 | grep -v SRC= ===
[    4.523107] igb 0000:02:00.1: eth1: (PCIe:2.5Gb/s:Width x4) 00:25:90:2d:26:99
[    4.523186] igb 0000:02:00.1: eth1: PBA No: ffffff-0ff
=== grep eth1 /var/log/messages | tail -10 ===
Aug 22 10:44:16 LNX-HOST-001 kernel: [    4.523107] igb 0000:02:00.1: eth1: (PCIe:2.5Gb/s:Width x4) 00:25:90:2d:26:99
Aug 22 10:44:16 LNX-HOST-001 kernel: [    4.523186] igb 0000:02:00.1: eth1: PBA No: ffffff-0ff
=== dmesg | grep eth2 | grep -v SRC= ===
=== grep eth2 /var/log/messages | tail -10 ===
========= cd /etc/dhcp3/dhclient-exit-hooks.d ; ls -al ========
total 20
drwxr-xr-x 2 root root 4096 2011-08-19 08:51 .
drwxr-xr-x 4 root root 4096 2011-08-19 08:51 ..
-rw-r--r-- 1 root root 1060 2010-04-01 18:57 debug
-rw-r--r-- 1 root root  806 2010-04-08 23:14 ntpdate
-rw-r--r-- 1 root root 1516 2010-04-01 18:57 rfc3442-classless-routes
==== end of config/network data dump =======

---

### Post by Cryovenom on 2011-08-22
Additional Info:

It looks like eth0 won't enter the "RUNNING" state.

I compared the ifconfig of that box (LNX-HOST-001) to another Ubuntu Server 10.04 that I have working here at the office. LNX-HOST-001 says:
UP BROADCAST MULTICAST  MTU:1500  Metric:1

whereas Jupiter (my other box) says:
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

I looked around and the "solution" to getting it running for people was always to ifdown/ifup the adapter. Tried that and it didn't work. Still not "RUNNING". I can't figure out why that is, or how to get it running.

Any ideas?

Jon

---

### Post by Cryovenom on 2011-08-24
Well folks, in internet parlance : Meet the brand new Mayor of Herpderpington. 

After days of troubleshooting I found an article suggesting I change the link speed from 1000baseTx-FD to something slower, 100baseTx-FD perhaps. I tried using mii-tool to do that and it gave some message saying that the adapter wouldn't accept the command. "No problem!" I thought "I'll just put a 10/100 switch in between that server and our network backbone Gbit switches, that'll make it auto-negotiate its way down to 10/100!"

So I go behind the server rack to setup the little 10/100 switch. A few days ago I had put a network cable in each of the two onboard NICs, connecting both to the backbone switch because I wasn't sure which was "eth0" and which was "eth1" so I figured I might as well cover both. I took the cable out of one NIC and put it in my little switch, then traced the other back to the backbone, unplugged it, and plugged it into my switch. Then the calls started coming in. "The GTA Database is down! No... wait... it just froze for a few minutes.. it's back". "How odd", I thought. Then I look down...

Yup. The server I've been working on for days is the one in the rack right **above** the one that I had just unplugged. The one I was working on (LNX-HOST-001) had a cable, but it was in "eth1" which was unconfigured. Plug it into eth0 and voila! Network.

I feel like such an idiot. 

Lesson: "UP" just means it has an IP, Subnet, etc... configured. "RUNNING" means it's actually got a network cable plugged into it. If it's not "RUNNING", check the cable! Oh, and double-check which server you're working on so that your Toronto office doesn't get disconnected.


Jon

---

