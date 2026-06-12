---
title: "iptables question: default DROP policy and TCP Three Way Handshake"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by Johnny-Gear on 2012-04-22
Hi All,

My default policy for an iptables config I am working on is as follows:

```
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
```I understand that in most cases, because the OUTPUT chain default policy is DROP, 2 rules are required so traffic can flow both ways (INPUT and OUTPUT) - basically, everything that is requires throughfare must be whitelisted.

My question is regarding the TCP Three Way Handshake - currently the only rule I have for it is:

```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```I believe I need an OUTPUT rule to allow the initial SYN packet out and also one to allow the final ACK packet. I was wondering if someone could help me to craft the most restrictive rules possible to allow this.

Here is what I have so far:

This is the conventional example I have seen:
```
iptables -A OUTPUT -p tcp -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT
```Can I get away with just this? If not, why not?
```
iptables -A OUTPUT -p tcp -m state --state NEW,ESTABLISHED -j ACCEPT
```Is something like this possible in place of the above?
(not sure if I have the right flags - advice is welcome)
```
iptables -A OUTPUT -p tcp -m tcp --tcp-flags SYN SYN -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --tcp-flags ACK ACK -j ACCEPT
```Thanks in advance.

Regards,

Johnny

---

