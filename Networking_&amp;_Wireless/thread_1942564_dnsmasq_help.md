---
title: "dnsmasq help"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by jwsicomputing on 2012-03-17
Hi there,

I am trying to configure my Ubuntu desktop machine into a dhcp server for my network
Here is my setup:

I have a satellite Internet modem which has primitive dhcp (rubbish can't handle more than 4 pcs through LAN) I would like to route the LAN from the modem to the Ubuntu machine let dnsmasq change the subnet from 176.227.x.x to 192.168.0.x and assign dhcp. I have 2 network cards installed just wondering how to configure dnsmasq to do this task above.

Many thanks,
James

---

### Post by Cheesehead on 2012-03-17
Well, if both cards are correctly usable by Network Manager, the easy way is to let NM do the work for you.

Edit the WAN connection in NM, look for the IPv4 settings tab, and look for the "Share this connection" checkbox.

---

### Post by jwsicomputing on 2012-03-18
Thank you so much it worked!!!

James

---

