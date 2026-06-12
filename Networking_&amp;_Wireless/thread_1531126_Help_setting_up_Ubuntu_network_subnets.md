---
title: "Help setting up Ubuntu network subnets"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by lkytmr on 2010-07-14
Tom 

--------------------------------------------------------------------------------

I am a long-time windows user and am new to Ubuntu although I am quickly becoming a fan. I understand networking from a user's perspective but I am by no means an administrator. Most of the help seems to be aimed at administrators so I would plead for some non-techie type help.

I have installed ubuntu server and added my own wiki.

Our office has 3 subnets.

164.4.166.xxx
192.168.1.xxx
172.26.3.xxx

I would like to set the Ubuntu server up as a router so that no matter which subnet someone in the office is on, they can connect to the wiki.

Is setting the server up as a router the right path and can anyone give me some guidance as to how to accomplish this?

Thanks
Tom Ryan

---

### Post by YesWeCan on 2010-07-14
Hi Tom. I started using Ubuntu nearly a year ago. It is fantastic.
There are much more expert people than I in this forum but I imagine what you want to do is easily achievable.

The linux box just needs to have 3 IP addresses, one in each subnet. I believe you can use a single NIC to receive packets from multiple subnets and to present multiple IP addresses to the LAN. So if the 3 subnets are on physically separate LANs then you either need a switch and a single NIC or 3 NICs. That's about it. No need for router functionality.

You need a router when you need to transfer packets from one subnet to another. That's not what you seem to need. You are transferring packets from multiple subnets to a single device.

However, if you have roaming user machines such that you need your server to have the same IP address reachable from any subnet it is more tricky. Typically, an IP address that is not within a subnet range is sent to the subnet's default gateway, usually a router. So in this case you would need each subnets default gateway to redirect packets to your server if they have your servers IP address.

Ubuntu's iptables facility is so flexible and powerful that you can make it behave as a router or almost any kind of packet handler you wish.
Brian

---

