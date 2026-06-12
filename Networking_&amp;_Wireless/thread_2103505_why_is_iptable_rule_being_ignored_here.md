---
title: "why is iptable rule being ignored here?"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-10
set to reject packets from 192.168.200.36

YET, the 192.168.200.36 PC still pings on thru fine.

 18  1560 REJECT     all  --  any    any     192.168.200.36  

```
scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 4954 packets, 988K bytes)
 pkts bytes target     prot opt in     out     source               destination         
   18  1560 REJECT     all  --  any    any     192.168.200.36       anywhere             reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT 2525 packets, 189K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 3254 packets, 333K bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```


shows the ipconfig AND the ping working
```
C:\Users\scott>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : westell.com
   Link-local IPv6 Address . . . . . : fe80::8838:bf1f:6336:d42f%11
   IPv4 Address. . . . . . . . . . . : 192.168.200.36
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.200.1

Tunnel adapter isatap.westell.com:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : westell.com

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:892:2153:3f57:37db
   Link-local IPv6 Address . . . . . : fe80::892:2153:3f57:37db%13
   Default Gateway . . . . . . . . . : ::

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 10.42.0.19: bytes=32 time=22ms TTL=126
Reply from 10.42.0.19: bytes=32 time=50ms TTL=126
Reply from 10.42.0.19: bytes=32 time=26ms TTL=126
Reply from 10.42.0.19: bytes=32 time=17ms TTL=126

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 50ms, Average = 28ms

C:\Users\scott>
```

---

### Post by sdowney717 on 2013-01-10
okay modified the rule to be in the chain forward section and it still pings thru

JUST TRYING to learn something with what seems to be wacky.

```
scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 357 packets, 50113 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     all  --  any    any     192.168.200.36       anywhere             reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT 186 packets, 15100 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     all  --  any    any     192.168.200.36       anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT 232 packets, 41742 bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```

```

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 10.42.0.19: bytes=32 time=50ms TTL=126
Reply from 10.42.0.19: bytes=32 time=33ms TTL=126
Reply from 10.42.0.19: bytes=32 time=17ms TTL=126
Reply from 10.42.0.19: bytes=32 time=18ms TTL=126

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 50ms, Average = 29ms

C:\Users\scott>
```

---

### Post by Doug S on 2013-01-10
1.) On its journey to 10.42.0.19, does 192.168.200.36 go through a NAT router? Both addresses are non routable on the internet (reserved for local use, or RFC1918), so something is missing here.
 
2.) 18 packets were rejected byt the rule in your first post.

---

### Post by sdowney717 on 2013-01-10
Ubuntu router, so ubuntu is a router.

I rebooted the ubuntu PC, then it denied the pings.

If a rule is in the iptables, does it not activate except on reboots?

here is a diagram of the network layout.

[IMG]https://lh5.googleusercontent.com/-uChF5IIApj8/UOrFVvJYMiI/AAAAAAAAEV0/lyAJAvYks9k/s1024/lan.jpeg[/IMG]

---

### Post by sdowney717 on 2013-01-10
On the 192.168.200.36 win7 pc, 

I can still browse samba shares on 10.42.0.19 with those iptables rules inplace.
Does this make any sense?
[IMG]https://lh3.googleusercontent.com/-8iu_aeyEdPM/UO7kSEowyNI/AAAAAAAAEYE/jz5hOiJknUY/s1276/can%2520still%2520browse%2520shareswith%2520rejectruleinplace.png[/IMG]

---

### Post by sdowney717 on 2013-01-10
This is the latest iptables after a flush and put rules back in.

This time there is no blocked packets appearing.

```
scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 36686 packets, 8232K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     all  --  any    any     192.168.200.36       anywhere             reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT 20104 packets, 1752K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 REJECT     all  --  any    any     192.168.200.36       anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT 22489 packets, 2958K bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```

---

