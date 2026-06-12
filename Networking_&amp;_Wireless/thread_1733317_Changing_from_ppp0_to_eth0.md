---
title: "Changing from ppp0 to eth0"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by oygle on 2011-04-19
Hi,

Have been using a mobile broadband connection (USB dongle direct to computer) on one computer, and sharing the internet connection via ethernet to another computer.

This is the setup

ppp0 <--> Computer A <--etho--> Computer B

Both computers are running Ubuntu, although Computer A is dual boot (to XP or Ubuntu)

The new equipment is a modem/router - [Billion 7404VGPX]("au.billion.com/product/voip/bipac7404vgpx.php") . It can use a 3G connection, so I can still use the USB dongle, and just plug it into the router and not to the computer.

The new connection from the router to each computer will be via ethernet.

I will need to completely "wipe" iptables (flush I mean) on both computers, and I think I run ufw/gufw on both, so that would need to be uninstalled. The router is very secure, has NAT, etc, etc, and I'd rather setup all that side of things in one point, rather than on each computer.

Can someone please advise how to flush iptables, and also advise on how to setup the connection via ethernet from each computer to the router/modem.

Thanks,

Oygle

---

