---
title: "TCP packets not reaching application"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by gvse99 on 2011-06-28
Hi,

I am trying to use a wireless broadband device on ubuntu 10.10. The device is able to get the ip address and i can ping the outside world through that interface. But my TCP and UDP packets from outside world are not reaching the applications. For e.g. if i ftp out to an external machine over this wireless broadband interface, i see the remote server responding with a SYN ACK but the ftp program doesnt receive that. I can see the syn ack packet on the wireshark that is running on my ubuntu machine and wireshark is able to decode the tcp syn ack correctly. Any idea why the packet wouldnt reach the application ? I tried telnet, ftp, iperf tcp etc and none of them work.   

I also have a eth0 (wired ethernet) and over that all these applications work without any problem. My iptables has no policy.
[INDENT][PHP]# iptables -L -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Here is the pkt dump

No.     Time        Source                Destination           Protocol Info
  11211 22.951034   27.143.21.90          27.135.2.13           TCP      45969 > ftp [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=453226043 TSER=0 WS=6

Frame 11211 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: Woonsang_04:01:03 (01:02:03:04:01:03), Dst: Kollmorg_87:02:0d (01:02:1b:87:02:0d)
Internet Protocol, Src: 27.143.21.90 (27.143.21.90), Dst: 27.135.2.13 (27.135.2.13)
Transmission Control Protocol, Src Port: 45969 (45969), Dst Port: ftp (21), Seq: 0, Len: 0
    Source port: 45969 (45969)
    Destination port: ftp (21)
    [Stream index: 0]
    Sequence number: 0    (relative sequence number)
    Header length: 40 bytes
    Flags: 0x02 (SYN)
    Window size: 5840
    Checksum: 0x91ac [validation disabled]
    Options: (20 bytes)

No.     Time        Source                Destination           Protocol Info
  11230 22.990016   27.135.2.13           27.143.21.90          TCP      ftp > 45969 [SYN, ACK] Seq=0 Ack=1 Win=5792 Len=0 MSS=1460 TSV=2544061120 TSER=453226043 WS=6

Frame 11230 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: Woonsang_ca:d8:02 (01:02:03:ca:d8:02), Dst: Woonsang_04:01:03 (01:02:03:04:01:03)
Internet Protocol, Src: 27.135.2.13 (27.135.2.13), Dst: 27.143.21.90 (27.143.21.90)
Transmission Control Protocol, Src Port: ftp (21), Dst Port: 45969 (45969), Seq: 0, Ack: 1, Len: 0
    Source port: ftp (21)
    Destination port: 45969 (45969)
    [Stream index: 0]
    Sequence number: 0    (relative sequence number)
    Acknowledgement number: 1    (relative ack number)
    Header length: 40 bytes
    Flags: 0x12 (SYN, ACK)
    Window size: 5792
    Checksum: 0xf901 [validation disabled]
    Options: (20 bytes)
    [SEQ/ACK analysis]
        [This is an ACK to the segment in frame: 11211]
        [The RTT to ACK the segment was: 0.038982000 seconds]

[/PHP][/INDENT]

I am kind of new to Ubuntu. Dont see any error on the /var/log/messages or anywhere about packets being dropped. Any help ?.

---

