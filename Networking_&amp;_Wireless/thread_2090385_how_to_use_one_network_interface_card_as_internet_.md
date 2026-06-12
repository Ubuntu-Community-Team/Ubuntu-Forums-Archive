---
title: "how to use one network interface card as internet gateway..!!"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by adym3333 on 2012-12-02
I want to set up internet gateway for my home to make use of my old system having lubuntu on it .. pc only having 1 network interface card ... so how i can use it for internet gateway i mean obviously this pc will be forwarding internet traffic to other pc's ... Just want to know how i can use single nic for gateway instead of two .:confused:.. ??want create below given network scenario ...

ISP (internet Router) -------> My.old.pc.as.gateway  -------> Other Users PC 

Actually after this i will be using this gateway as firewall ...

---

### Post by 2F4U on 2012-12-02
If you want to use that PC as a gateway, the machine need 2 network devices. One connects to the outside world, the other connects to your internal network and a DHCP server is running on this interface. The web is full of tutorials on how to do it, here is just one example

[http://rbgeek.wordpress.com/2012/05/14/ubuntu-as-a-firewallgateway-router/](http://rbgeek.wordpress.com/2012/05/14/ubuntu-as-a-firewallgateway-router/)

---

