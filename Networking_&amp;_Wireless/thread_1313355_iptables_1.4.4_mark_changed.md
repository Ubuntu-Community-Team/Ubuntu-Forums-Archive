---
title: "iptables 1.4.4 mark changed?"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by PhoenixtheII on 2009-11-03
I've just upgraded to ubuntu 9.10 from debian lenny 
and before i used -J MARK --set-mark to mark connections
and pick them up in ip rule's

example:
iptables -t mangle -A PREROUTING -s 192.168.1.0/24 -d 81.4.97.0/24 -j MARK --set-mark 0x1

32761: from all fwmark 0x1 lookup table1

but that doesn't seem to work anymore ;(

Any one knows what has changed?

The goal is to route a certain range/ports onto to 1 WAN connection (I've got 2 here..)

---

### Post by PhoenixtheII on 2009-11-04
Bump

---

### Post by mpokrywka on 2009-11-05
You can check manually each step:
Can iptables rule with "MARK" target be added?
```
sudo iptables -t mangle -A PREROUTING -i test -j MARK --set-mark 0x1
sudo iptables -t mangle -D PREROUTING -i test -j MARK --set-mark 0x1
```

Addidng and removing rule should run without error, in fact it should run without any output.

Then check if MARK is really set - add iptables logging right after MARK setting rule, something like:
```
iptables -t mangle -A PREROUTING -s 192.168.1.0/24 -d 81.4.97.0/24 -j LOG --log-prefix 'MARK check '
```
and watch /var/log/syslog if any packets are logged.
Log lines should end with "MARK=0x1" if MARK is set.

If MARK is set correctly, then you need to check if routing works as you configured:
First, check if you have any routing rules that can match before your "routing by fwmark", use **ip rule | egrep -v '^(0|32766|32767):'**
Then check routing table if it contains correct route: **ip route show table table1**

If you think that routing is correct, add logging of packets in iptables FORWARD chain:
```
iptables -t mangle -I FORWARD -j LOG --log-prefix 'routing check '
```
Now you will have packets logged in /var/log/syslog with input and output interface (i.e. IN=eth0 OUT=eth1), so you can check if routing works as you wanted.

---

