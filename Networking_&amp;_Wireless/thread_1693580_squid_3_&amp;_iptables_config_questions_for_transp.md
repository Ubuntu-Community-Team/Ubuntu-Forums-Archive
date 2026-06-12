---
title: "squid 3 &amp; iptables config questions for transparent proxy"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by keevill on 2011-02-23
I am trying to set up my squid3 proxy as a transparent proxy - right now, I have to manually configure browsers to access via proxy.
I understand that I have to put some rules into Iptables and also some further directives in the squid.conf.

I have a couple of specific questions.
The proxy server is running on a Ubuntu 10.04 workstation and this machine also acts as a dhcp server for the network. I have just one subnet , namely 192.168.0.1-254
There is only 1 network card. Is it much easier to put in a second network card or is it just as easy to configure the existing lan card as a dual IP ?

Is it necessary to configure these 2 IP's ( whether they are via 2 lan cards or dual IP on single card ) to be on different subnets.
i.e ETH0 192.168.0.1 and ETH1 192.168.1.1  or is ok to have something like 
ETH0 192.168.0.1 and ETH1  192.168.0.254
( where  ETH0 is the one facing the LAN and ETH1 points to the modem router / switch i.e The Internet )
Where specifically do I save the Iptables rule configuration file and what must I call it ?
-keevill-

---

