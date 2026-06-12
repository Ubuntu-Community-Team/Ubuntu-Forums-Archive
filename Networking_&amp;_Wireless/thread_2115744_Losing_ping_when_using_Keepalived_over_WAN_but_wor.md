---
title: "Losing ping when using Keepalived over WAN but works locally."
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by AsherSevyn on 2013-02-13
I am tasked with setting up redundancy on two load balancers (using Haproxy & Keepalived). The idea is that we will have a load balancer managing our site but we need that load balancer to have a backup. 

I am having trouble pinging a load balancer server through a VPN. I'm using keepalived for a failover to keep the load balancers redundant. The failover works fine locally (when it's within its own network) when I test it but it doesn't succeed through the VPN. Somehow the request is getting mapped to the master LB's mac even though they both share the same virtual IP as this is the function of keepalived, to allow a hand off in case of a failure. The pings are continuous through VPN till the failover happens. What do I have to do on my network to allow the ping to succeed with a failover through a VPN?

Here's the detailed version:

LB0 = XXX.XXX.XXX.104 (Shared failover virtual IP) This is what all traffic is directed towards.

LB1 = XXX.XXX.XXX.70 (This is the master LB but the 104 is what the network sees)

LB2 = XXX.XXX.XXX.103 (This is the backup. During failover this gets the 104 otherwise it's 103)

We host our website in a colocation facility. We work in a remote office. We have a load balancer that serves our website which has a fail over. The fail over is using an app called Keepalived. Keepalived shares a virtual address with both the failover and the master load balancer. If a fail over occurs the slave LB will assume the shared address that previously belonged to the master LB. Here's the catch. We know keepalived works internally and hands off the address to the failover seamlessly like nothing ever happened. We have tested this within our live site network. Pings are constant locally to the private IP when the failover occurs. Something about hitting it externally over the VPN that is somehow binding the expected mac address and not accepting when it changes regardless of the fact that the IP has been assumed by the failover. When we do a constant ping on the LB and we restart it (Testing the failover) the ping breaks from our office VPN connection but a local ping from within the live site network keeps replying. 

What's the cause of this?

I should mention that our VPN has a one way trust from our Live Site to our Local Office. Not sure if that has anything to do with it.

Thanks in advance!

-Ash

---

