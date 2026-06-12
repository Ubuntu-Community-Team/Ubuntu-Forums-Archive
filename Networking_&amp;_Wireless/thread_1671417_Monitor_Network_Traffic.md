---
title: "Monitor Network Traffic"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by Billisnice on 2011-01-20
Is there an easy way to monitor network traffic? I want to make sure my kids are surfing safe...

Thanks

---

### Post by endotherm on 2011-01-20
well, there are a couple ways, but the best is probably to set up a proxy server, but depending on your resources and technical background that can be quite troublesome (or easy) to implement. [http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

another easier but slightly less enforcable method would be to subscribe and configure for [opendns]("http://www.opendns.com/"). they have some dns resolution filtering services that might work for you. they are commercial services however and I have no idea how much they cost.

the least enforcable are client end loggers like [this]("http://ubuntuforums.org/showthread.php?t=550287") or filters like [this]("http://ubuntuforums.org/showthread.php?t=843510")

---

### Post by dBuster on 2011-01-20
If you have just the one computer I have no answers.

If you have a network at home most routers now a days have the ability to restrict access to certain websites.  If that is not your cup of tea, then there is software, and for the life of my I can not remember what it is, but I can monitor my network traffic at home.  Simple easy configuration and I see all traffic or just the traffic I want to see.  If I was at home I would have it but here at work I do not.

Check this out: [Network traffic analyzers for Ubuntu System](http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html)

---

### Post by dBuster on 2011-01-20
If you have just the one computer I have no answers.

If you have a network at home most routers now a days have the ability to restrict access to certain websites.  If that is not your cup of tea, then there is software, and for the life of my I can not remember what it is, but I can monitor my network traffic at home.  Simple easy configuration and I see all traffic or just the traffic I want to see.  If I was at home I would have it but here at work I do not.

Check this out: [Network traffic analyzers for Ubuntu System](http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html)

---

### Post by endotherm on 2011-01-20
@Op:
on terminology, one thing to consider: network traffic monitoring will not usually provide the data on the high level you want it. Wireshark, darkstat, and etherape are great tools for low level (packet by packet) analysis, and global statictics, but they won;t give you a readable list of the sites the kids visit. that info is there, but the details are often so fine that you will not be able to answer your question without a lot of work analyzing the data. 

instead you will likely find much better results looking for "Usage monitoring" software instead of traffic monitoring.

---

### Post by Backharlow on 2011-01-21
I agree with endotherm. Opendns is a free service with parental type settings to block adult content. It also generates network analysis of your web habits. Because it is DNS, there is nothing to install on your machine, just get a free account, and add their DNS IP to your network connection.

---

