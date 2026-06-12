---
title: "Merge two ADSL connections on ubuntu server"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by md9568 on 2012-07-07
Hi all,

I have two questions.

01. My company is having two ADSL connections. I want to know how to combine them to a Ubuntu server and configure squid proxy server on that.

02. Also I need to send only [COLOR=Red]**YouTube traffic**[/COLOR] from one ADSL line and Other ADSL link for the normal internet browsing.

Greatly appreciate, If anyone can give me a solution for this.
Thank you....

---

### Post by Kirk Schnable on 2012-07-11
Your work got a dedicated DSL connection for YouTube?  Must be a nice place to work.

To make good use of two separate Internet connections, "merge" them as you say, you want a Link Load Balancer.  At work, we just installed an Ecessa PowerLink which is an expensive appliance designed to do what you want to do.

However, you can do it with iptables.  I have not followed this guide, but it looks comprehensive and it might get you started:
[http://blog.khax.net/2009/12/01/multi-gateway-balancing-with-iptables/](http://blog.khax.net/2009/12/01/multi-gateway-balancing-with-iptables/)

As far as tagging "YouTube" traffic, that's not going to be very easy.  You can tag traffic in iptables by destination IP, but you'd need a list of IP addresses Google uses for YouTube.

Load balancing the two connections will be easy.  Reliably pushing YouTube to only one connection, probably not.

As far as your Squid Cache\Proxy, check this out: [https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

Kirk

---

