---
title: "Strange network problem"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by vlebar on 2012-07-02
Hi,

I ave a very strange problem. A few days ago my ISP changed my ADSL modem. Afterwards everything was ok, but yesterday I noticed that some of the web pages arn't loading at all. Two examples are [https://www.facebook,com](https://www.facebook,com) and [https://login.live.com](https://login.live.com).

The problem is that this happens only on unbuntu machines (laptop & desktop), while on my windows laptop (running windows 7) works normally. The ubuntu desktop machine is connected to the router via network cable, the ubuntu & windows laptops via wireless.

For a router I'm using Linksys Wireless-G Broadband Router WRT64GL.

I haven't changed any settings on any of the computers or router. The only change is the new ADSL modem to which I connect via the router.

I'm thinking that the problem is in the https protocol but I don't know how to fix it.

Any ideas would be great.

Vasja

(I had to post this thread from the windows laptop, becouse I couldn't submit it from ubuntu)

---

### Post by ignaciop on 2013-02-25
Hello, i have the same problem but my router is Tp-link wr340g. I made a post but no one responds. If i know something i will post you. Bye.

---

### Post by vlebar on 2013-02-25
i found out that in my case it was a MTU problem.  I found the fix here
[http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows](http://superuser.com/questions/213264/cant-access-select-websites-on-linux-but-can-on-windows)

---

### Post by ignaciop on 2013-02-26
YES IT'S A MTU PROBLEM. HERE IS THE SOLUTION THEY GAVE ME:

sudo ifconfig wlan0 mtu 1456

---

