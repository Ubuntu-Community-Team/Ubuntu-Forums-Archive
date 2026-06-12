---
title: "dnsmasq server config options not working"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by irose123 on 2012-03-22
I have set up a Ubuntu 10.04 LTS desktop machine with 2 interfaces (eth0 and wlan0). wlan0 acts as a wifi access point using hostapd.

dnsmasq is installed OK, and everything works so that locally on that machine DNS works fine as normal, but connections over wlan0 get everything routed to localhost. This means for example that you can view a website using firefox on the local machine, but connect via wlan from a phone, for example, and you get routed to an internally hosted website. All well and good so far.

I want to add domains that will be excepted from this default behavior, for example to allow someone connected via wlan to be able to tweet from the internal website. I have tried using both the server and address options in the dnsmasq.conf file, but neither work.

[B]#This has no effect at all:
server=/twitter.com/#

#Neither does this:
server=/twitter.com/192.168.1.254@eth0[/B]

Where 192.168.1.254 is the IP address of the router it's attached to via eth0 and the gateway to the internet. Nor does replacing this IP address with the DNS lookup addresses specified in the router config. IP address for twitter.com is gives 10.0.0.2 as before, the address of this machine via wlan0.

Alternatively trying something like the following seems to resolve addresses OK, but makes a browser on the wireless connected device (eg phone) hang:
[B]
address=/twitter.com/199.59.150.7
address=/twimg.com/184.169.81.33
address=/ssl.google-analytics.com/173.194.41.94
address=/www.google-analytics.com/173.194.41.137[/B]

Any ideas what is going on? Why doesn't the server option have any effect at all?

Thanks.

---

### Post by irose123 on 2012-04-16
Hello? Anybody there?!

---

