---
title: "TC and qdisc as wanemulator"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by MrTimpi on 2009-04-16
Hi,

Ive been trying to use tc qdisc to simulate our wan in our testenviroment.

The closest thing i found was actually here on ubuntuforums
[http://ubuntuforums.org/showthread.php?t=946624]("http://ubuntuforums.org/showthread.php?t=946624")

In my case i got an virtual machine with ubuntu server 8.04
4 NIC's

The machine acts as router between the different subnets.

Site1 eth0 10.0.1.0/24
Site2 eth1 10.0.2.0/24
Site3 eth2 10.0.3.0/24
Site4 eth3 10.0.4.0/24

Site1 <-> Site2-4 got 4Mbit, 
Delays to Site2(30+10ms), Site3(40+10ms), Site 4(70+30ms)

Site3 <-> Site2 and Site 4 got 2Mbit
Delays to Site2(35+10ms), Site4(60+30)

Site2 <-> Site4 cannot communicate.

Ive managed puzzle this togheter to set delay and ip src dst for one site, but when i need to add the other sites im lost.

```

tc qdisc add dev eth0 root handle 1: prio bands 10
tc qdisc add dev eth0 parent 1:1 handle 10: netem delay 30ms 10ms
tc qdisc add dev eth0 parent 10:1 handle 11: htb default 1 r2q 10
tc class add dev eth0 parent 11: classid 0:1 htb rate 4096kbit ceil 4096kbit
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip src 10.0.2.0/24 flowid 10:1
tc filter add dev eth0 protocol ip parent 1:0 prio 1 u32 match ip dst 10.0.2.0/24 flowid 10:1
tc qdisc add dev eth0 parent 1:2 handle 20: pfifo
tc filter add dev eth0 protocol ip parent 1:0 prio 2 u32 match ip src 0.0.0.0/0 match ip dst 0.0.0.0/0 flowid 20:2

```

Any help would be greatly appreciated.

---

