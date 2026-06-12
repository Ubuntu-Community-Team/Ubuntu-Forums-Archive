---
title: "Why I get slow connection when I use TC Commands"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by j19861986 on 2012-03-13
I have Basic Knowledge in Networking Ports
I have recently found out that I can limit the bandwidth at the network ports, it cost quite much in Greenland the internet... after I installed it then I get all slow connections, I mean all connections (just had few ports that is un-limited, but why do I get slow connections?) I have made it into a script and can run it...

Look at the code below, and tell me what I have been wrong in this... The Ports is in the last lines
```
# Reset First and Something
tc qdisc del dev eth0 root
tc qdisc add dev eth0 root handle 1: htb
# the max Bandwidth for the download and upload
tc class add dev eth0 parent 1: classid 1:1 htb rate 3500kbit
tc class add dev eth0 parent 1: classid 1:2 htb rate 400kbit
# The Bandwidth Allocated to Ports, 1:1 is for downloads and 1:2 is for uploads
tc class add dev eth0 parent 1:1 classid 1:13 htb rate 80kbit ceil 90kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:14 htb rate 80kbit ceil 90kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:15 htb rate 1kbit ceil 11kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:16 htb rate 1kbit ceil 11kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:17 htb rate 1kbit ceil 11kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:18 htb rate 1kbit ceil 11kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:19 htb rate 1kbit ceil 11kbit prio 0
tc class add dev eth0 parent 1:1 classid 1:20 htb rate 80kbit ceil 90kbit prio 0
tc class add dev eth0 parent 1:2 classid 1:23 htb rate 40kbit ceil 45kbit prio 0
tc class add dev eth0 parent 1:2 classid 1:24 htb rate 40kbit ceil 45kbit prio 0
tc class add dev eth0 parent 1:2 classid 1:25 htb rate 1kbit ceil 1kbit prio 0
tc class add dev eth0 parent 1:2 classid 1:26 htb rate 1kbit ceil 1kbit prio 0
tc class add dev eth0 parent 1:2 classid 1:27 htb rate 1kbit ceil 1kbit prio 0
tc class add dev eth0 parent 1:2 classid 1:28 htb rate 1kbit ceil 1kbit prio 0
tc class add dev eth0 parent 1:2 classid 1:29 htb rate 1kbit ceil 1kbit prio 0
tc class add dev eth0 parent 1:2 classid 1:31 htb rate 40kbit ceil 45kbit prio 0
# Handling Number List 
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 13 fw flowid 1:13
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 14 fw flowid 1:14
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 15 fw flowid 1:15
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 16 fw flowid 1:16
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 17 fw flowid 1:17
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 18 fw flowid 1:18
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 19 fw flowid 1:19
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 20 fw flowid 1:20
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 23 fw flowid 1:23
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 24 fw flowid 1:24
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 25 fw flowid 1:25
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 26 fw flowid 1:26
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 27 fw flowid 1:27
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 28 fw flowid 1:28
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 29 fw flowid 1:29
tc filter add dev eth0 parent 1:0 prio 0 protocol ip handle 31 fw flowid 1:31
# The Ports and Number for Handling
iptables -t mangle -A POSTROUTING -p tcp --sport 3129:4999 -j MARK --set-mark 13
iptables -t mangle -A POSTROUTING -p tcp --sport 1024:3127 -j MARK --set-mark 14
iptables -t mangle -A POSTROUTING -p tcp --sport 2:19 -j MARK --set-mark 15
iptables -t mangle -A POSTROUTING -p tcp --sport 22:52 -j MARK --set-mark 16
iptables -t mangle -A POSTROUTING -p tcp --sport 54:79 -j MARK --set-mark 17
iptables -t mangle -A POSTROUTING -p tcp --sport 81:442 -j MARK --set-mark 18
iptables -t mangle -A POSTROUTING -p tcp --sport 444:1023 -j MARK --set-mark 19
iptables -t mangle -A POSTROUTING -p tcp --sport 6000:39999 -j MARK --set-mark 20
iptables -t mangle -A PREROUTING -p tcp --dport 3129:4999 -j MARK --set-mark 23
iptables -t mangle -A PREROUTING -p tcp --dport 1024:3127 -j MARK --set-mark 24
iptables -t mangle -A PREROUTING -p tcp --dport 2:19 -j MARK --set-mark 25
iptables -t mangle -A PREROUTING -p tcp --dport 22:52 -j MARK --set-mark 26
iptables -t mangle -A PREROUTING -p tcp --dport 54:79 -j MARK --set-mark 27
iptables -t mangle -A PREROUTING -p tcp --dport 81:442 -j MARK --set-mark 28
iptables -t mangle -A PREROUTING -p tcp --dport 444:1023 -j MARK --set-mark 29
iptables -t mangle -A PREROUTING -p tcp --dport 6000:39999 -j MARK --set-mark 31
```I really don't know what is wrong with it, need help guys

Best Regards
Johan Taunajik

---

### Post by j19861986 on 2012-03-19
Been doing some research, I come to the conclusion that it must be in Class C Network
It is fixed now

---

