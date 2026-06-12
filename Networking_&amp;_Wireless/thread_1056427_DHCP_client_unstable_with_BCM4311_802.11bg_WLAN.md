---
title: "DHCP client unstable with BCM4311 802.11b/g WLAN"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by VinzC on 2009-01-31
Hi.

I have installed Ubuntu 8.10 on a Dell Vostro 1000. It has a Broadcom BCM4311 wireless adapter. I used my home network to install it two or three weeks ago. I used it again probably once or twice with my home network until today.

Today I powered my laptop up again and it connected successfully to my home network when the network connection suddenly dropped while I was downloading updates. I could connect to my neighbour's wireless LAN and get an IP however :s.

I tried to connect several times again to my home network, in vain. On my DHCP server (it's dnsmasq-2.45 under Gentoo Linux) I can see DHCPDISCOVER and DHCPOFFER message pairs 4 times. This means BTW the wireless connection is established; the problem hence just lies within the DHCP client. I think the Dell laptop makes 4 attempts to get an IP address and gives up. I then get a notification "Network connection was closed" when I change to my home network manually.

I'm running dhcp3-client-3.1.1-1ubuntu2 on my Ubuntu laptop. Does anyone know how to cure that issue?

Thanks in advance.

---

