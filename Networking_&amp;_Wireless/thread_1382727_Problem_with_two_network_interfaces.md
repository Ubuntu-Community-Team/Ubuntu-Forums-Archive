---
title: "Problem with two network interfaces"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by msaleiro on 2010-01-16
Hi all!

I am currently trying to set up two network interfaces in my laptop. The wireless connection wlan0 works fine and it's the one that I use to connect the internet. It's in 
the range of 192.168.0.x/24 (gateway: 192.168.0.1). The wired interface eth0 is connect to another router (gateway: 10.0.0.138) with IPs in the range of 10.0.0.x/24. The router is set up to work as an AP and the 10.0.0.x network will only be used to control a robot, so no internet access will be required in this network. The problem is that when I have both connections up, I can't access the Internet anymore. I can still ping both routers, I can enter both routers configuration pages but I can't connect to the Internet. If I unplug the network cable, Internet gets accessible again. 
I'm still a novice in linux  and I can't figure out how to fix this. I don't want to get into static ip for the wireless connection since I'm constantly using the laptop in different places.

The objective is to use the 10.0.0.x router to have a development platform for the robot that can be used anywhere without having to reconfigure the robot for a new network, which is a real pain.

In detail, the laptop connects via wireless to the network with intenet (192.168.0.x) and also connects via cable to another wireless router(10.0.0.x). The wireless connection of the second router is used to connect to the robot.

Since I can ping both routers when they're both connected, I think it may be something related to the ip routes.

I'm using Ubuntu 9.10 with kernel 2.6.31-17-generic

Any suggestions?

Here goes the result of route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0
```If any other information is necessary I'l provide it as quickly as I can.

Thanks in advance.

---

### Post by Iowan on 2010-01-16
The gateway is where all non-local traffic should go.
You should have only one - I presume that'd be your internet connection (wlan0).

---

### Post by msaleiro on 2010-01-16
I thought about it too, but wasn't sure. How can I remove one of the gateways (10.10.0.138) ? Thanks for your reply!

---

### Post by Iowan on 2010-01-16
[This]("http://ubuntuforums.org/showpost.php?p=8142708&postcount=8") might be modified slightly. You'd want to use your address and interface  instead of "192.168.1.1 lo"  - still may not work.

---

### Post by msaleiro on 2010-01-16
Thanks, I'll give it a try when I get home!

---

### Post by DGortze380 on 2010-01-16
This is your problem

```

0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0

```

It's common when you have two NICs.
These are default gateways. The list is processed top down, so when it hits 0.0.0.0 (ie. any address) it forwards the traffic to the gateway at 10.0.0.138

I would start by removing that route and doing some testing.

```

route del default gw 10.0.0.138 eth0

```

can you access the internet now?
the 192.168.x.x network?
the 10.0.0.x network?

If yes, you can add a 'post-up' line to /etc/interfaces to remove this route after the interface comes online.

---

### Post by msaleiro on 2010-01-17
Hi again!

It worked like a charm! Thanks to both of you guys!

By the way, how can I do this? 

> If yes, you can add a 'post-up' line to /etc/interfaces to remove this route after the interface comes online. 	

---

### Post by DGortze380 on 2010-01-17
> **msaleiro said:**
> Hi again!

It worked like a charm! Thanks to both of you guys!

By the way, how can I do this?

Add this line to /etc/network/interfaces

```

post-up route del default gw 10.0.0.138 eth0

```

---

### Post by msaleiro on 2010-01-18
Thanks!

---

