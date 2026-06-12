---
title: "upload traffic control using TC and NAT with iptables"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by mabol on 2012-11-06
Well, I'm trying to limit the upload traffic of an interface using tc, but it's giving me some headaches. Let me describe my environment.

I have a ubuntu server 12.04 which is a router. It has public IPs and private IPs. Every private IP has an interface.

When someone access and public IP the iptables translate this to a private and vice-versa (NAT).. Works greate, with no problem.

Now I'm trying to limit the traffic of the private interfaces, I use tc for download and upload.

I'm not sure if I chose the right rules.

For download I've created a htb qdisc on the interface with two classes, one for limit the traffic, just setting the rate to the speed I want and another class just to set a high priority and classify it on some ports with the iptables.

For upload, I create a ingress qdisc and after, a filter using some parameters which I didn't understand very well, it's kinda:

tc filter add dev ethx parent ffff: prio 3 protocol all u32 match ip src 0.0.0.0/0 police rate SPEED action drop burst 15k flowid ffff:a

I really don't know how to calculate the burst exactly and the flowid seems to me very weird 'cause it's a classless qdisc if I'm not wrong, so it doesn't have any class to set with flowid....

Besides that, the download rules above seems to work without problems, but the upload drop many packets preventing the site to load, even doesn't reaching the rate established in the rule. Don't know why this happens.

If it's necessary I can give more information. I've searched everywhere to understand that and found nothing to help me hehe.

Thank you!

---

