---
title: "Routing basics"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by jcab on 2011-11-17
Hi everyone,

Attached is a simple network diagram of my Linux box that connects to a VPN via openVPN, a virtual network via vmware (host-only), and a network, known as "Other" in the diagram.

I ran the following commands in the linux router box:

```
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

I can perfectly ping all networks from my linux router box and here's my routing table:

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.96.232.1     0.0.0.0         UG    0      0        0 eth0
10.22.0.1       10.22.0.117     255.255.255.255 UGH   0      0        0 tun0
10.22.0.117     0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.122.0.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet0
10.96.232.0     0.0.0.0         255.255.248.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```

But... I need the desktop in the virtual LAN (10.122.0.2) to be able to ping the VPN (10.22.0.1), and it won't get a ping reply!!!

I tried :

```
iptables -F
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT 
iptables -P FORWARD ACCEPT
```

Just to make sure iptables is not dropping anything. I've been beating on this problem the entire day today and trying different routes. And I also want to prohibit (10.122.0.2) from touching the "other" network connected to eth0, but that's another problem. My main concern now is to get the computer to get ping replies. 

Any help is greatly appreciated. Thank you.

---

### Post by pjd99 on 2011-11-17
I'm by no means an expert (it's been years since I've touched iptables), but it looks like you need to set up forwarding rules between the two virtual interfaces.

Something along the lines of:
```

iptables -I FORWARD -p all -s -i tun0 -d -i vmnet0 -j ACCEPT 
iptables -I FORWARD -p all -s -i vmnet0 -d -i tun0 -j ACCEPT 

```No guarantees though.

---

### Post by jonobr on 2011-11-17
One of the better posts I have seen in the forum, and it was a pleasure to read,.

You put a lot of time into this. (not saying I can do much to help)

But what happens when you tracert from the machine on the Lan (left hand side) to the remote network?

I think your going to have to start running tcpdump to look and see if anything is leaving your router as as far as I can see your routing table looks fine.

---

### Post by jcab on 2011-11-17
The packet does not proceed to tun0, but it does proceed to eth0. I guess that's because it's the default gateway.

```
traceroute 10.22.0.1
traceroute to 10.22.0.1 (10.22.0.1), 30 hops max, 60 byte packets
 1  10.122.0.1 (10.122.0.1)  0.292 ms  0.097 ms  0.110 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * *^C


traceroute 10.96.232.1
traceroute to 10.96.232.1 (10.96.232.1), 30 hops max, 60 byte packets
 1  10.23.122.0.1 (10.23.122.0.1)  0.592 ms  0.126 ms  0.138 ms
 2  10.96.232.3 (10.96.232.3)  0.754 ms * *
```


And tcpdump shows only echoes, but no replies. Seems like it's dropping them. Except when I ping 10.96.232.1, it does reply.

```
sudo tcpdump -i vmnet0 icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on vmnet0, link-type EN10MB (Ethernet), capture size 65535 bytes
18:59:10.097704 IP 10.122.0.2 > 10.22.0.1: ICMP echo request, id 1130, seq 1, length 64
18:59:11.093121 IP 10.122.0.2 > 10.22.0.1: ICMP echo request, id 1130, seq 2, length 64
18:59:12.092599 IP 10.122.0.2 > 10.22.0.1: ICMP echo request, id 1130, seq 3, length 64
18:59:13.092104 IP 10.122.0.2 > 10.22.0.1: ICMP echo request, id 1130, seq 4, length 64
18:59:14.091594 IP 10.122.0.2 > 10.22.0.1: ICMP echo request, id 1130, seq 5, length 64
18:59:15.091253 IP 10.122.0.2 > 10.22.0.1: ICMP echo request, id 1130, seq 6, length 64
18:59:47.021407 IP 10.122.0.2 > 10.96.232.1: ICMP echo request, id 1131, seq 1, length 64
18:59:47.036425 IP 10.96.232.1 > 10.122.0.2: ICMP echo reply, id 1131, seq 1, length 64
18:59:48.022884 IP 10.122.0.2 > 10.96.232.1: ICMP echo request, id 1131, seq 2, length 64
18:59:48.023762 IP 10.96.232.1 > 10.122.0.2: ICMP echo reply, id 1131, seq 2, length 64
18:59:49.023832 IP 10.122.0.2 > 10.96.232.1: ICMP echo request, id 1131, seq 3, length 64
18:59:49.024553 IP 10.96.232.1 > 10.122.0.2: ICMP echo reply, id 1131, seq 3, length 64
18:59:50.024716 IP 10.122.0.2 > 10.96.232.1: ICMP echo request, id 1131, seq 4, length 64
18:59:50.025614 IP 10.96.232.1 > 10.122.0.2: ICMP echo reply, id 1131, seq 4, length 64
18:59:51.025854 IP 10.122.0.2 > 10.96.232.1: ICMP echo request, id 1131, seq 5, length 64
18:59:51.026597 IP 10.96.232.1 > 10.122.0.2: ICMP echo reply, id 1131, seq 5, length 64
18:59:52.026690 IP 10.122.0.2 > 10.96.232.1: ICMP echo request, id 1131, seq 6, length 64
18:59:52.027507 IP 10.96.232.1 > 10.122.0.2: ICMP echo reply, id 1131, seq 6, length 64
^C
18 packets captured
18 packets received by filter
0 packets dropped by kernel
```

And I tried running the iptables line, but it's giving an error:

```
iptables -I FORWARD -p all -s -i tun0 -d -i vmnet0 -j ACCEPT 
Bad argument `tun0'
Try `iptables -h' or 'iptables --help' for more information.
```

---

### Post by pjd99 on 2011-11-17
> **jcab said:**
> 
And I tried running the iptables line, but it's giving an error:

```
iptables -I FORWARD -p all -s -i tun0 -d -i vmnet0 -j ACCEPT 
Bad argument `tun0'
Try `iptables -h' or 'iptables --help' for more information.
```

NVM, I think I had a brain fart. I think what I meant to say was -- set up a static route. I can't remember how to do it off the top of my head (last time was in Windows) so:
```

man route

```

---

### Post by jonobr on 2011-11-17
I was just reading and thinking that myself given ping from ubuntu seems to work ok in all directions


```

route add -host 10.22.0.1 netmask 255.255.255.255 gw 110.22.0.118 dev tun0
```

Confirm with route -rn command

If it works at to /etc/network/interfaces

---

### Post by jonobr on 2011-11-18
Any joy with this?

I really want this to work for you as you put so much effort into your OP

---

