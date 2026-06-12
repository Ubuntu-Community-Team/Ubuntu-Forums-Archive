---
title: "D-Link Wireless WNA-1330 PCMCIA Card Failure"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by volobiz on 2010-10-01
I had Ubuntu 8.04 and the D-Link Wireless WNA-1330 PCMCIA card worked just fine. I upgraded to 10.04 and it fails. I can see the network of wireless routers in my neighborhood, but when I try to connect on WEP 40/128bit with my hex key of my router, it tries to connect but can't get a DHCP address. I cannot ping the router in that state, of course. I have two other 10.04 laptops (with built-in wireless) and they connect just fine, as does a Windows Vista laptop.

I also tried the pci=noapi item in /boot/grub/menu.lst, but that failed to show any results either.

The card lights up like it should, and acts just like it did with 8.04 on the lights, but it doesn't connect. I end up seeing the "Enter your WEP password" dialog again and again unless I hit Cancel.

What steps do you recommend I take to remedy this?

---

### Post by volobiz on 2010-10-01
I set my wireless card to static IP and was able to get the wireless router connected. I found I could ping the router, but did have some packet loss and could not ping Google's DNS 8.8.8.8. So, I then changed the config so that I used Google's DNS instead of the DSL router's DNS hookup. At that point, I could ping multiple sites on the web as well as the DSL router and Google's DNS -- but I couldn't browse to any websites, and couldn't browse to the DSL router's website. Strange, huh? As well, the packet loss continued in this new config. I mean, pings go through, but there was some packet loss.

And again, in Ubuntu 8.04, this problem did not occur. It's only in 10.04 that this occurs for me.

---

