---
title: "Ping ok, but no Internet"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by bot2k9 on 2009-07-08
Hello,

I installed Cruncheee (ubuntu variant) recently on my EEE 1000h, and got everything working like a charm.

At university, I have to use a vpn connection, so I installed vpnc (like on my old laptop) and could connect, no problems.

Then, after the first time I used vpnc at university, I came home and bam, no internet.
So what's wrong?

I have no idea.
The "host" and "ping" commands are working,
I can ping [www.google.com](www.google.com) and 74.125.77.99 , so no problem there.
Host gives me the ping of the page, everything ok.

Firefox and mail, apt-get update don't work.

One strange behaviour though, when I give "wget www.google.com", it saves index.html .  No luck with pictures though.

I read somewhere in a forum that there was a DNS problem with my router, but my question: 
Why did it work before my connection with vpnc?
Why are the other pc's (also ubuntu variants) still working?

When I try to enter the two DNS ip's of my router, it network-admin accepts it, but after I connect to my wlan, it changes back to my routers ip (192.168.1.1). 
Trying to edit /etc/resolv.conf makes no difference, as it changes back to what it was before after connection.

Do you have any idea what I can do?
A netbook without net is like a car without tires..

---

### Post by bot2k9 on 2009-07-09
Well, don't bother anymore,

removing vpnc using apt-get did the trick for me.

I still don't know why vpnc, without launching it, always reset my /etc/resolv.conf to a bad nameserver.

Greets, Chris

---

