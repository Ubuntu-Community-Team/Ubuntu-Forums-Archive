---
title: "CODE CHECK: IP Tables"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by WhiteDragon4Ever on 2013-02-25
Hello,

I have a wireless router that I am trying use IP Tables to limit bandwidth. It has been a long time since I have used IP Tables and I was wondering if someone could look this script over and let me know if there are any mistakes in it.

What this script is suppose to do: It is suppose to limit all of 192.168.1.0/24 to have:

Down= 3000 kbit
Up= 175 kbit

But it is suppose to also give 192.168.1.33 a greater priority to have access to bandwidth limits of:

Down= 10000 kbit
Up= 525 kbit

```

# br0 and download limit on 192.168.1.0/24
tc qdisc del dev br0 root
tc qdisc add dev br0 root handle 1: htb
#isp down limit
tc class add dev br0 parent 1: classid 1:1 htb rate 12288kbit
tc class add dev br0 parent 1:1 classid 1:10 htb rate 3000kbit ceil
3000kbit prio 0
tc class add dev br0 parent 1:1 classid 1:15 htb rate 10000kbit ceil
10000kbit prio 1
tc qdisc add dev br0 parent 1:15 handle 15: sfq perturb 10
tc qdisc add dev br0 parent 1:10 handle 10: sfq perturb 10
tc filter add dev br0 parent 1:0 prio 0 protocol ip handle 10 fw flowid 1:10
iptables -t mangle -A POSTROUTING -d 192.168.1.33   -j MARK --set-mark 15
iptables -t mangle -A POSTROUTING -d 192.168.1.0/24 -j MARK --set-mark 10

# upload limits
ip link set imq0 up
tc qdisc del dev imq0 root
tc qdisc add dev imq0 root handle 1: htb
#isp uplimit
tc class add dev imq0 parent 1: classid 1:1 htb rate 700kbit
tc class add dev imq0 parent 1:1 classid 1:10 htb rate 175kbit ceil
175kbit prio 0
tc class add dev imq0 parent 1:1 classid 1:15 htb rate 525kbit ceil
525kbit prio 1
tc qdisc add dev imq0 parent 1:10 handle 10: sfq perturb 10
tc qdisc add dev imq0 parent 1:15 handle 15: sfq perturb 10
tc filter add dev imq0 parent 1:0 prio 2 protocol ip handle 10 fw flowid 1:10
tc filter add dev imq0 parent 1:0 prio 0 protocol ip handle 15 fw flowid 1:15
iptables -t mangle -A PREROUTING -s 192.168.1.33 -j MARK --set-mark 15
iptables -t mangle -A PREROUTING -s 192.168.1.0/24 -j MARK --set-mark 10
iptables -t mangle -A PREROUTING -j IMQ --todev 0

```

I think the only thing that might be wrong is the ordering of priorities. Help is appreciated :)

---

