---
title: "IPTABLES and LOG"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by Cartell on 2012-04-27
Hi there,
I'm new here and in IPTABLES.
I cannot find info about what means the output of iptables log.

This is the output of "sudo iptables -L -v"
```

Chain INPUT (policy ACCEPT 8716 packets, 6883K bytes)
 pkts bytes target     prot opt in     out     source               destination         
13813   13M LOG        all  --  any    any     anywhere             anywhere            LOG level debug prefix `iptables in: ' 
 1316 3790K ACCEPT     all  --  any    any     192.168.128.31       anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 8787 packets, 1838K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 9601 2304K LOG        all  --  any    any     anywhere             anywhere            LOG level debug prefix `iptables out: ' 
  814  466K ACCEPT     all  --  any    any     anywhere             192.168.128.31      


```

and this is a row of syslog file:
```

Apr 27 12:26:01 pippo kernel: [506085.615690] iptables out: IN= OUT=wlan0 SRC=192.168.128.126 DST=192.168.128.31 LEN=336 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=4655 DPT=4655 LEN=316 

```

I don't understand what some fields mean:
LEN = lenght? Why twice? in bytes?
TOS = ?
PREC = ?

Thank you,
Davide

---

