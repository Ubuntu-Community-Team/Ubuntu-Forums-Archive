---
title: "Can't ping default gateway"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by t93ha07 on 2010-02-23
Hi Y'alls,

I have installed ubuntu 9.04 Jaunty server from disk.  I am connect to my corporate internet.  I have put in my http_proxy everywhere I can find to put it.  I am getting an ipaddress, gateway, broadcast,etc. My wired is connected.

When I try to ping my default gateway it times out. %100 packet loss. I get the ipaddress of the gateway from the (route command).

My configurations on /etc/network/interfaces is correct(I am on another computer so I can't copy and paste) and I even tried updating the drivers for NIC card.  I am using a Intel 82567LM-3.

I have been working on this longer than I care to admit. Can anyone help?

---

### Post by lloyd_b on 2010-02-23
> **t93ha07 said:**
> Hi Y'alls,

I have installed ubuntu 9.04 Jaunty server from disk.  I am connect to my corporate internet.  I have put in my http_proxy everywhere I can find to put it.  I am getting an ipaddress, gateway, broadcast,etc. My wired is connected.

When I try to ping my default gateway it times out. %100 packet loss. I get the ipaddress of the gateway from the (route command).

My configurations on /etc/network/interfaces is correct(I am on another computer so I can't copy and paste) and I even tried updating the drivers for NIC card.  I am using a Intel 82567LM-3.

I have been working on this longer than I care to admit. Can anyone help?

It's going to be very tough for us to help you if you can't provide more information.  My *guess* is that you have a routing issue, but I can't be sure without seeing information from the "ifconfig" and "route -n" commands.

Note that if you're getting an IP address from a DHCP server on the corporate LAN, then your hardware is working correctly.

Lloyd B.

---

### Post by t93ha07 on 2010-02-23
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.29.36.0   0.0.0.0         255.255.254.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0   U     0      0        0 eth0
0.0.0.0         172.29.36.1     0.0.0.0         UG    0      0        0 eth0

Here is the route -n

---

### Post by t93ha07 on 2010-02-23
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0f:fe:c4:ef:e5  
          inet addr:172.29.37.175  Bcast:172.29.37.255  Mask:255.255.254.0
          inet6 addr: fe80::20f:feff:fec4:efe5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:694571 (694.5 KB)  TX bytes:108373 (108.3 KB)
          Memory:f0500000-f0520000

---

### Post by lloyd_b on 2010-02-23
Okay - the gateway is properly defined, and it's accessible via eth0.  So it *should* be working.

Next question: is that gateway being provided via DHCP (automatically), or is that something that you manually entered in the "/etc/network/interfaces" file?  If it's manually entered, how did you determine the gateway's IP.

You mention having another machine (that you're using to post).  Can you ping the gateway from it?  And what does its routing table (the output of 'route -n') look like?

Lloyd B.

---

### Post by t93ha07 on 2010-02-23
DHCP is working automatically, not using static entries.
Yeah I can ping it from another machine
From another machine:
[root@int home]# ping -c1 172.29.36.1
PING 172.29.36.1 (172.29.36.1) 56(84) bytes of data.
64 bytes from 172.29.36.1: icmp_seq=1 ttl=255 time=0.500 ms

--- 172.29.36.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.500/0.500/0.500/0.000 ms

From another machine:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
172.29.36.0     0.0.0.0         255.255.254.0   U     0      0        0 eth0
0.0.0.0         172.29.36.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by lloyd_b on 2010-02-23
Okay, I see one difference.  The "problem" machine:```
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
[COLOR="Red"]172.29.36.0[/COLOR] 0.0.0.0 255.255.[COLOR="Red"]255[/COLOR].0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.254.0 U 0 0 0 eth0
0.0.0.0 172.29.36.1 0.0.0.0 UG 0 0 0 eth0
``` and the "good" machine ```
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.122.0 0.0.0.0 255.255.255.0 U 0 0 0 virbr0
[COLOR="Red"]172.29.36.0[/COLOR] 0.0.0.0 255.255.[COLOR="Red"]254[/COLOR].0 U 0 0 0 eth0
0.0.0.0 172.29.36.1 0.0.0.0 UG 0 0 0 eth0
```
Since the machine's IP address is at 172.29.37.x, this difference may be the problem.

You can try manually deleting that route ("route delete -net 172.29.36.0" IIRC), and then adding it back in with the correct netmask, and see what happens.  But this information *should* be provided by DHCP, and I have no clue why two different machines are getting different routes from the same DHCP server...

Also, for a sanity check, is it possible to switch the cables for the two machines?  This *shouldn't* make any difference, but if it does it means the problem isn't with the machine, but with the network.

Lloyd B.

---

### Post by t93ha07 on 2010-02-23
Thanks Man.  It was the wire or the port.  I switch wires from my PC and I tried to ping the server. IT WORKED.  Now I just need a really long ethernet cable to replace it or have the port checked.  Thanks man so much. It was your sanity check suggestion that did it. My hat if off to you.

---

