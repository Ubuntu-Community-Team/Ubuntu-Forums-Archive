---
title: "receiving packets problem"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by ankheg on 2009-05-20
i can't receive packets from net, except registering on i-face.
for example: 
my net 10.4.4.0/24 , and i have ip 10.4.4.123 with bc 10.4.4.255
packets from 10.4.4.145 i can read without any problem, but packets from 10.4.5.x can't.

it's checked by nc:
on listening(ubuntu) machine:
 # nc -l -u -p xxxxx
sending form other machine: 
# echo "message" | nc <ip> xxxx
in the same time, i can register packets with tcpdump on ubuntu machine.
iptables clear.

also, i checked the same situation on bsd in this net, all work excellent.

do anybody know, where packets can be losted?

---

