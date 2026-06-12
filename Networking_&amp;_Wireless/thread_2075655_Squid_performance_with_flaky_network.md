---
title: "Squid performance with flaky network"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by JamesSMurray on 2012-10-24
(First time poster here and I've not found an answer after a bit of searching.)

I was diagnosing a network problem on a customer's site yesterday. They use squid on ubuntu (11.x) and connect to the 'net via one of two ADSL lines.

Connectivity to the main business site they used had slowed to an impossible crawl. But other sites (bbc, google) were working fine. That site works mostly ok if I hook my (XP) laptop directly to the ADSL router, taking maybe 10 seconds to load a page, but can take multiple minutes to load via squid/ubuntu.

Turns out there was end to end packet loss, when the other site pinged us, but I wasn't seeing any losses pinging from here.

I took some packet traces with Wireshark and late last night found some disturbing behaviour.

There are a lot of re-transmissions, ACK dupes and fragmented packets. But, the killer seems to be the retry timeout on the TCP Retransmissions.

One .js item on the page is effectively taking 75 seconds to load.

Here's a re-typed fragment of the packet trace:

4.91  192.168.2.4  65.161.xx.xx  HTTP 723 [TCP Retransmission] GET /modules/scripts/gloassarymanager.js HTTP/1.0
then same again at 9.87, 19.79, 39.62, 79.3 before it finally gets a reply.

Is this squid or the lower TCP layer?

While obviously I want the packet loss problem out there on the internet to be resolved, I'm left wondering why squid/Ubuntu are handling this problem so much worse than Windows XP is.

I tried with a much older Linux box and it wasn't so badly impacted.

any help appreciated

regards

James Murray

---

