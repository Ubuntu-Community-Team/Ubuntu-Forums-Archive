---
title: "Monitoring internet usage in a serverless network"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by tabibito on 2009-02-03
Hello, this is just a newbie's first post so go easy on me please.

I have an Prolink Hurricane 9200R ADSL modem+ router in my office, which its internet connection is then shared to several desktops and notebooks through a Linksys WRT54G wireless router.

What I want to know is, am I able to monitor the bandwidth usage of each computers from my notebook (mine is also connected to the internet through the wireless router).

I've been looking around a bit and found some softwares such as ntop, but they all seem have to be installed on a server computer, which we don't have. 

I am currently using Dell Latitude D610 with Ubuntu Intrepid 8.10. Any help anyone?

---

### Post by Kebabman on 2009-02-03
That would depend how adventurous you are :)

I have a wrt54g at home but it is flashed with [OpenWRT]("http://openwrt.org/") (a version of linux). It still acts as my wireless router but I can do a lot mroe with it such as bandwidth monitoring etc. It's not always ideal for everyone but it does have a web itnerface for most things so it's fairly easy to use.

---

### Post by tabibito on 2009-02-03
Thanks for the reply Kebabman. I've tried to use WRT before but my version of router (WRT54G v7.0) is not supported. If possible I want to rule out flashing my router. I would get in trouble should something happen to it :(. Thanks anyway.

---

### Post by Kebabman on 2009-02-03
Without using that you would have to either install something on to your router that would monitors all the traffic going through the WAN port (such as [bwlog]("http://www.hetos.de/bwlog.html") which still won't run on the official firmware :(). Or install some sort of monitoring app on each pc that you want to check. It depends really if you want to monitor each individual pc or just the total amount of traffic leaving your network.

---

### Post by tabibito on 2009-02-03
Well, what I would like to do is to monitor each PC's traffic usage. It seems like something is dragging down our connection and I want to know where it comes from. Seems like turning one of our desktops to a server is my only option afterall.

---

### Post by Kebabman on 2009-02-03
Unfortunately that may be the best way, although if you have a bit of cash you could buy an old wrt54g for cheap and flash it with linux. That way you always have the new one to fall back to should anything go wrong. You can get them very cheaply i believe and it's good fun and a good thing to learn.

---

### Post by tabibito on 2009-02-03
I'll consider that option. Thanks for the help :D.

---

