---
title: "how to create a simple lan"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by orrymr on 2012-05-11
Hi, I'm having some trouble creating a point-to-point network.
I've got 2 machines, connected by an ethernet cable.
I've use the following commands:
```

ifconfig eth2 192.168.0.10

```
and
```

ifconfig eth1 192.168.0.11

```
on the two machines to give them two unique ip addresses. (I'm not sure why they are eth2 and eth1, and not both eth0)
When I then try to ssh into one machine from the other I get a "connection refused" error.
What am I doing wrong here?

---

### Post by HermanAB on 2012-05-11
Howdy,

You need three things to make the network stack happy:
IP Address
Netmask
Default route

on first machine:
$ sudo ifconfig eth0 192.16.1.1 netmask 255.255.255.0 up
$ sudo route add default gw 192.168.1.2 eth0

on second machine:
$ sudo ifconfig eth0 192.16.1.2 netmask 255.255.255.0 up
$ sudo route add default gw 192.168.1.1 eth0

Now each should be able to ping the other one.

For SSH to work, you have to install a ssh server daemon on one of the two machines.

---

### Post by ratcheer on 2012-05-11
To connect two machines that way, you have to use a crossover cable, not a standard ethernet cable, so one NIC is sending to the other's receive pins and vice versa. It would be much better and simpler in the long run to buy a cheap ethernet switch.

Tim

---

### Post by The Cog on 2012-05-11
It may be a simple cabling issue. To connect two machines directly, you need a **crossover** cable. A normal ehternet cable will not work.

A simple way to see if the basic ethernet connection is working is to look at the output of the command **ifconfig**. The appropriate interface (probably eth0) should show the word RUNNING. Also, you would expect to see at least a few TX packets and RX packets (sent and received packets).

If the word RUNNING is missing from the interface (but it says it is UP), the most likely reason is a cabling problem.

---

