---
title: "Network Configurations"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by ahop on 2009-02-15
I got Ubuntu 8.10 up and running on a desktop. I am trying to get the network connection going, and running into some issues. After calling my ISP, they tried walking me through a bit, but ran into a wall because they were not familiar with Ubuntu. So, I am here to plead for help.

**ifconfig**
```
eth0
Link encap:Ethernet HWaddr 00:07:e9:7c:e8:76
inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::207:e9ff:fe7c:e876/64 Scope:Link
UP BRAODCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:438 errors:0 dropped:0 overruns:0 frame:0
TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:121870 (121.8 KB) TX bytes:22083 (22.0 KB)

lo
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNINT MTU:16436 Metric:1
RX packets:240 errors:0 dropped:0 overruns:0 frame:0
TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:15040 (15.0 KB) TX bytes:15040 (15.0 KB)

pan0
Link encap:Ethernet HWaddr 06:ba:b2:f0:4c:aa
inet6 addr: fe80::4ba:b2ff:fef0:4caa/64 Scope/Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 KB) TX bytes:636 (636.0 KB)

```

**sudo lshw -C network**
```
*-network
description: Ethernet interface
product: 82801DB PRO/100 VE (LOM) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:02:08.0
logical name: eth0
version: 81
serial: 00:07:e9:7c:e8:76
size: 100mb/s
width: 32 bits
clock: 33mhz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation-on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=64 link=yes maxlatency=56 mingt=8 module=e100 multicast=yes port=MII speed=100mb/s
*-network
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 06:ba:b2:f0:4c:aa
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by puppywhacker on 2009-02-15
Hi,

Your network card eth0 is up and running, it has an ip-address 192.168.1.3 which is used for internal networks, if your broadband router takes care of the routing you should already be in business.

So if you are not in busines, post your results for the following commands, that should helps us figure out a thing or three

```
route
iptables -L -v
dig www.google.com
cat /etc/resolv.conf
ping 192.168.1.1
ping www.google.com
traceroute www.google.com
```

---

### Post by ahop on 2009-02-15
I know the router is working fine since I can get on with ither computers.

Thanks in advance for the help.

**route**
```
Kernel IP routing table
Destination  Gateway  Genmask  Flags Metric Ref  Use Iface
```

**sudo iptables -L -v**
```
 Chain INPUT (policy ACCEPT 249 packets, 178k bytes)
pkts bytes target   prot opt in   out   source     destination


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
pkts bytes target   prot opt in   out   source     destination


Chain OUTPUT (policy ACCEPT 55 packets, 11110 bytes)
pkts bytes target   prot opt in   out   source     destination
```

**dig [www.google.com](www.google.com)**
```
; <<>> DiG 9.5.0-P2 <<>> www.google.com
;; global options: printcmd
;; connection timed out; no servers could be reached
```

**cat /etc/resolv.conf**
```
domain home
search home
nameserver 192.168.1.1
```

**ping 192.168.1.1**
```
connect: Network is unreachable
```

**ping [www.google.com](www.google.com)**
```
ping: unknown host www.google.com
```

**traceroute [www.google.com](www.google.com)**
```
The program 'traceroute' can be found in the following packages:
 * traceroute-nanog
 * tracerout
Try sudo apt-get install <selected package>
bash: tracerout: command not found
```

So I tried:
**sudo apt-get install traceroute**
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package traceroute is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package traceroute has no installation candidate
```

**sudo apt-get install traceroute-nanog**
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package traceroute-nanog
```

---

### Post by puppywhacker on 2009-02-15
Your route to the outside world doesn't exist. Bit strange since it should have been generated automatically. In a terrminal you can add them yourself and start executing 

```
sudo route add -net 192.168.1.0/24 dev eth0
sudo route add -net default gw 192.168.1.1 dev eth0
```

so if that works you can print the route again, check if you can ping the router, see if dns nameresolving is working and see if you can ping google. Rest of the commands is now less relevant

```
route
ping 192.168.1.1
dig www.google.com
ping www.google.com
```

---

### Post by ahop on 2009-02-15
I added those two lines. I tried to connect again through the network manager and that still is not working. Here is the results of the terminal commands:

**route**
```
Kernel IP routing table
Destination   Gateway       Genmask   Flags  Metric  Ref   Use Iface
default       192.168.1.1   0.0.0.0   UG     0       0       0 eth0
```

**ping 192.168.1.1**
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data
```

After that point, it seems like it is getting caught up and doesn't finish executing. So I went into Networking tools, and tried pingning the IP from there. It returned with no results.

---

### Post by ahop on 2009-02-15
Okay, well. It is working now. Apparently the solution was taking the dog out for a walk around the block. When I came back, the network icon on the top bar was initialized. And, now it works.

Thanks for the help.

---

### Post by GARoss on 2009-02-15
I see that you've got this working; great. Here's a few this I've learned over the last 2 weeks with Ubuntu that might help. If you have Firestarter as a firewall, read on. If not, ignore this post as your issue is elsewhere.
 
*Firestarter* as an add-on firewall in Ubuntu it will block all sharing when it is activated. I could not connect to shared folders & printers on my network until it was de-activated. Today, I learned to edit inbound traffic port #s to Firestarter's Policy that corrected this issue. Now, all network shared folders & printers are allowed with the firewall active. 
The way I learned what port #s were being blocked was to start *Firestarter*. There are 3 tabs *Status, Events & Policy*. Click on Events. From another computer, try to open a shared folder on the Ubuntu computer. The Events window will indicate & show what is being blocked & info time, port, ect shows in a line beneath Blocked connections. Write the port # down & open the next tab, Policy. Under Editing/ Inbound traffic policy, use the lower window & right mouse click & pick + Add rule. Another window opens; just add the port # you'd like to add under Allow service. Then toggle Anyone under When the source is... Click + Add & your finished. It should work from now until something is changed.
As I said, I don't know if you have Firestarter or not. In any case, welcome to Ubuntu!

---

