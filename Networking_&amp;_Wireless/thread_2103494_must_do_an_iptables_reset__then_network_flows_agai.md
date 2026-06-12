---
title: "must do an iptables reset  then network flows again"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-10
If I let the network run for a while, hours or a day, the network stops allowing traffic from 192.168.200.36 onwards to get to 10.42.0.19

I dont expect anyone will know the reason why it is doing this
Is it a bug?

I kept a running command prompt open on the 192.168.200.36 PC which shows how it eventually looses the ping ability.

What will fix it is I MUST reset the iptables to allow everything, And I have not added any rules and there none. By reset, I mean using webmin to reset 

> Click this button to clear all existing firewall rules and set up new rules for a basic initial configuration.

before I reset iptables and the pings do not go thru it looks like this
```
sudo iptables -L -v
Chain INPUT (policy ACCEPT 295K packets, 195M bytes)
 pkts bytes target     prot opt in     out     source               destination         
   31 10174 ACCEPT     udp  --  eth0   any     anywhere             anywhere             udp dpt:bootps
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere             tcp dpt:bootps
  493 32798 ACCEPT     udp  --  eth0   any     anywhere             anywhere             udp dpt:domain
    0     0 ACCEPT     tcp  --  eth0   any     anywhere             anywhere             tcp dpt:domain

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
1025K 1495M ACCEPT     all  --  any    eth0    anywhere             10.42.0.0/24         state RELATED,ESTABLISHED
 866K   64M ACCEPT     all  --  eth0   any     10.42.0.0/24         anywhere            
    0     0 ACCEPT     all  --  eth0   eth0    anywhere             anywhere            
  694 37950 REJECT     all  --  any    eth0    anywhere             anywhere             reject-with icmp-port-unreachable
    0     0 REJECT     all  --  eth0   any     anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT 280K packets, 61M bytes)
 pkts bytes target     prot opt in     out     source               destination 


```

 after doing the iptables reset, looks like this 
      ```

scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 257 packets, 31928 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 2 packets, 93 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 259 packets, 33125 bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 19880 packets, 5018K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 2881 packets, 1125K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 23673 packets, 2689K bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ ping 10.42.0.19

```

This shows the 192.168.200.36 running pings and traceroutes.
After it fails, If i do the reset then pings and traceroutes complete. 

Scroll to end to see it completes, after doing iptable reset firewall. I am not adding rules, it just quits working.

It always works going to the ubuntu router GATEWAY of 10.42.0.1
But will eventually fail to go to 10.42.0.19 client pc.

In that log, when it works going to 10.42.0.19, is after I do the iptables reset.

