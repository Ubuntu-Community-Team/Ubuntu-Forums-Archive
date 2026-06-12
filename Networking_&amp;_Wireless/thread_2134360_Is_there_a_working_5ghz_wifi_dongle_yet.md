---
title: "Is there a working 5ghz wifi dongle yet?"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by Taxcheat on 2013-04-11
Question: Is there a dual-band usb wifi adapter that works with Linux?  I searched every 802.11ac adapter, and none appear to work with linux (might as well jump to the latest). Searches find N adapters that "work", but when I look closer, they're only working with 802.11g.

That's useless to me. I live in ultra-congested WiFi space -- about 30 visible access points are sucking up all the 2.4ghz space. Some idiot must be using the world's largest Pringles can, because I recently have been kicked from my own network and can't connect unless the laptop is in the same room as the router (Netgear N600, which is dual band N). I suppose that means it's time to escape to 5ghz, which means I need USB wifi dongles for my laptops.

Help! Am I doomed to windows?

---

### Post by ahallubuntu on 2013-04-11
~

---

### Post by QIII on 2013-04-11
A bit expensive, but...

[https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-req-antennas](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-usb-req-antennas)

---

### Post by Taxcheat on 2013-04-11
Thanks for the responses. First: already did a network analysis using inSSIDer. There is no unused 2.4 space. I played with different channels, no luck. I'm up against routers set to "auto" that hop around. 

The thinkpenguin dongle looks ok, but $65 plus ludicrous shipping cost from the UK kill the deal. :( Did a few searches off the Atheros AR9170 chip it uses, and stumbled on Tenda W522U:
[http://www.tenda.cn/tendacn/Product/show.aspx?productid=384](http://www.tenda.cn/tendacn/Product/show.aspx?productid=384)

Looks like cheap Chinese junk, but at least they have a Linux driver. Might try it for $26. Their .11ac adapter doesn't show Linux availability.

---

### Post by kurt18947 on 2013-04-11
The adapter can make a huge difference in signal strength.  A Dlink DWA-131 v.1 sporting a Realtek 8192SU chipset has about twice the signal strength (measured using wavemon) compared to a generic rt5370 in exactly the same spot/same orientation/same USB port.  I still don't get the rated 150 mb./sec. though, usually 65 mb./sec.  I'm curious about how accurate those measurements are but don't have a LAN setup with throughput measuring.

---

### Post by QIII on 2013-04-11
Avoid Tenda.  I bought several models to experiment with them and none worked.

---

### Post by Taxcheat on 2013-04-13
Oops, too late. Already received the Tenda (love Amazon prime). Works perfectly on Windows. There are only 3 other 5ghz networks near me, with no overlap. I tried installing the driver in Ubuntu, but couldn't figure it out. I'll update to the latest distro (actually, will change to Mint since I despise Unity) and try again. I consider $26 cheap to get my laptop usable again. I use two laptops, so I might try something else for the other one. Maybe look into a PCI card swap, as mentioned above.

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by Taxcheat on 2013-04-14
Just installed Mint 14 on one of my laptops, and the Tenda 522U worked right from the live USB stick. Awesome. I assume it would work from the latest Ubuntu as well. Confirmed it's working in 5ghz. The chipset is: Ralink Technology, Corp. RT3572 Wireless Adapter

I do have Ubuntu 12.04 running on my desktop with Gnome, but it took hours to undo all the idiotic design decisions the Ubuntu devs made when I 'upgraded.' If I wanted my PC to be treated like a tablet, I'd get Windows 8. I need to figure out how to customize Mint, but so far the default is pretty nice.

I'll definitely look into the minipci upgrade for my Samsung laptop. The dongle is annoying.

---

