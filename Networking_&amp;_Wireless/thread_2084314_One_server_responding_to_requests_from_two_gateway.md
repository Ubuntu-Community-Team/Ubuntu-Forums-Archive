---
title: "One server responding to requests from two gateways."
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by Cyphix on 2012-11-15
The idea is conceptually easy - giving my Ubuntu Server two IP addresses, which are reached through two separate ISPs.

Objective - the server answers to two separate IP addresses, and sends responses to two different gateways based on which IP address it is answering as.

Problem - The server has one NIC, and must respond through the same gateway the request comes in from. The idea is that each IP address the server responds to is linked to a gateway to respond through.

What I've tried:

[http://unix.stackexchange.com/questions/4420/reply-on-same-interface-as-incoming](http://unix.stackexchange.com/questions/4420/reply-on-same-interface-as-incoming) or [http://ubuntuforums.org/archive/index.php/t-2035163.html](http://ubuntuforums.org/archive/index.php/t-2035163.html) - ip rules and routes, but these seems to fail due to only having one hardware NIC. ip route does not seem to recognise eth0:0 as a separate interface.

Aside from that, I've looked up things all day on this, and it seems that if there was a driver to create a virtual NIC (ie. eth1 not eth0:0) that it should be possible.

Question - Is there a way to achieve my objective? (Without installing a second NIC.)

---

