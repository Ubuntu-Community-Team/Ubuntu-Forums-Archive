---
title: "if eth0 goes down eth1 also becomes unavailable"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by harshalshete on 2011-10-20
Hi All,

I have simple configuration.
2 machines connected to a switch

**Switch config (static allocation)**
ip 192.168.0.239
sm 255.255.255.0
def gatewy 192.168.0.1

**Machine 1 config (running ubuntu and has 2 ethernet cards respectively eth0,eth1)** This machine is connected to switch.
**eth0** config
ip 192.168.0.10
sm 255.255.255.0
def gatewy 192.168.0.1

**eth1** config
ip 192.168.0.11
 sm 255.255.255.0
 def gatewy 192.168.0.1
 
**Machine 2 (Windows xp, one ethernet card)**
Config
ip 192.168.0.14
sm 255.255.255.0
dg 192.168.0.1

In this configuration everyone is able to ping each other and network is working fine.
But the problem occurs when i unplug the cable from eth0 on ubuntu machine.
after unplugging the cable from eth0 eth0 goes down.
But now if i try to ping to 192.168.0.11 from 192.168.0.14 then its also not working.
Why this kind of dependency is there? Is it property of linux kernel?
If it is then is there any workaround to this problem which will make both the ethernet cards independent of each other.


Thanks and Regards,
Harshal Shete.

---

### Post by jonobr on 2011-10-20
Hello


Having one machine with two nics on the same subnet with IP address on the same range, I dont nbelieve works.

If you want to get something like this working, you need something like hearbeat 

Take a read [Here for info]("http://www.zivtech.com/blog/setting-ip-failover-heartbeat-and-pacemaker-ubuntu-lucid")

---

