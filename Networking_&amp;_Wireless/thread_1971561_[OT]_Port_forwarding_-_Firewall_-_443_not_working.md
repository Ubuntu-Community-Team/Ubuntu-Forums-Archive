---
title: "[OT] Port forwarding - Firewall - 443 not working"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by dbrooke on 2012-05-02
Hello,
I put [OT] in the subject because this question has to do with my Apple Snow Leopard Server, but I am posting here because I know that it is unlikely that I'll get a knowledgeable answer at the apple discussions. ;-)

I am running a server-side language for my web server, and am trying to connect to a payment gateway with one of the sites running on that server. I am trying to connect via a tcp (telnet-like) connection on port 443. For some reason, my snow leopard server is blocking the connection.

I came to this idea because I can run the same code on my local laptop web server and get a response from the gateway just fine. 

So far, I've narrowed it down to 2 ideas that I can think of.

1.) My firewall on the Snow Leopard Server is blocking 443??

2.) My router could be an issue, which is doing port forwarding for port 443 and pointing incoming port 443 traffic to that same Snow Leopard Server.

However, I don't see how it could be #2 if the same code works on another machine in the same network as the snow leopard server.

So, I've checked my firewall settings and there is a rule in there to "allow tcp from any to any dst-port 443".

That should open it up right?

However, when I do:
'traceroute -p 443 <someSecureDomain>

from that server, it hangs with only one hop displayed.

When I do the same on my local dev machine, I get the full traceroute.

Not sure how to fix this.

Thx.

Donovan

---

### Post by dbrooke on 2012-05-02
Well, I ruled out the firewall by completely turning it off. Still having an issue connecting.

---

### Post by dbrooke on 2012-05-02
O.K., so the issue was the port mapping I had set up in my Airport Extreme router. After eliminating the line:

443 -> 10.0.1.70:443

My outgoing port 443 tcp connect (from 10.0.1.70) works.

The problem now is that I won't receive any port 443 requests to my webserver that is behind this router!

Any networking guru's out there have any suggestions?

I suppose I could get a block of I.P.'s from host provider so that I don't have to do port mapping in my router.

Donovan

---

### Post by dbrooke on 2012-05-02
Well, I spoke too soon.. the firewall *is* the problem.

 

There must have been a cache when I stopped it, which made it appear as if the fix was in the Airport Extreme. However, after turning the firewall back on, the issue came back. I've now done more testing, and the issue definitely involves the firewall.

 

I have the following Active Rule in the firewall:

 

'Allow tcp from any to any dst-port 443'

 

I am guessing that my server-side language "tcp connection" is not being matched to that rule. I was under the impression that the server-side "tcp connection" was basically like a telnet connection... Is there a different rule that I should put in to allow telnet connections on port 443? I guess I thought the same rule would apply for both.

My script now works, but I have no firewall for my web server. ;-)

... saga continues.

 
Donovan

---

### Post by dbrooke on 2012-05-02
O.K., I think I found the solution.

It appears that i needed to enable ICMP connections in my firewall. 

I suppose my outgoing port 443 requests (from both the traceroute and my server-side tcp connection) were met with ICMP responses. Since the ICMP responses were being denied by the firewall, the communication was lost.

Anyway, allowing ICMP in the firewall has fixed the issue.

Donovan

---

