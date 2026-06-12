---
title: "ufw firewall questons"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-07
Why when I tell it to reject incoming and outgoing traffic, that I can still ping my ubuntu pc from a win7 pc?

It does block my access to internet data set on reject.

but also did not block chrome remote desktop as that is how I can instantly use win7 pc from ubuntu.

---

### Post by sdowney717 on 2013-01-07
notice this, I enter 2 rules to say deny in for those ip's.
however from win7 , I can still ping my ubuntu pc.

The win7 ip adress is 192.168.200.36

wont the deny rule for 192.168.200.0/24 prevent it?

I can also still browse files on ubuntu from win7 at 192.168.200.36

why, what do I not understand here?

---

### Post by haqking on 2013-01-07
```
gksudo gedit /etc/ufw/before.rules
```add a comment # to the line

```
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```or use DROP instead of ACCEPT

restart ufw

GUFW sucks ;-=) and doesnt support ICMP blocking from what i remember, it is only a interface to UFW which interfaces IPTables

---

### Post by sdowney717 on 2013-01-07
what does not suck, please tell me what is a great firewall program?

Firestarter sucks too.
[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/4378](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/4378)

---

### Post by haqking on 2013-01-07
> **sdowney717 said:**
> what does not suck, please tell me what is a great firewall program?

Firestarter sucks too.
[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/4378](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/4378)

IPTables/Netfilter doesnt, it is part of the kernel.

UFW/GUFW, Firestarter are merely interfaces to it, they are not Firewalls themselves only interfaces.

Firestarter is way out of date and buggy.

read up on IPTables or UFW

and see here [http://ubuntuforums.org/showthread.php?p=11461477](http://ubuntuforums.org/showthread.php?p=11461477)

---

### Post by sdowney717 on 2013-01-07
from reading here [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I notice this here in iptables

is this just dropping all input from 192.168.200.0/24?
If so, how to get to say ACCEPT?
Is this some line I entered using gufw?
It says 0 under pkts, does this mean it has seen no packets coming from 192.168.200.0/24?
(I did ping from there)

```
Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     192.168.200.0/24     anywhere            
  199 23070 DROP       all  --  any    any     10.42.0.0/24         anywhere            


```


I would like eth2 to pass incoming packets to eth0 if that is where they are headed.
Currently they dont seem to want to pass there.

```
scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 1 packets, 60 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    7  2302 ACCEPT     udp  --  eth0   any     anywhere             anywhere             udp dpt:bootps
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere             tcp dpt:bootps
   15   976 ACCEPT     udp  --  eth0   any     anywhere             anywhere             udp dpt:domain
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere             tcp dpt:domain
 139K   44M ufw-before-logging-input  all  --  any    any     anywhere             anywhere            
 139K   44M ufw-before-input  all  --  any    any     anywhere             anywhere            
 4784 1169K ufw-after-input  all  --  any    any     anywhere             anywhere            
 4743 1159K ufw-after-logging-input  all  --  any    any     anywhere             anywhere            
 4743 1159K ufw-reject-input  all  --  any    any     anywhere             anywhere            
 4735 1159K ufw-track-input  all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  540 57817 ACCEPT     all  --  any    eth0    anywhere             10.42.0.0/24         state RELATED,ESTABLISHED
  488 59776 ACCEPT     all  --  eth0   any     10.42.0.0/24         anywhere            
    0     0 ACCEPT     all  --  eth0   eth0    anywhere             anywhere            
   13   780 REJECT     all  --  any    eth0    anywhere             anywhere             reject-with icmp-port-unreachable
    0     0 REJECT     all  --  eth0   any     anywhere             anywhere             reject-with icmp-port-unreachable
    0     0 ufw-before-logging-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-before-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-after-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-after-logging-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-reject-forward  all  --  any    any     anywhere             anywhere            


```

---

### Post by sdowney717 on 2013-01-08
Solved by installing webmin!!

I did get a certificate warning, log in anyway!

after you log in to webmin then on left side click
Networking then Linux firewall.

I got a message saying 2 rules had been entered that webmin could not deal with, so saved current iptables to a file.

The I reset the firewall.
And it worked, I can browse shared folders on all the computers. On first win7 pc, I have to map network drive since it is in a different subnet.

The webmin shows a very nice gui to the firewall configuration!


[IMG]https://lh4.googleusercontent.com/-JLN674cmEuc/UOx_lsKNoNI/AAAAAAAAEXo/GtGZ8LHzexA/s1440/fixedfirewall.png[/IMG]

---