```
 

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),


C:\Users\scott>ping 10.42.0.1

Pinging 10.42.0.1 with 32 bytes of data:
Reply from 10.42.0.1: bytes=32 time=42ms TTL=63
Reply from 10.42.0.1: bytes=32 time=25ms TTL=63
Reply from 10.42.0.1: bytes=32 time=17ms TTL=63
Reply from 10.42.0.1: bytes=32 time=26ms TTL=63

Ping statistics for 10.42.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 42ms, Average = 27ms

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),



Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>ping 10.42.0.1

Pinging 10.42.0.1 with 32 bytes of data:
Reply from 10.42.0.1: bytes=32 time=42ms TTL=63
Reply from 10.42.0.1: bytes=32 time=33ms TTL=63
Reply from 10.42.0.1: bytes=32 time=20ms TTL=63
Reply from 10.42.0.1: bytes=32 time=16ms TTL=63

Ping statistics for 10.42.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 16ms, Maximum = 42ms, Average = 27ms

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination host unreachable.
Reply from 192.168.1.102: Destination host unreachable.
Reply from 192.168.1.102: Destination host unreachable.
Reply from 192.168.1.102: Destination host unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 10.42.0.19: bytes=32 time=51ms TTL=126
Reply from 10.42.0.19: bytes=32 time=17ms TTL=126
Reply from 10.42.0.19: bytes=32 time=17ms TTL=126
Reply from 10.42.0.19: bytes=32 time=43ms TTL=126

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 51ms, Average = 32ms

C:\Users\scott>tracert 10.42.0.19

Tracing route to SCOTT-PC [10.42.0.19]
over a maximum of 30 hops:

  1     1 ms    <1 ms    <1 ms  hubrouter.westell.com [192.168.200.1]
  2    45 ms    18 ms    17 ms  192.168.1.1
  3    47 ms    16 ms    44 ms  SCOTT-P5QC [192.168.1.102]
  4    17 ms     1 ms     1 ms  SCOTT-PC [10.42.0.19]

Trace complete.

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 10.42.0.19: bytes=32 time=45ms TTL=126
Reply from 10.42.0.19: bytes=32 time=17ms TTL=126
Reply from 10.42.0.19: bytes=32 time=38ms TTL=126
Reply from 10.42.0.19: bytes=32 time=17ms TTL=126

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 45ms, Average = 29ms

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 10.42.0.19: bytes=32 time=45ms TTL=126
Reply from 10.42.0.19: bytes=32 time=53ms TTL=126
Reply from 10.42.0.19: bytes=32 time=21ms TTL=126
Reply from 10.42.0.19: bytes=32 time=24ms TTL=126

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 21ms, Maximum = 53ms, Average = 35ms

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.
Reply from 192.168.1.102: Destination port unreachable.

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),

C:\Users\scott>tracert 10.42.0.19

Tracing route to 10.42.0.19 over a maximum of 30 hops

  1    52 ms     6 ms     1 ms  hubrouter.westell.com [192.168.200.1]
  2    17 ms    16 ms    37 ms  192.168.1.1
  3    17 ms    39 ms    17 ms  SCOTT-P5QC [192.168.1.102]
  4  SCOTT-P5QC [192.168.1.102]  reports: Destination protocol unreachable.

Trace complete.

C:\Users\scott>tracert 10.42.0.1

Tracing route to SCOTT-P5QC [10.42.0.1]
over a maximum of 30 hops:

  1    49 ms    <1 ms     1 ms  hubrouter.westell.com [192.168.200.1]
  2    18 ms    16 ms    46 ms  192.168.1.1
  3    16 ms     1 ms     1 ms  SCOTT-P5QC [10.42.0.1]

Trace complete.

C:\Users\scott>tracert 10.42.0.19

Tracing route to 10.42.0.19 over a maximum of 30 hops

  1    47 ms     1 ms     1 ms  hubrouter.westell.com [192.168.200.1]
  2    17 ms    16 ms    38 ms  192.168.1.1
  3    37 ms    16 ms    46 ms  SCOTT-P5QC [192.168.1.102]
  4  SCOTT-P5QC [192.168.1.102]  reports: Destination protocol unreachable.

Trace complete.

C:\Users\scott>ping 10.42.0.19

Pinging 10.42.0.19 with 32 bytes of data:
Reply from 10.42.0.19: bytes=32 time=37ms TTL=126
Reply from 10.42.0.19: bytes=32 time=17ms TTL=126
Reply from 10.42.0.19: bytes=32 time=17ms TTL=126
Reply from 10.42.0.19: bytes=32 time=32ms TTL=126

Ping statistics for 10.42.0.19:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 37ms, Average = 25ms

C:\Users\scott>tracert 10.42.0.19

Tracing route to SCOTT-PC [10.42.0.19]
over a maximum of 30 hops:

  1    <1 ms     2 ms     1 ms  hubrouter.westell.com [192.168.200.1]
  2    47 ms    16 ms    17 ms  192.168.1.1
  3    42 ms    16 ms    43 ms  SCOTT-P5QC [192.168.1.102]
  4    41 ms    55 ms    23 ms  SCOTT-PC [10.42.0.19]

Trace complete.

C:\Users\scott>
```

---

### Post by sdowney717 on 2013-01-10
only a reboot puts the rule into working order??
I rebooted and it started blocking 192.168.200.36

the webmin has apply which says
> 	Click this button to make the firewall configuration listed above active. Any firewall rules currently in effect will be flushed and replaced


If a rule is in the iptables then is is not activated unless you reboot? Which contradicts the line in webmin.

---

