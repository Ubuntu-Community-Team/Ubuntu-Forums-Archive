---
title: "DNS search doesn't stop after a match, so it slows down connections"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by sergiR on 2013-05-22
Hello,

First of all I would like to explain the configuration I've got in order to understand the problem.

I have two different networks, every network with a domain (domain1 and domain2) and a dns server (dns1 and dns2).

Computers of domain2 has the following resolv.conf:

> 
domain domain2
search domain2 domain1
nameserver ipDns2
namserver ipDns1


When a computer of domain2 makes a ping to other computer (for example computerA) in domain2 I can see using ngrep in port 53 that it asks computerA.domain2 to the dns2, it get the answer and the ping is performed. Ok, this is the behaviour I want to have.

But when a ssh is made to computerA I see with ngrep that it asks for computerA.domain2 (it gets an answer), and then it continues asking computerA.domain1... dns2 doesn't know it so it asks to dns1.

And here is the problem I have, the connection with dns1 is sometimes bad, it can fail so it is very probably to have timeouts.
So, this is what I don't understand. If the resolver has a match with the first domain search why it continues searching the other domains?

The communications inside domain2 depends on the connectivity with dns1, because even trying to connect computers inside this domain2 they try to connect to dns1.

Is there any way to configure resolver in order to stop when the first match is achieved?

Thank you for your help.

---

