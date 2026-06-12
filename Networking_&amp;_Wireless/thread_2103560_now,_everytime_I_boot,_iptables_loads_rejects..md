---
title: "now, everytime I boot, iptables loads rejects."
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-10
Is there any way to see how it is doing this rule on startup?

```
sudo iptables -L -v
Chain INPUT (policy ACCEPT 727 packets, 90205 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    2   662 ACCEPT     udp  --  eth0   any     anywhere             anywhere             udp dpt:bootps
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere             tcp dpt:bootps
    7   473 ACCEPT     udp  --  eth0   any     anywhere             anywhere             udp dpt:domain
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere             tcp dpt:domain

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  293 31320 ACCEPT     all  --  any    eth0    anywhere             10.42.0.0/24         state RELATED,ESTABLISHED
  417 33194 ACCEPT     all  --  eth0   any     10.42.0.0/24         anywhere            
    0     0 ACCEPT     all  --  eth0   eth0    anywhere             anywhere            
    0     0 REJECT     all  --  any    eth0    anywhere             anywhere             reject-with icmp-port-unreachable
    0     0 REJECT     all  --  eth0   any     anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT 396 packets, 47942 bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```

The only code I was using was webmin, and it shows no rules.
yet there are rules showing in terminal view.

So a discontinuity is appearing. I read that normally, iptables comes up allowing all traffic on a boot, and rule must load separately. Now I also had played with gufw, can that still be haning around and if so how to kill it?

I uninstalled firestarter, gufw, ufw, webmin doing complete purges. the oss config still appears on booting.
So I then try this

>  sudo sh -c "iptables-save > /etc/iptables.rules"
which saves a file of iptable data. No I do remember doing a masquerade command

so I deleted it. this is that masquerade neve shows up in iptables as masquerade.
>  sudo  iptables --table nat -D POSTROUTING -s 10.42.0.0/24 ! -d 10.42.0.0/24 -j MASQUERADE


it looks like this

```
scott@scott-P5QC:~$ sudo iptables -L -v
[sudo] password for scott: 


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  161 21830 ACCEPT     all  --  any    eth0    anywhere             10.42.0.0/24         state RELATED,ESTABLISHED
  179 16885 ACCEPT     all  --  eth0   any     10.42.0.0/24         anywhere            
    0     0 ACCEPT     all  --  eth0   eth0    anywhere             anywhere            
    0     0 REJECT     all  --  any    eth0    anywhere             anywhere             reject-with icmp-port-unreachable
    0     0 REJECT     all  --  eth0   any     anywhere             anywhere             reject-with icmp-port-unreachable


```

so after running the 
>  sudo  iptables --table nat -D POSTROUTING -s 10.42.0.0/24 ! -d 10.42.0.0/24 -j MASQUERADE

and doing the 
>  sudo sh -c "iptables-save > /etc/iptables.rules"

the masquerade line is gone in the output file iptables.rules

Now perhaps how to get rid of these 2 lines?
```
    0     0 REJECT     all  --  any    eth0    anywhere             anywhere             reject-with icmp-port-unreachable
    0     0 REJECT     all  --  eth0   any     anywhere             anywhere  
```

---

