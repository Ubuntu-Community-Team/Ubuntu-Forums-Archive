---
title: "PPP problems"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by mpetty423 on 2009-09-09
Ok, so I have two ubuntu boxes connected to phone lines.  I would like to be able to use PPP to send IP data back and forth between each other.

I have one set as a PPP server, and the other one will just dial into it.

Neither of these machines are connected to the internet in any other way.  I just want to make a Point-to-Point (PPP) connection, and send some data around.


I can get them to both dial no problem.

In /etc/ppp/options on the server, I have (among other options)

```

asyncmap 0
defaulteroute
noccp
ipcp-accept-local
ipcp-accept-remote
10.0.0.1:10.0.100

```On the client, it's basically the same without the 10.0.0.1:10.0.0.100.

I can dial in fine, the link gets made, but no matter what I seem to do, I eventually get an error

```
LCP: timeout sending Config-Requests
```I've increased the number of times it tries to resend the config requests, and how long it waits, etc with no success.

I feel like I'm missing something pretty fundamental here.  But it's just two pppd's running, one as the server to dial into and one as the client dialing out.

But it just never fully configures the connection, and i have no idea why!  All of the online manuals talk about PPTP, and PPoE, and just dialing in, etc.  I can't seem to find a simple manual on how to just connect two computers via PPP.

Any help would be appreciated!

---

