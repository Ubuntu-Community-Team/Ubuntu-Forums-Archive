---
title: "Wired Network Problem on New Install"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by canbonly on 2009-09-09
Let me start off by saying I am new to Ubuntu and Linux buy not computers and networks. I just did a fresh install on a brand new hard drive of Ubuntu 9.04 Jaunty Jackalope release. The install appears to have gone well except I can get my network card to connect. I did the install on an old HP m1170n and according to the HP website the network card, which is built in to the mother board, is a Realtek RTL8101L. I went to the realtek website and it says the drivers are built into the kernel. When I click on the network manger icon in the top right corner of the screen it tells me the card is disconnected. I connect to a cable modem through a linksys wrt54g router. I know the wired connect is good because I plugged another computer into the connection and all works fine. I have searched through many websites and I have changed the /etc/NetworkManger managed from false to true. The connection is DHCP and yes I have checked to make sure I have some addresses available. In the /etc/network/interfaces file it shows:

auto lo
iface lo inet loopback

I have also tried adding
auto eth0
iface eth0 inet dhcp

with no luck. I can edit the connection it the card shows up as auto eth0 and is set to Auto but it is like the card is not recognizing that it has a network cable plugged in to the card. Any help would be greatly appreciated and I really want to learn more about Ubuntu. Thank you in advance for all your help with this issue.

Carl

---

### Post by canbonly on 2009-09-09
Well I solved my own problem. All that trouble shooting and I forgot the first rule of networking check the card. Turns out the card must have been bad. Disabled the on board network card and put one in a PCI slot and it came right up and worked. Oh well live and learn.

Carl

---

