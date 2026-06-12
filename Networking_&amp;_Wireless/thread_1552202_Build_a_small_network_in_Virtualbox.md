---
title: "Build a small network in Virtualbox"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by tranduyhung on 2010-08-13
I have never done any thing about networking like this in Linux and Ubuntu before, so I really need your help.
I have a Ubuntu Server and a Ubuntu Desktop (they are virtual machines).
Ubuntu Server has 2 adapters, the first connects to internet (NAT or Bridged), 2nd adapter connects to local network with Ubuntu Desktop with static IP (for example 192.168.1.1).
Ubuntu Desktop has only 1 adapter with static IP (192.168.1.2).
And now I want Ubuntu Desktop to be able to connect to internet through Ubuntu Server like a small office network.

Please give me some instructions.

Thank you very much!

---

### Post by bodhi.zazen on 2010-08-16
You will need to use the route command on the desktop.

Remove the default gw and add the server as the default.

Post the output of

```
sudo ifconfig
``` from the Desktop.

---

### Post by tranduyhung on 2010-08-17
Ubuntu Server:

eth0      Link encap:Ethernet  HWaddr 08:00:27:93:19:93  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe93:1993/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3170 (3.1 KB)  TX bytes:5656 (5.6 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:df:0b:a9  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fedf:ba9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3547 (3.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

Ubuntu Desktop:

eth0      Link encap:Ethernet  HWaddr 08:00:27:f6:63:0e  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fef6:630e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2320 (2.3 KB)  TX bytes:2088 (2.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Thank you so much!

---

### Post by bodhi.zazen on 2010-08-17
Well, it may be simple or complex.

First, did you set up the server to act as a firewall ? If so, how ? NAT or not ?

Second, just looking at the output, you already have a problem in that your desktop and server have the same IP address. You will need to fix that.

Basically, on the server, you will have 2 NIC, each with a different subnet.

10.x.x.x. and say 192.168.x.x

Say the 10.x.x.x connects to your new LAN, and 192.168.xx.xx connects to "the internet"

You will need to change your Desktop IP to be on the LAN and direct traffic to the server.

You can do that with iptables or the route command. I was going to suggest route, but I do not see your  virtual interfaces listed in ifconfig.

So probably you will need to configure iptables on the server and desktop, probably configure NAT.

How much or little of that do you understand ?

---

### Post by tranduyhung on 2010-08-17
Thank you bodhi.zazen.
I only understand about subnet and chaging IP.
Please give me more instructions.

---

### Post by tranduyhung on 2010-08-18
With your instructions about NAT and iptables, I've found out the solution here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing). This is what I need.
Thank you so much bodhi for your help! And so thanks to the community here!
:)

---

### Post by bodhi.zazen on 2010-08-18
> **tranduyhung said:**
> With your instructions about NAT and iptables, I've found out the solution here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing). This is what I need.
Thank you so much bodhi for your help! And so thanks to the community here!
:)

Sweet =)

I was going to give you a few references , but it is hard to generalize without a ton of typing.

If you are new to iptables, you may find this link helpful:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