### Post by Doug S on 2013-01-10
O.K., this is a little confusing. I saw your other thread on this also.> If a rule is in the iptables, does it not activate except on reboots?
No. It is active right away. I suspect you might have routing issues, but am not sure. In addition to what you already post for iptables rules sets, also consider to post your nat tables, with:```
sudo iptables -t nat -v -x -n -L
```or just observe / post the entire thing in one step with```
sudo iptables-save -c
```

---

### Post by sdowney717 on 2013-01-10
does this help?

```
scott@scott-P5QC:~$ sudo iptables-save -c
[sudo] password for scott: 
# Generated by iptables-save v1.4.12 on Thu Jan 10 11:03:28 2013
*mangle
:PREROUTING ACCEPT [109065:48241281]
:INPUT ACCEPT [55132:13693252]
:FORWARD ACCEPT [53917:34547221]
:OUTPUT ACCEPT [34619:4067097]
:POSTROUTING ACCEPT [88598:38621660]
COMMIT
# Completed on Thu Jan 10 11:03:28 2013
# Generated by iptables-save v1.4.12 on Thu Jan 10 11:03:28 2013
*filter
:INPUT ACCEPT [55132:13693252]
:FORWARD ACCEPT [53917:34547221]
:OUTPUT ACCEPT [34619:4067097]
[0:0] -A INPUT -s 192.168.200.36/32 -j REJECT --reject-with icmp-port-unreachable
[0:0] -A FORWARD -s 192.168.200.36/32 -j REJECT --reject-with icmp-port-unreachable
COMMIT
# Completed on Thu Jan 10 11:03:28 2013
# Generated by iptables-save v1.4.12 on Thu Jan 10 11:03:28 2013
*nat
:PREROUTING ACCEPT [275:18903]
:INPUT ACCEPT [63:7683]
:OUTPUT ACCEPT [860:58068]
:POSTROUTING ACCEPT [1056:68480]
COMMIT
# Completed on Thu Jan 10 11:03:28 2013
scott@scott-P5QC:~$ 

```

```
scott@scott-P5QC:~$ sudo iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 285 packets, 19477 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 64 packets, 7789 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 904 packets, 60790 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1109 packets, 71670 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2013-01-10
showing the tracert on the win7 192.168.200.36 pc

```
C:\Users\scott>tracert 10.42.0.19

Tracing route to SCOTT-PC [10.42.0.19]
over a maximum of 30 hops:

  1    14 ms     1 ms    <1 ms  hubrouter.westell.com [192.168.200.1]
  2    17 ms    17 ms    37 ms  192.168.1.1
  3    17 ms    43 ms    16 ms  SCOTT-P5QC [192.168.1.102]
  4    17 ms     1 ms     4 ms  SCOTT-PC [10.42.0.19]

Trace complete.

C:\Users\scott>
```

---

### Post by Doug S on 2013-01-10
> does this help?well, yes but only in that now I am even more confused (ha, ha). At the moment it isn't clear to me how any packet is directed to the correct destination. On your diagram above, the first router after the cable modem needs to know how to direct packets, which from your traceroutes on the other thread, it seems to. I do not understand how packets are getting mapped through your Ubuntu computer without any rules in the nat table.
 
Note: I am out of time for now, and may have hurried my reply and missed something. It'll be about 6 hours before I'll be back.

---

### Post by Doug S on 2013-01-10
Your ubuntu computer should never see packets from the 192.168.200.0 sub-net, it will only see then as NAT'd via the upstream router to the 192.168.1.0 sub-net. So I think your iptables rule needs to be adjusted accordingly.

---

### Post by sdowney717 on 2013-01-10
Likely due to the magic routing table inside that router. I setup static routes to forward packets from outlier router.

If there is no route (like a road map) in the router, then packets do get dropped.

inside the ubuntu router shows this
```
scott@scott-P5QC:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth2
10.42.0.0       0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.42.0.0       10.42.0.1       255.255.0.0     UG        0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth2
scott@scott-P5QC:~$ 

