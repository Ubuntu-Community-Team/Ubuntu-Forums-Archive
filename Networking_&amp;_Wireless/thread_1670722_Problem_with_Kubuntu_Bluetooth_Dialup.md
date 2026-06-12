---
title: "Problem with Kubuntu Bluetooth Dialup"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by sandyford on 2011-01-19
Hi. 

I'm having problems to get my phone work as a bluetooth modem. Phone is Nokia E65 and I'm using Kubuntu 10.10.  I'm trying to use ppp for connection.

Everything seems to be okay, I've found a few websites which I have used as advice.

Anyhow, even my configuration seems to be okay, I get this output when initiating the connection:

```

Script /etc/ppp/dna-connect-chat finished (pid 2125), status = 0x0
Serial connection established.
using channel 4
Using interface ppp0
Connect: ppp0 <--> /dev/rfcomm0
sent [LCP ConfReq id=0x1 <asyncmap 0xa0000> <magic 0x2644fa0c>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0xa0000> <magic 0x2644fa0c>]
sent [LCP ConfNak id=0x1 <magic 0x770b5b44>]
rcvd [LCP ConfNak id=0x1 <magic 0x770b5b44>]
sent [LCP ConfReq id=0x2 <asyncmap 0xa0000> <magic 0xf5e54c25>]
rcvd [LCP ConfReq id=0x2 <asyncmap 0xa0000> <magic 0xf5e54c25>]
sent [LCP ConfNak id=0x2 <magic 0x420a15e8>]
rcvd [LCP ConfNak id=0x2 <magic 0x420a15e8>]
sent [LCP ConfReq id=0x3 <asyncmap 0xa0000> <magic 0xcc1d8820>]
rcvd [LCP ConfReq id=0x3 <asyncmap 0xa0000> <magic 0xcc1d8820>]
sent [LCP ConfNak id=0x3 <magic 0x2f4651f2>]
rcvd [LCP ConfNak id=0x3 <magic 0x2f4651f2>]
sent [LCP ConfReq id=0x4 <asyncmap 0xa0000> <magic 0x2845e190>]
rcvd [LCP ConfReq id=0x4 <asyncmap 0xa0000> <magic 0x2845e190>]
sent [LCP ConfNak id=0x4 <magic 0xc7d9372c>]
rcvd [LCP ConfNak id=0x4 <magic 0xc7d9372c>]
sent [LCP ConfReq id=0x5 <asyncmap 0xa0000> <magic 0xea3e1a53>]
rcvd [LCP ConfReq id=0x5 <asyncmap 0xa0000> <magic 0xea3e1a53>]
sent [LCP ConfNak id=0x5 <magic 0x42be329f>]
rcvd [LCP ConfNak id=0x5 <magic 0x42be329f>]
sent [LCP ConfReq id=0x6 <asyncmap 0xa0000> <magic 0x417fe8da>]
rcvd [LCP ConfReq id=0x6 <asyncmap 0xa0000> <magic 0x417fe8da>]
sent [LCP ConfNak id=0x6 <magic 0x24c6f63e>]
rcvd [LCP ConfNak id=0x6 <magic 0x24c6f63e>]
sent [LCP ConfReq id=0x7 <asyncmap 0xa0000> <magic 0xf0c57953>]
rcvd [LCP ConfReq id=0x7 <asyncmap 0xa0000> <magic 0xf0c57953>]
sent [LCP ConfNak id=0x7 <magic 0xd09843d3>]
rcvd [LCP ConfNak id=0x7 <magic 0xd09843d3>]
sent [LCP ConfReq id=0x8 <asyncmap 0xa0000> <magic 0xf6dc125f>]
rcvd [LCP ConfReq id=0x8 <asyncmap 0xa0000> <magic 0xf6dc125f>]
sent [LCP ConfNak id=0x8 <magic 0x5a12229e>]
rcvd [LCP ConfNak id=0x8 <magic 0x5a12229e>]
sent [LCP ConfReq id=0x9 <asyncmap 0xa0000> <magic 0xba54fa4d>]
rcvd [LCP ConfReq id=0x9 <asyncmap 0xa0000> <magic 0xba54fa4d>]
sent [LCP ConfNak id=0x9 <magic 0x1dd23e80>]
rcvd [LCP ConfNak id=0x9 <magic 0x1dd23e80>]
sent [LCP ConfReq id=0xa <asyncmap 0xa0000> <magic 0xd24387ed>]
rcvd [LCP ConfReq id=0xa <asyncmap 0xa0000> <magic 0xd24387ed>]
sent [LCP ConfNak id=0xa <magic 0xe2f080ab>]
rcvd [LCP ConfNak id=0xa <magic 0xe2f080ab>]
Serial line is looped back.
sent [LCP TermReq id=0xb "Loopback detected"]
rcvd [LCP TermReq id=0xb "Loopback detected"]
sent [LCP TermAck id=0xb]
rcvd [LCP TermAck id=0xb]
Connection terminated.
Script /etc/ppp/dna-disconnect-chat finished (pid 2132), status = 0x0
Serial link disconnected.

```

What might be wrong?

---

