---
title: "Bond Two EVDO Cards"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by robTard on 2009-01-14
Hello,

I have two Sprint Novatel U727 EVDO cards.  I am curious
as to whether there is any way to bond these two cards together
into a single interface bond0.  

My reasons for wanting to do this is because I would like
to run a NAT on my machine where the wireless card is the
access point and any outgoing connections go to either of 
the EVDO interfaces.

I have set up this functionality with these three lines:
iptables -A FORWARD -i ppp+ -o ath0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ath0 -o ppp+ -j ACCEPT
iptables -t nat -A POSTROUTING -o ppp+ -j MASQUERADE

And it seems to work correctly, except that when I look
at which interfaces are active in wireshark, only ppp1 is
spitting out packets (ppp0 is entirely inactive).

Any suggestions welcome.

---

### Post by irw on 2009-01-21
A very good question!

I am trying to setup an old PC as a file server and use it to share an evdo internet connection with other PCs on my network.

Where I am the local DSL connection is as slow as dial-up some days, and expensive.I have an evdo USB card that is faster and one third of the price, and to enable us all to access the web with reasonable speeds, I am considering a second - but only if I can use the two together!

Any pointers gratefully received.

---

