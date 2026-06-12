---
title: "ibm R50e wirless connection is slow"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by p0miki on 2011-02-16
Hello,
I have installed Ubuntu 10.10 on my old ibm R50e. Everything work like a charm except the wireless network. If the signal strength is good (more than 80%) than everything is fine. Alas, where I'm at, the usual signal strength is about 30%. Browsing in general is very slow. Many web pages don't completely load and just get stuck in the middle and the connection itself have a tendency to disconnect and reconnect every now and than. I have searched and tried numerous things so far including:
Testing several browsers (chrom, midori & firefox. With firefox I also went ahead into the config and tripled just about any timeout option to no avail).
Tried changing dns file to help improve dns speed as well as specifying the dns server of the ISP the w. router is using.
Trying some tcp tweaking from different google results when searching Ubuntu wireless slow and other similar phrases.
The thing is that when I reboot to the XP that sits on the laptop, the wireless network work fine and the speed is constant and good - which make me believe  the problem is in the tcp/ip configuration - I tried searching around the net but I'm not much of a network man and I don't have a clue which of the many parameters I should try to change. 
I would be very grateful if someone could suggest how and which tcp/ip parameter I should config, and if you could throw a little explanation as to why, all the better.
Here is a netstat -s summary:
```
Ip:
    28597 total packets received
    8 with invalid addresses
    0 forwarded
    0 incoming packets discarded
    26413 incoming packets delivered
    27984 requests sent out
    108 dropped because of missing route
Icmp:
    89 ICMP messages received
    3 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 89
    80 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 80
IcmpMsg:
        InType3: 89
        OutType3: 80
Tcp:
    907 active connections openings
    30 passive connection openings
    13 failed connection attempts
    44 connection resets received
    5 connections established
    20713 segments received
    21367 segments send out
    968 segments retransmited
    0 bad segments received.
    283 resets sent
Udp:
    5431 packets received
    41 packets to unknown port received.
    0 packet receive errors
    5693 packets sent
UdpLite:
TcpExt:
    5 packets pruned from receive queue because of socket buffer overrun
    387 TCP sockets finished time wait in fast timer
    518 packets rejects in established connections because of timestamp
    633 delayed acks sent
    Quick ack mode was activated 501 times
    14 packets directly queued to recvmsg prequeue.
    5618 bytes directly received in process context from prequeue
    9888 packet headers predicted
    4 packets header predicted and directly queued to user
    2232 acknowledgments not containing data payload received
    536 predicted acknowledgments
    112 congestion windows recovered without slow start after partial ack
    8 timeouts after SACK recovery
    11 retransmits in slow start
    433 other TCP timeouts
    178 packets collapsed in receive queue due to low socket buffer
    519 DSACKs sent for old packets
    9 DSACKs sent for out of order packets
    95 DSACKs received
    70 connections reset due to unexpected data
    15 connections reset due to early user close
    38 connections aborted due to timeout
    TCPDSACKIgnoredOld: 17
    TCPDSACKIgnoredNoUndo: 32
    TCPSackShiftFallback: 13
    TCPDeferAcceptDrop: 13
IpExt:
    InMcastPkts: 151
    OutMcastPkts: 60
    InBcastPkts: 162
    InOctets: 19769831
    OutOctets: 4318201
    InMcastOctets: 29654
    OutMcastOctets: 12292
    InBcastOctets: 19337

```

---

