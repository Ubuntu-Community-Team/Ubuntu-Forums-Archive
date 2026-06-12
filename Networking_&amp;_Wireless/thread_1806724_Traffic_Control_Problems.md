---
title: "Traffic Control Problems"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by liuhb86 on 2011-07-18
I forwarded this post to Server Platform, which I think is more suitable.

Hello,

I want to set up a DNS server and due to cost restrictions, we need to limit the traffic extremely, about 30M bytes/month.

So I used the following command:

tc qdisc add dev eth0 root tbf rate 100bit burst 240mb limit 20kb mtu 1540

That means at 100bps, we can get about 30MB/month, and with a high burst, unused token can be accumulated so that if the net is idle for a long time, the following packet can be sent quickly using the accumulated tokens. 

However it doesn't works. Using tc qdisc ls. I get:

qdisc tbf 8008: dev eth0 root refcnt 2 rate 96bit burst 2293b lat 1515.5s

which means that burst is set to 2293b instead of 240mb. I think the large burst value with respect to small rate causes a integer overflow. So I don't know what to do now.

Does anyone know how to do that? 

TIA

liuhb

---

### Post by jmoorse on 2011-07-18
Let me make sure I understand: You need to limit upload and download to a total of 30 megaBYTES a month to a certain IP providing DNS resolution?  Is that correct?

---

### Post by liuhb86 on 2011-07-19
In short, I want to limit the outgoing(upload) traffic of my server  to 30 megabytes per month. 

Thanks,

Liu

---

### Post by jmoorse on 2011-07-19
I don't know if policing would be an effective way to handle this. 

If I am reading the qdisc documentation correctly the largest burst value you can have is 100% of the tokens, which would equate roughly to an additional 100bps burst in your case.  200bps would render any link unusable, and considering the IP header alone is 20Bytes it would take 1-1.6s just to handle the L3 encapsulation.

---

