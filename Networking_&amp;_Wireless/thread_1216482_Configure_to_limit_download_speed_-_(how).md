---
title: "Configure to limit download speed - (how?)"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by Darktrax on 2009-07-18
There are plenty of posts about getting the speed UP, but none I can readily find on throttling it a bit.

Our ADSL router is shared, and we are also at a rural location where the download speed is decided more often by the length and quality of our line than any limitation from the website server.

If I just start downloading, my Ubuntu will often max out the capacity, leaving all others using the internet here with a unresponsive system, until I quit. So is there some configuration line I can put somewhere to make Ubuntu less greedy? I need to cap the maximum download speed.

My thanks
G

---

### Post by Kraut~salat on 2009-07-18
the key word for you is "traffic control". It is done in Linux with the tc command. google that in connection with "token bucket filter", that should get you started.

tc qdisk add dev eth0 root tbf rate 125kbit latency 50ms burst 1540

is an example of how to limit traffic of the eth0 interface to 125kbit.

---

### Post by jerrrys on 2009-07-18
i don't do that, but found this

[http://www.google.com/search?q=limit+download+speed+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=limit+download+speed+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

also

[http://www.google.com/search?q=limit+download+speed+firefox&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=limit+download+speed+firefox&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Brandon Williams on 2009-07-18
Instead of limiting download speeds for the whole system, you might want to consider using a specialized tool to limit download rates for large file downloads. For example, if you download with wget on the command line, you can explicitly specify a rate limit with the --limit-rate flag. To limit download rate for apt-get, [look here](http://linux.derkeiler.com/Mailing-Lists/Debian/2008-02/msg01872.html).

---

