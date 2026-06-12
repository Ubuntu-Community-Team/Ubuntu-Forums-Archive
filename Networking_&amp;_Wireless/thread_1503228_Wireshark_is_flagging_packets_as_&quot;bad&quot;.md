---
title: "Wireshark is flagging packets as &quot;bad&quot;"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by BattlePanic on 2010-06-06
I've recently been experimenting with Wireshark as a means exploring the traffic coming to and from my computer's laptop interface

Using Wireshark for the first time, I was quickly overwhelmed by the amount of data I was seeing, so I decided to narrow my scope.  I applied a filter to only show IRC (internet relay chat) traffic.  While I know very little of the workings of TCP/IP, I'm seeing some strange things.

Upwards of 50% of the IRC-related packets are being flagged as "bad".  The packets are variously labelled "TCP Out-Of-Order", "TCP Dup ACK", and "TCP Window Update".  I'm not sure what this means nor whether there is actually a problem here.  I have noticed that the "TCP Out-Of-Order" packets appear to be identical to the preceding incoming packet.  Are these packets somehow being repeated?

I've tried using two different IRC, (irssi and xchat), and the flagged packets seem to appear in both cases.  I wondered if perhaps Wireshark was the problem and so I tried using tcpdump instead of Wireshark to observe traffic.  While tcpdump doesn't explicitly flag anything as bad, I have noticed the same same packets moving across the NIC.

As an example, this is a plain-text dump of what Wireshark reports when I send a channel message over IRC:

```

No.     Time        Source                Destination           Protocol Info
     16 6.792035    192.168.2.10          82.96.64.4            IRC      Request

Frame 16 (95 bytes on wire, 95 bytes captured)
Ethernet II, Src: IntelCor_0b:92:66 (00:13:ce:0b:92:66), Dst: 2wire_a6:87:89 (00:21:7c:a6:87:89)
Internet Protocol, Src: 192.168.2.10 (192.168.2.10), Dst: 82.96.64.4 (82.96.64.4)
Transmission Control Protocol, Src Port: 51412 (51412), Dst Port: ircd (6667), Seq: 1, Ack: 1, Len: 29
Internet Relay Chat
    Request: PRIVMSG #testchant :sdfalja

No.     Time        Source                Destination           Protocol Info
     17 7.039357    82.96.64.4            192.168.2.10          TCP      ircd > 51412 [ACK] Seq=1 Ack=30 Win=46 Len=0 TSV=2753741584 TSER=2440241

Frame 17 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: 2wire_a6:87:89 (00:21:7c:a6:87:89), Dst: IntelCor_0b:92:66 (00:13:ce:0b:92:66)
Internet Protocol, Src: 82.96.64.4 (82.96.64.4), Dst: 192.168.2.10 (192.168.2.10)
Transmission Control Protocol, Src Port: ircd (6667), Dst Port: 51412 (51412), Seq: 1, Ack: 30, Len: 0

No.     Time        Source                Destination           Protocol Info
     18 7.040740    82.96.64.4            192.168.2.10          TCP      [TCP Dup ACK 17#1] ircd > 51412 [ACK] Seq=1 Ack=30 Win=46 Len=0 TSV=2753741584 TSER=2440241

Frame 18 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: 2wire_a6:87:89 (00:21:7c:a6:87:89), Dst: IntelCor_0b:92:66 (00:13:ce:0b:92:66)
Internet Protocol, Src: 82.96.64.4 (82.96.64.4), Dst: 192.168.2.10 (192.168.2.10)
Transmission Control Protocol, Src Port: ircd (6667), Dst Port: 51412 (51412), Seq: 1, Ack: 30, Len: 0

```

And for comparison this is what tcpdump reported over the same period:

```

11:18:08.449153 IP 192.168.2.10.51412 > 82.96.64.4.6667: P 278900680:278900709(29) ack 1551024396 win 1172 <nop,nop,timestamp 2440241 2753732326>
11:18:08.696477 IP 82.96.64.4.6667 > 192.168.2.10.51412: . ack 29 win 46 <nop,nop,timestamp 2753741584 2440241>
11:18:08.697861 IP 82.96.64.4.6667 > 192.168.2.10.51412: . ack 29 win 46 <nop,nop,timestamp 2753741584 2440241>

```

In both outputs you see three packets, The last of which seems redundant.

Also, I'm not sure if it should matter, but my computer is sitting behind an integrated firewall/wireless router/dsl modem which faces the internet.

My knowledge is somewhat limited so I'm short of possible explanations for what I'm seeing.  Can any of you offer some insight?

---

