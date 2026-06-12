---
title: "Sniffing ppp dialup layer 2 packets like LCP frames etc."
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by linuxusr50 on 2010-09-11
All,

I would like some assistance from someone that knows how to sniff dial-up packets while the ppp session is being established.

I have had no problem sniffing packets with wireshark after the connection has been established,  but I am attempting to learn the ppp, lcp, and chap protocols better and would like to look at some of the frames that occur while establishing the ppp dial-dial up link.

I have not found anything useful yet in tcpdump or wireshark that can help me do this.

I use gnome-ppp to establish the connection.

Any help would be appreciated.

---

### Post by utilitytrack on 2010-09-13
> **linuxusr50 said:**
> 
I have not found anything useful yet in tcpdump or wireshark that can help me do this.

Hello, look:

```

# pppd call provider
# tcpdump pppoes -i eth0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

PPPoE  [ses 0xd5f] LCP, Conf-Request (0x01), id 1, length 16
PPPoE  [ses 0xd5f] LCP, Conf-Request (0x01), id 233, length 21
PPPoE  [ses 0xd5f] LCP, Conf-Ack (0x02), id 1, length 16
PPPoE  [ses 0xd5f] LCP, Conf-Ack (0x02), id 233, length 21
PPPoE  [ses 0xd5f] LCP, Echo-Request (0x09), id 0, length 10
PPPoE  [ses 0xd5f] CHAP, Challenge (0x01), id 1, Value 596b047f0ae432c659d3fa87664b9876, Name a919-arb01
PPPoE  [ses 0xd5f] CHAP, Response (0x02), id 1, Value c9cf76a0089b655f54fd5433ad34420b, Name EXAMPLE@example
PPPoE  [ses 0xd5f] LCP, Echo-Reply (0x0a), id 0, length 10
PPPoE  [ses 0xd5f] CHAP, Success (0x03), id 1, Msg CHAP authentication success, unit 8020
PPPoE  [ses 0xd5f] IPCP, Conf-Request (0x01), id 29, length 12
PPPoE  [ses 0xd5f] IPCP, Conf-Request (0x01), id 1, length 12
PPPoE  [ses 0xd5f] IPCP, Conf-Ack (0x02), id 29, length 12
PPPoE  [ses 0xd5f] IPCP, Conf-Nack (0x03), id 1, length 12
PPPoE  [ses 0xd5f] IPCP, Conf-Request (0x01), id 2, length 12
PPPoE  [ses 0xd5f] IPCP, Conf-Ack (0x02), id 2, length 12
PPPoE  [ses 0xd5f] LCP, Echo-Request (0x09), id 0, length 10
PPPoE  [ses 0xd5f] LCP, Echo-Reply (0x0a), id 0, length 10
```

