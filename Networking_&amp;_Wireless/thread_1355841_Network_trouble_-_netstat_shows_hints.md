---
title: "Network trouble - netstat shows hints?"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by geohei on 2009-12-15
Hi.

I have some weird network problems.
Can some tell me if this netstat print shows anything worth analysing deeper?

```
geohei@ubuntu910hol:~$ netstat -s
Ip:
    28523 total packets received
    0 forwarded
    0 incoming packets discarded
    28503 incoming packets delivered
    30959 requests sent out
Icmp:
    54 ICMP messages received
    53 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 54
    2 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 2
IcmpMsg:
        InType3: 54
        OutType3: 2
Tcp:
    864 active connections openings
    420 passive connection openings
    57 failed connection attempts
    405 connection resets received
    55 connections established
    27559 segments received
    26317 segments send out
    3736 segments retransmited
    0 bad segments received.
    583 resets sent
Udp:
    852 packets received
    2 packets to unknown port received.
    0 packet receive errors
    893 packets sent
UdpLite:
TcpExt:
    43 invalid SYN cookies received
    2 resets received for embryonic SYN_RECV sockets
    1 packets pruned from receive queue because of socket buffer overrun
    146 TCP sockets finished time wait in fast timer
    713 delayed acks sent
    1 delayed acks further delayed because of locked socket
    Quick ack mode was activated 238 times
    56 times the listen queue of a socket overflowed
    56 SYNs to LISTEN sockets dropped
    6 packets directly queued to recvmsg prequeue.
    52 bytes directly received in process context from prequeue
    9860 packet headers predicted
    7 packets header predicted and directly queued to user
    6552 acknowledgments not containing data payload received
    6226 predicted acknowledgments
    79 times recovered from packet loss by selective acknowledgements
    Detected reordering 2 times using FACK
    Detected reordering 4 times using time stamp
    10 congestion windows fully recovered without slow start
    22 congestion windows partially recovered using Hoe heuristic
    1 congestion windows recovered without slow start by DSACK
    85 congestion windows recovered without slow start after partial ack
    129 TCP data loss events
    498 timeouts after SACK recovery
    127 timeouts in loss state
    164 fast retransmits
    16 forward retransmits
    1264 retransmits in slow start
    1054 other TCP timeouts
    29 SACK retransmits failed
    94 packets collapsed in receive queue due to low socket buffer
    243 DSACKs sent for old packets
    205 DSACKs received
    1 DSACKs for out of order packets received
    98 connections reset due to unexpected data
    151 connections reset due to early user close
    9 connections aborted due to timeout
    TCPDSACKIgnoredOld: 25
    TCPDSACKIgnoredNoUndo: 80
    TCPSpuriousRTOs: 3
    TCPSackShifted: 12
    TCPSackMerged: 102
    TCPSackShiftFallback: 1001
IpExt:
    InMcastPkts: 54
    OutMcastPkts: 56
    InBcastPkts: 26
    InOctets: 5672005
    OutOctets: 14237886
    InMcastOctets: 5496
    OutMcastOctets: 5612
    InBcastOctets: 4241
```

---

### Post by geohei on 2009-12-17
Hi.

Meanwhile I noticed in the System Monitor that I have peaks in upload exceeding my max. upload capacity of my provider, which is 32 KiB. It goes up to +60 KiB, but as as said, only peaks.

Does this show any potential problem?

If yes, where can I tweak Ubuntu in such a way that this doesn't occur anymore.

I'm really running out of ideas ...

Thanks,

---

### Post by puppywhacker on 2009-12-17
Hi,

Describe your problem.

Just from a netstat, it's pretty hard to see what you are trying to do. You do have a connection and a lot of traffic which is not established properly. It looks like a congested network, but I before you start complaining to your internet provider, you really have to think about what you are trying to do here?

If you are maxing out the upload capacity also the downstream will be affected. But if your provider doesn't limit your upload stream properly you can limit the bandwith yourself to something slightly lower than the provider with "tc" trafficshaping for a smoother connection.

---

### Post by geohei on 2009-12-17
Hi.

I have some kind of torrent software (though it's not torrent). It send and receives data in irregular intervals. Sending and receiving can be simultaneous or separate. Anyway ... because of the +60 KiB upload curve on the System Monitor, it looks to me that I try to exceed the upload capacity my provider assigned.

Anyway ... I have the following speeds subscribed:
upload: 289 KiB
download: 2326 KiB
Ping times vary from 50ms to 200ms.

I have the following "RWIN" values at this time:

```
geohei@ubuntu910hol:~$ sudo sysctl -w net.ipv4.tcp_rmem="4096 80000 320000" net.ipv4.tcp_wmem="4096 10000 40000" net.ipv4.tcp_mem="320000 320000 320000"
[sudo] password for geohei: 
net.ipv4.tcp_rmem = 4096 80000 320000
net.ipv4.tcp_wmem = 4096 10000 40000
net.ipv4.tcp_mem = 320000 320000 320000
```

MTU is properly (tested!) set to 1492.

What's wrong here?

Thanks

---

### Post by puppywhacker on 2009-12-17
Torrents are congesting your network.

Set your max-connection to smething decent like 200 or lower.
Limit your bandwith, transmission has the switch to the left bottom.

Tinkering on your tcp/ip settings will not improve your situation, setting a limit on your upload will help, so that ack's on your downstream will not be queue'd in the upload queue and your latency.

---

### Post by geohei on 2009-12-17
Thanks for the reply. However the software congesting my DSL is not a torrent client. It is, regarding network technology, torrent-like. It has absolutely no buttons to manipulate in any way the network traffic! I need to get the Linux own network variables properly set in order to avoid queues.

---

### Post by puppywhacker on 2009-12-17
than your best option is to use traffic shaping with tc.

something like this will use linux to queue connections, rather than overflowing (and congesting) your internet
```
tc class add dev eth0 parent 1: classid 1:1 cbq rate 256kbit allot 1500 prio 5 bounded isolated

```

---

### Post by geohei on 2009-12-18
```
geohei@ubuntu910hol:~/Desktop/cccam213$ sudo tc class add dev eth0 parent 1: classid 1:1 cbq rate 256kbit allot 1500 prio 5 bounded isolated
RTNETLINK answers: No such file or directory
```
Besides this ... regarding the System Monitor > Ressources > Network History.
Is it correct that the Sending curve should never exceed (also no peak) the max. DSL subscribtion (in my case 256 KiB)?

Thanks,

---

### Post by puppywhacker on 2009-12-18
No, the peak is due to datapolling. And will always be an inaccurate measurement between two. Points in time and depends on how your provider throttles the connection, probably by using some bucket queuing dicipline, that is why your latency goes up. you cant limit the incoming stream so using your own upload queue will stabilize your internetconnection during congestion

---

### Post by geohei on 2009-12-21
Thanks for the explanations!

But what aboutthis error (see my previous posting ...):
```
...
RTNETLINK answers: No such file or directory
```

---