```

static routes listed in the hardware router are here.

---

### Post by sdowney717 on 2013-01-10
> **Doug S said:**
> Your ubuntu computer should never see packets from the 192.168.200.0 sub-net, it will only see then as NAT'd via the upstream router to the 192.168.1.0 sub-net. So I think your iptables rule needs to be adjusted accordingly.

How?
and 
I thought packets know their origin, so iptables should also know and block.

I did a reboot and now it is blocked!
So the iptables only work on a reboot.

see results, now it is blocked! 

Ideas on why this is true?

```
C:\Users\scott>tracert 10.42.0.19

Tracing route to 10.42.0.19 over a maximum of 30 hops

  1     1 ms    <1 ms    <1 ms  hubrouter.westell.com [192.168.200.1]
  2    17 ms    17 ms    17 ms  192.168.1.1
  3    47 ms    47 ms    47 ms  SCOTT-P5QC [192.168.1.102]
  4  SCOTT-P5QC [192.168.1.102]  reports: Destination protocol unreachable.

Trace complete.

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>
```

---

### Post by sdowney717 on 2013-01-10
Reset iptables using webmin to allow all
And now it is unblocked!

Which is what I expect.
What the problem is, the iptables are not active unless I reboot.
Webmin can reset tables if there are no rules without a reboot.
Webmin can not activate rules without a reboot.
Perhaps even though webmin says it can and does, it cant and does not.

Even if the iptables show the entries, they are not active.
So is there a command to activate the tables?

```
C:\Users\scott>tracert 10.42.0.19

Tracing route to SCOTT-PC [10.42.0.19]
over a maximum of 30 hops:

  1    55 ms    <1 ms     1 ms  hubrouter.westell.com [192.168.200.1]
  2    31 ms    16 ms    17 ms  192.168.1.1
  3    33 ms    17 ms    46 ms  SCOTT-P5QC [192.168.1.102]
  4    41 ms     1 ms     1 ms  SCOTT-PC [10.42.0.19]

Trace complete.

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 10.42.0.19: bytes=32 time=51ms TTL=126
Reply from 10.42.0.19: bytes=32 time=1ms TTL=126
Reply from 10.42.0.19: bytes=32 time=1ms TTL=126
Reply from 10.42.0.19: bytes=32 time=1ms TTL=126

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 51ms, Average = 13ms

C:\Users\scott>
```

---

### Post by sdowney717 on 2013-01-10
webmin view see says it can do it.

give me terminal command to add a blocking rule and try without going thru webmin

---

### Post by sdowney717 on 2013-01-10
IMO, a bug exists in the code. I just tried it using terminal commands

> scott@scott-P5QC:~$ sudo iptables -A INPUT -s 192.168.200.0/24 -j DROP

still allows pings

```
scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 5106 packets, 903K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    7   672 DROP       all  --  any    any     192.168.200.0/24     anywhere            

Chain FORWARD (policy ACCEPT 2994 packets, 204K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 3630 packets, 433K bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```

The bug being I have to reboot for iptable new rules to activate. Flush iptables works without a reboot.


Adding reject still allowing pings
```
scott@scott-P5QC:~$ sudo iptables -A INPUT -s 192.168.200.0/24 -j REJECT
scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 786 packets, 323K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    7   672 DROP       all  --  any    any     192.168.200.0/24     anywhere            
    0     0 REJECT     all  --  any    any     192.168.200.0/24     anywhere             reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT 261 packets, 17749 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 590 packets, 53942 bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```

---

### Post by Doug S on 2013-01-10
I'm back, but sorry I am giving up on this thread, and the at least two other threads on the same thing. It is too confusing and unclear.
 
I assure you that what you see with iptables is what you get, and there isn't some bug requiring re-boot. As you investigate, also monitor the state of the ip_forward flag:```
cat /proc/sys/net/ipv4/ip_forward
```I do not use webmin or gufw or ufw or firestarter. I only use iptables directly. But, from other threads, I have seen that sometimes firestarter leaves behind a mess if it is removed, although nothing you have listed looks like firestarter leftovers to me.
 
I hope you get it all figured out and that others will help.

---

