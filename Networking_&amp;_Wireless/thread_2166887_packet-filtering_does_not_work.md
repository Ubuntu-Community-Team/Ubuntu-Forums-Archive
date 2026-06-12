---
title: "packet-filtering does not work"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by Apagon on 2013-08-11
Hello folks !

I am trying to set up my firewall the way it's done in this link: 

[http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-5.html](http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-5.html)

here is my fw hard settings: 

adsl modem*192.168.0.22/29----192.168.0.17/29*eth0=fw=172.16.5.25/29*eth1----172.16.5.26/29*pc.in internal network

here is my iptables file: 

#!/bin/sh

### SET VARIABLES

echo "** setting up variables..."

IPTABLES='sudo /sbin/iptables'
IP6TABLES='sudo /sbin/ip6tables'
MODPROBE='sudo /sbin/modprobe'
INT_NET='172.16.5.24/29'
INT_INTF=eth1
EXT_INTF=eth0


### LOAD MODULES

echo "** Loading modules..."

$MODPROBE iptable_filter 
$MODPROBE iptable_nat 
$MODPROBE nf_nat
$MODPROBE nf_conntrack_ipv4
$MODPROBE nf_conntrack
$MODPROBE ip_tables 
$MODPROBE x_tables

### FLUSH EVERYTHING

echo "** Flushing existing iptables rules..."

$IPTABLES -F INPUT 
$IPTABLES -F OUTPUT 
$IPTABLES -F FORWARD
$IPTABLES -F -t nat
$IPTABLES -X

echo "** Building fw main rule..."

$IPTABLES -N block
$IPTABLES -A block -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A block -m state --state NEW -i !eth0 -j ACCEPT
$IPTABLES -A block -j DROP

$IPTABLES -A INPUT -j block
$IPTABLES -A FORWARD -j block

iptables -t nat -A POSTROUTING -s $INT_NET -o eth1 -j MASQUERADE

##end

When I apply it (sudo ./<file name>), it works without any error. 
But then, I cannot access internet anymore. 
Before I apply this bash, it worked of course with a simple masquerade:
sudo iptables -t nat -A POSTROUTING -o eth1 -s 172.16.5.24/29 -j MASQUERADE

NB.: to remove the block chain, you need to do the following: 
sudo iptables -F block 
sudo iptables -X block
otherwise, it's unremovable with the following error message: 'iptables: Directory not empty'

Of course,later on, other rules will be put inside iptables (anti-flood, anti-fragments, anti-spoof (although should be useless here), no malformed pkts, and so on...)

any idea folks? 

Many thanx to you.

---

### Post by Doug S on 2013-08-11
To ne it looks at though eth0 and eth1 are reversed. I'm suggesting that this:```
iptables -t nat -A POSTROUTING -s $INT_NET -o eth1 -j MASQUERADE
```Maybe should be this:```
iptables -t nat -A POSTROUTING -s $INT_NET -o eth0 -j MASQUERADE
```or this:```
iptables -t nat -A POSTROUTING -o $EXT_INTF -j MASQUERADE
```or even this:```
iptables -t nat -A POSTROUTING -o $EXT_INTF -j SNAT --to 192.168.0.17
```Modules do not need to be force loaded anymore, they will autoload if needed. When you mention that "I cannot access internet anymore", is that from the computer running the firewall or the pc at 172.16.5.26?

Is forwarding enabled? Example```
doug@doug-64:~/init$ cat /proc/sys/net/ipv4/ip_forward
1
```And if needed, perhaps add this to your script (or use some other method):```
#CRITICAL:  Enable IP forwarding since it is disabled by default
#
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward
```

---

### Post by Apagon on 2013-08-12
I greatly appreciate your reply Doug 

Once the fw is booted: 
The masquerade rule applied alone: I can access internet from internal netw (sysctl.conf is ok)
The same masquerade rule  applied with iptables rule: I cannot access internet anymore (from my internal netw)

Now, I notice that when I reboot, on my firewall, internal_netw is on eth0, and external_netw is on  eth1, but anyway this is another issue. 
I then do the same thing but all the way around (eth1 becoming eth0), and the issue remains the same. 

Many thanx.

---

### Post by Apagon on 2013-08-12
following my last post, 
when fw reboots with internal_netw on eth0 and external_netw on eth1, I change the routes accordinly:
I mean, on the internal_netw, default route goes always to 172.16.5.25, on fw, default goes always to 192.168.0.22, and 172.16.5.24/29 to 172.16.5.25...

---

### Post by Apagon on 2013-08-12
you were right Doug !

Having made too many changes, I made mistake with eth0 & eth1. 

I put a SNAT rule instead of MASQUERADE: iptables -t nat -A POSTROUTING -s 172.16.5.24/29 -j SNAT --to 192.168.0.17

but there is one remaining question: 

it works like this:                   $IPTABLES -A block -m state --state NEW -i eth0 -j ACCEPT 
but it does not work like this:  $IPTABLES -A block -m state --state NEW -i !eth1 -j ACCEPT 

:-((

---

### Post by GwL3eNC on 2013-08-12
Hi,

because i dont know user defined chains i made it like that. I'm no pro, please dont take it blind. Think you can adapt it.
Because it denis all, it's possible you must implement more rules for icmp etc.

fw="/sbin/iptables"

WWW_IP="`ifconfig wlan0 | grep 'inet Adresse' |  awk '{print $2}' | sed -e 's/.*://'`"
WWW_IF="wlan0"

LAN_IP="192.168.0.1"
LAN_RANGE="192.168.0.0/24"
LAN_IF="eth0"

echo 1 > /proc/sys/net/ipv4/ip_forward 

$fw -P INPUT DROP
$fw -P OUTPUT DROP
$fw -P FORWARD DROP

$fw -A INPUT -i lo -j ACCEPT
$fw -A OUTPUT -o lo -j ACCEPT

$fw -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
$fw -A OUTPUT -p tcp ! --syn -m state --state NEW -j DROP
$fw -A FORWARD -p tcp ! --syn -m state --state NEW -j DROP

$fw -A INPUT -p tcp ! --syn -m state --state NEW -j LOG
$fw -A OUTPUT -p tcp ! --syn -m state --state NEW -j LOG
$fw -A FORWARD -p tcp ! --syn -m state --state NEW -j LOG

$fw -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$fw -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$fw -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

$fw -A OUTPUT -p tcp -o $WWW_IF -m multiport --dports 80,443 -j ACCEPT
$fw -A OUTPUT -p udp -o $WWW_IF --dport 53 -j ACCEPT

$fw -A INPUT -p tcp -m multiport --dports 80,443 -i $LAN_IF -s $LAN_RANGE -j ACCEPT
$fw -A INPUT -p udp --dport 53 -i $LAN_IF -s $LAN_RANGE -j ACCEPT
$fw -A FORWARD -p udp --dport 53 -i $LAN_IF -o $WWW_IF -m state --state NEW -j ACCEPT 
$fw -A FORWARD -o $WWW_IF -i $LAN_IF -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
$fw -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

$fw -o $WWW_IF -t nat -A POSTROUTING -j MASQUERADE

$fw -A INPUT -j LOG --log-level debug --log-prefix "LOG_IN: " 
$fw -A OUTPUT -j LOG --log-level debug --log-prefix "LOG_OUT: " 
$fw -A FORWARD -j LOG --log-level debug --log-prefix "LOG_FOR: "

---

### Post by Apagon on 2013-08-12
Many thanx to you GwL3eNC

I will dig into your code and use some chunks of it if it fits to me

---

