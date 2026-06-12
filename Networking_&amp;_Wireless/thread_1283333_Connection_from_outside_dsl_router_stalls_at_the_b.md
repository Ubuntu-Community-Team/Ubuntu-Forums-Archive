---
title: "Connection from outside dsl router stalls at the begin"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by bterkuile on 2009-10-05
I have a strange problem and have not found a solution after long searching all kinds of fora.

The problem:
When I access my computer when I am not at home the connection stalls for a moment, and then the connection is fast again.

My Setup:
Jaunty 9.04 64bit updated today, still have the problem. Internal ip:
192.168.1.7
router is at: 192.168.1.1
I forwarded all incoming traffic from port 1 to 10000 to 192.168.1.7 from the router using NAT.
The computer is connected to the router with a cable.

Situation:
When I access my computer from outside using:
ssh username@outside_ip
It directly asks for a password. After typing the password, I directly see the bash. When I do a directory listing ls -la, the first few entries of the directory are displayed (say: . .. Desktop etc), then the connection seems to stall for about ten seconds, and then the rest of the directory is displayed. The second time directory listing is fast. Sometimes when I open a file using vim the connection seems to stall again, but I did not noticed a strict reproducible pattern in this. 

When accessing from within the local network with another computer, ssh username@192.168.1.7, there is no problem at all.

This problem came up on a Kubuntu installation, but to really test it I installed the server edition of jaunty 9.04 64bit and the fresh installation of this one had the same problem. 

I suspect that it may have something to do with the router or dns settings, but I don't know how to resolve it.

ps.
/etc/resolv.conf
192.168.1.1

ps2
The router distributes ip addresses using DHCP

A beer for the answer, because it is a bit annoying :)

Benjamin

---

