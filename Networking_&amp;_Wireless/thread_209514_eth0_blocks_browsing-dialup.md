---
title: "eth0 blocks browsing-dialup"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by RichardR on 2006-07-05
A Linux new-be point of view.

In my original post I was trying to resolve a problem I had browsing the Internet using a dial up connection. Any browser failed to resolve a url for viewing. I experienced the problem using ubuntu (live cd and HD), knoppix live cd and SuSe 10.1. I determined the problem was with the eth0 (NIC) being active. When I disabled the NIC by various methods, I was then able to browse using a browser.

To complicate the problem further, Firestarter (firewall) won't activate. 

If you use ifconfig (relative to this discussion), I found lo and ppp0 active, eth0 is inactive. When I try to start Firestarter, it fails to activate because device eth0 isn't active.

If I activate eth0 I'm unable to to use a browser. Further investigation determined I have to use ifup and ifdown with various options to control activation of eth0. Sometimes ifdown and ifup are effective, depending on the flavor of Linux.

A further problem occurs with the dial up connection (ppp0) since it updates resolv.conf. Dial-up uses resolv.conf to resolve url's vie DNS.  eth0 also uses resolv.conf. eth0 uses a gateway address (192.168.1.1) to get the attention of the router to access ADSL to access the DSL modem. In my case ppp0 is using 63.71.176.250 and 63.71.176.245 DNS servers. So the question is what (eth0/ppp0) is going to control the resolv.conf file?

One further point, this isn't generally a problem in windows 2K Pro. I can access My Network and dial-up at the same time seamlessly. Meaning I have to change my mind set or find a work around when using Linux. 

I also know this is a tcp/ip configuration problem. This is relative to both Windows and Linux.

---

### Post by one norse on 2006-07-05
I have the same problem:

If eth0 is enabled, browsers, email, and even ADEPT will not talk to ppp0. That is making my dream of one printer in the house accessed by wireless network impossible until I get a work-around in place.

---

### Post by RichardR on 2006-07-05
I hear you!

My thoughts are running to digging into the kernel and making eth0 use another file for resolution of DNS. That's been a process I've been avoiding ever since I heard the word Linux in the early  nineties. Too lazy!

The problem isn't as bad using SuSe 10.1. I can easily use ifup and ifdown. I could proably do it with a  script. Problem is I prefer ubuntu for many reasons over SuSe. Ubuntu boots very much faster that SuSe.

Stay tuned!

---

### Post by one norse on 2006-07-16
I finally got the problem apparently fixed, at least I can have eth0 up and running while using ppp0 to talk to the internet. I haven't tried to configure eth0 to do anything, but progress, notheless. The step that worked was adding two options to the /etc/ppp/options file:

defaultroute
replacedefaultroute

These are pppd options, and more info can be found in the pppd man page (help->search pppd) or man pppd in a terminal.

---

