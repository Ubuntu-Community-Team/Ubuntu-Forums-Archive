---
title: "iptables load balancing help - nth mode"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by tgates81 on 2011-08-02
I was wondering if someone can help me figure out what is wrong with my rules, I am completely stuck. 
I am trying to create a load balancer host (192.168.32.67) that will load  balance DNS queries (port 53 tcp and udp) round robin fashion to  192.168.2.197 and 192.168.2.252 via nth mode from the statistic module.  The problem is that when I try and do nth balancing every 1 to 4 queries  gets 'stuck', as in dig hangs, I see nothing logged in iptables and  iptraf mentions something about ICMP destn port unreachable which  doesn't make much sense. Below are my rules

```


# enable forwarding 
echo 1 >| /proc/sys/net/ipv4/ip_forward 
# clear rules 
iptables -t filter -F 
iptables -t filter -X 
iptables -t nat -F 
iptables -t nat -X 
iptables -t mangle -F 
iptables -t mangle -X 
iptables -t filter -P INPUT ACCEPT 
iptables -t filter -P OUTPUT ACCEPT 
iptables -t filter -P FORWARD ACCEPT 
 
# marks for restoring existing connections 
iptables -t mangle -N RESTOREMARK 
iptables -t mangle -A RESTOREMARK -j CONNMARK --restore-mark 
iptables -t mangle -A RESTOREMARK -j LOG --log-prefix 'restore-mark: ' --log-level info 
 
# snat 
iptables -t nat -N SNAT1 
iptables -t nat -A SNAT1 -j LOG --log-prefix 'snat-source-192.168.32.67: ' --log-level info 
iptables -t nat -A SNAT1 -p all -j SNAT --to-source 192.168.32.67 
 
# dnats 
iptables -t nat -N DNAT1 
iptables -t nat -A DNAT1 -j LOG --log-prefix 'dnat-to-192.168.2.197: ' --log-level info 
iptables -t nat -A DNAT1 -p udp --dport 53 -j DNAT --to-destination 192.168.2.197:53 
iptables -t nat -A DNAT1 -p tcp --dport 53 -j DNAT --to-destination 192.168.2.197:53 
iptables -t nat -A DNAT1 -j MARK --set-mark 1 
iptables -t nat -A DNAT1 -j CONNMARK --save-mark 
 
iptables -t nat -N DNAT2 
iptables -t nat -A DNAT2 -j LOG --log-prefix 'dnat-to-192.168.2.252: ' --log-level info 
iptables -t nat -A DNAT2 -p udp --dport 53 -j DNAT --to-destination 192.168.2.252:53 
iptables -t nat -A DNAT2 -p tcp --dport 53 -j DNAT --to-destination 192.168.2.252:53 
iptables -t nat -A DNAT2 -j MARK --set-mark 2 
iptables -t nat -A DNAT2 -j CONNMARK --save-mark 
 
# restore existing connections 
iptables -t mangle -A PREROUTING -p udp --dport 53 -m state --state ESTABLISHED,RELATED -j RESTOREMARK 
iptables -t mangle -A PREROUTING -p tcp --dport 53 -m state --state ESTABLISHED,RELATED -j RESTOREMARK 
 
# round robin balance DNAT requests 
iptables -t nat -A PREROUTING -m state --state NEW -m statistic --mode nth --every 2 --packet 0 -j DNAT1 
iptables -t nat -A PREROUTING -m state --state NEW -m statistic --mode nth --every 2 --packet 1 -j DNAT2 
 
# allow DNATS back through 
iptables -t nat -A POSTROUTING -j SNAT1 

```

---

