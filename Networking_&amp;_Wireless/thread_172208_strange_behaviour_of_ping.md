---
title: "strange behaviour of ping"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by uddunderline on 2006-05-08
Dear all,

I'm using Ubuntu Breezy Badger (version 5.10) and the my kernel is 2.6.12-10-386.

I met something strange about ping and everything related to network (http, smtp, ...).

The problem is the following:
- my pc is in the 101.x network, i can ping localhost and my ip address without any problem. i can even reach the gateway of my LAN 101.1.
- The other hosts in the LAN can ping my box but i can not ping them back, the ping command was just looping without any output.
- is that the problem of my firewall? I don't think so. This is the output of my "iptables -L":

Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

I also see nothing when i run "lsmod | grep iptables".

- The other hosts in the LAN can communicate with others (inside and outside the LAN without any problem)

Can someone please tell me that anything is wrong in my box?

Thanks for your help.

Udd

---

### Post by mips on 2006-05-08
post output of **ifconfig -a** , **cat /etc/network/interface** , **route -n**

---

### Post by uddunderline on 2006-05-09
Sorry,

the problem is fixed. I had the bad IP of my gateway that's why the network request is not forwarded.

SORRY ONCE AGAIN.

Thanks for the intervention.

Udd

---