Also you can capture the headers of ethernet frames (it's data-link layer):
```
# pppd call provider
# tcpdump -e -i eth0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

00:23:8b:fb:f8:ef (oui Unknown) > Broadcast, ethertype PPPoE D (0x8863), length 32: PPPoE PADI [Service-Name] [Host-Uniq 0xD95C0000]
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE D (0x8863), length 118: PPPoE PADO [Host-Uniq 0xD95C0000] [AC-Name "STREAM"] [Service-Name "mtu"] [Service-Name "mgts"] [Service-Name "mgts.ru"] [Service-Name "MyLAN"] [Service-Name "mtu:stream"][|pppoe]
00:23:8b:fb:f8:ef (oui Unknown) > 00:30:88:00:65:e7 (oui Unknown), ethertype PPPoE D (0x8863), length 32: PPPoE PADR [Service-Name] [Host-Uniq 0xD95C0000]
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE D (0x8863), length 60: PPPoE PADS [ses 0x1d38] [Service-Name] [Host-Uniq 0xD95C0000] [AC-Name "STREAM"]
00:23:8b:fb:f8:ef (oui Unknown) > 00:30:88:00:65:e7 (oui Unknown), ethertype PPPoE S (0x8864), length 36: PPPoE  [ses 0x1d38] LCP (0xc021), length 16: LCP, Conf-Request (0x01), id 1, length 16
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE S (0x8864), length 60: PPPoE  [ses 0x1d38] LCP (0xc021), length 21: LCP, Conf-Request (0x01), id 106, length 21
00:23:8b:fb:f8:ef (oui Unknown) > 00:30:88:00:65:e7 (oui Unknown), ethertype PPPoE S (0x8864), length 41: PPPoE  [ses 0x1d38] LCP (0xc021), length 21: LCP, Conf-Ack (0x02), id 106, length 21
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE S (0x8864), length 60: PPPoE  [ses 0x1d38] LCP (0xc021), length 16: LCP, Conf-Ack (0x02), id 1, length 16
00:23:8b:fb:f8:ef (oui Unknown) > 00:30:88:00:65:e7 (oui Unknown), ethertype PPPoE S (0x8864), length 30: PPPoE  [ses 0x1d38] LCP (0xc021), length 10: LCP, Echo-Request (0x09), id 0, length 10
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE S (0x8864), length 60: PPPoE  [ses 0x1d38] CHAP (0xc223), length 33: CHAP, Challenge (0x01), id 1, Value c9cf76a0089b655f54fd5433ad34420b, Name a919-arb01
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE S (0x8864), length 60: PPPoE  [ses 0x1d38] LCP (0xc021), length 10: LCP, Echo-Reply (0x0a), id 0, length 10
00:23:8b:fb:f8:ef (oui Unknown) > 00:30:88:00:65:e7 (oui Unknown), ethertype PPPoE S (0x8864), length 58: PPPoE  [ses 0x1d38] CHAP (0xc223), length 38: CHAP, Response (0x02), id 1, Value c9cf76a0089b655f54fd5433ad34420b, Name EXAMPLE@example
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE S (0x8864), length 64: PPPoE  [ses 0x1d38] CHAP (0xc223), length 44: CHAP, Success (0x03), id 1, Msg CHAP authentication success, unit 7624
00:23:8b:fb:f8:ef (oui Unknown) > 00:30:88:00:65:e7 (oui Unknown), ethertype PPPoE S (0x8864), length 32: PPPoE  [ses 0x1d38] IPCP (0x8021), length 12: IPCP, Conf-Request (0x01), id 1, length 12
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE S (0x8864), length 60: PPPoE  [ses 0x1d38] IPCP (0x8021), length 12: IPCP, Conf-Request (0x01), id 229, length 12
00:23:8b:fb:f8:ef (oui Unknown) > 00:30:88:00:65:e7 (oui Unknown), ethertype PPPoE S (0x8864), length 32: PPPoE  [ses 0x1d38] IPCP (0x8021), length 12: IPCP, Conf-Ack (0x02), id 229, length 12
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE S (0x8864), length 60: PPPoE  [ses 0x1d38] IPCP (0x8021), length 12: IPCP, Conf-Nack (0x03), id 1, length 12
00:23:8b:fb:f8:ef (oui Unknown) > 00:30:88:00:65:e7 (oui Unknown), ethertype PPPoE S (0x8864), length 32: PPPoE  [ses 0x1d38] IPCP (0x8021), length 12: IPCP, Conf-Request (0x01), id 2, length 12
00:30:88:00:65:e7 (oui Unknown) > 00:23:8b:fb:f8:ef (oui Unknown), ethertype PPPoE S (0x8864), length 60: PPPoE  [ses 0x1d38] IPCP (0x8021), length 12: IPCP, Conf-Ack (0x02), id 2, length 12
```

**Cool!**


tcpdump it's awesone tool for network research. As usual, you find many useful info in manual: [http://linux.die.net/man/8/tcpdump]("http://linux.die.net/man/8/tcpdump")

---

### Post by linuxusr50 on 2010-09-13
utilitytrack,

This is exactly what I was looking for.  I see you did it on a PPPoE session but if you can do it with that I am sure there is a method to do it with on the PPPO interface that is created during the dial up process.

My current provider is DHCP only and uses no PPP on their network.  They do provide a username and password for a ppp dial up connection to be used as a back up for the broadband connection in the event of a failure, and that is what I had hoped to use for educating myself on the data link layer of a ppp session.

I found that wireshark would capture packets ok after the dialup ppp0 session had already been established.  That did not help much as all the packets at that point were standard TCP packets and did not show what happened at the datalink layer.

I will take another hard look at tcpdump to see if I can get the same information during a dialup session.  Thank you for your response.  I think you put me on the right track and I appreciate the examples.

---

