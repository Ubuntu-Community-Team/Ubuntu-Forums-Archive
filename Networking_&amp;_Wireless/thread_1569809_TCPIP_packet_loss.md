---
title: "TCP/IP packet loss?"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by tsocket on 2010-09-07
Hello all

I'm really hoping someone can help me with a strange problem I'm experiencing under Ubuntu Server 10.04 LTS. 

I have a server application listening for TCP/IP connections. When it receives a connection, sometimes all works as expected and sometimes not. In the cases where things do not go well, the server reports the socket is open and connected, but receives no data. On the other end, the client sends the data over TCP/IP, then waits for a response back from the server, which it of course never gets. Eventually the server gives up and closes the connection, which the client sees.

I'm not sure where to look for the problem and was hoping others may have experienced something similar or at least help me to narrow down what the problem might be.

For a start, here is the output of netstat -s:

```
$ netstat -s
Ip:
    10811 total packets received
    0 forwarded
    0 incoming packets discarded
    10811 incoming packets delivered
    7236 requests sent out
Icmp:
    348 ICMP messages received
    3 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 13
        timeout in transit: 3
        echo requests: 332
    337 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 5
        echo replies: 332
IcmpMsg:
        InType3: 13
        InType8: 332
        InType11: 3
        OutType0: 332
        OutType3: 5
Tcp:
    9 active connections openings
    57 passive connection openings
    8 failed connection attempts
    35 connection resets received
    3 connections established
    10416 segments received
    6682 segments send out
    175 segments retransmited
    8 bad segments received.
    187 resets sent
Udp:
    42 packets received
    5 packets to unknown port received.
    0 packet receive errors
    42 packets sent
UdpLite:
TcpExt:
    15 TCP sockets finished time wait in fast timer
    67 delayed acks sent
    Quick ack mode was activated 4 times
    15 packets directly queued to recvmsg prequeue.
    1 bytes directly received in process context from prequeue
    2980 packet headers predicted
    799 acknowledgments not containing data payload received
    3796 predicted acknowledgments
    17 times recovered from packet loss by selective acknowledgements
    16 congestion windows recovered without slow start after partial ack
    18 TCP data loss events
    TCPLostRetransmit: 1
    5 timeouts after SACK recovery
    23 fast retransmits
    1 forward retransmits
    91 other TCP timeouts
    6 DSACKs sent for old packets
    35 connections reset due to early user close
    3 connections aborted due to timeout
    TCPSackShifted: 50
    TCPSackMerged: 68
    TCPSackShiftFallback: 67
IpExt:
    InOctets: 3744888
    OutOctets: 2593250

```

---

