---
title: "VPN and customized routing"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by September on 2009-10-02
Hi,

I'm using two computers, one at work and one at home, both ubuntu 9.04. The computer at work can use internet only through port 80 and some other ports like 22 and 110 and some others. Any port > 1024 is strictly non-accessible. So I've installed openvpn at my home computer and make it listen port 110. Since I don't have any other application listening port 110, it work just fine, I can make a connection between the work and home computers and I can even connect to the computer at work from home using the vpn channel.

The problem is, I've done this vpn setup so that I could use internet such as irc or internet radios from the computer at work. The next step after setting up the vpn successfully is to direct any connection/packet from the computer at work with port > 1024 to the home computer through vpn and then the home computer will redirect them to the internet. So I'll be able to use ports > 1024 from my computer at work.

My home computer has 10.8.0.1 on vpn and the computer at work has 10.8.0.6. The vpn interface is tun0 on both machines.

As far as I know, there are two steps. First one is to direct all connections/packers generated on the work computer to 10.8.0.1 (home computer). And the second step is to NAT the incoming connections/packets from 10.8.0.6 to internet, by masquareding. The second step must be relatively easy, one entry to the iptables on home computer and it should be done. But how to do the first step?

Thanks in advance

ps: it would be lovely if anyone writes he second step as well :P

---

