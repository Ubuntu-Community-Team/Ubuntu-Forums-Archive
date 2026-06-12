---
title: "Cant access outside network"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by UltraDangerLord on 2010-03-10
Hello All,

I setup this ubuntu 9.10 server (32bit), at first I did DHCP and it gave me an address, I updated and downloaded most of the packages I needed at that time.

I switched the IP from DHCP to static IP and now I cant access outside my network. with ping or to download packages. I can however login via ssh over my network.

The only changes I made were the hostname and the static IP

This is my /etc/network/interfaces

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.50.1
        netmask 255.255.0.0
        gateway 192.168.123.1
        broadcast 192.168.1.255

```

This is my hostname

```

sstgarment.selectsst.com

```

This is ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:11:43:cd:18:90
          inet addr:192.168.50.1  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::211:43ff:fecd:1890/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:253732 (253.7 KB)  TX bytes:101386 (101.3 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)



```


Any suggestions would be great! :p

Thanks in advance:D

---

### Post by Iowan on 2010-03-10
Big subnet... but that's probably not the problem.
What is in */etc/resolv.conf*? 
Can you **ping** externally by IP (74.125.95.103)?

---

### Post by UltraDangerLord on 2010-03-10
Thanks for the prompt reply good sir, your a gentleman and a scholar.

I should have paid more attention, this IP was outside the typical blocks that I use regularly, and I hadn't properly setup port-mapping in my router/firewall. So I made the changes in my separate hardware firewall and It works now.

Thanks for the reply :p, and sorry for the trouble;)

---

### Post by Iowan on 2010-03-10
Glad you got it going!
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

