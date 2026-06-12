---
title: "Wireless Tether not working, and I think the wrong driver is installed."
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by elv5034 on 2012-02-11
Hello all! This is my first post ever, so please bear with me. I'm having trouble with wifi tethering. I have Ubuntu 11.04 installed and am using the Wireless Tether for Root Users app. When I connect, the network manager says it's connected but the wireless icon remains grey, I can't load any web pages and the app on my phone doesn't show a connection. 

I think this is because I may have the wrong wireless driver installed, but I don't know how to change it. With the lsmod command, it's showing rtl8187, lsusb shows RTL8187B Wireless Adapter, lspci and system testing both show RTL8101E/RTL8102E PCI Express Fast Ethernet controller. Originally, the wireless tether didn't connect at all. I then downloaded the rtl8101e Windows driver and installed it with ndiswrapper and now the network manager says it's connected, but I have no internet access. I tried blacklisting rtl8187, but that didn't work and I ended up with no wireless connections at all and had to undo it. I can see all the wireless connections available now, but I still can't do Wireless Tether. 

EasyTether works fine and that's what I usually use, but there are certain web pages that I need to access for school and they go through an infinite redirect loop with EasyTether, but when I try on a Windows machine with WirelessTether, they work fine. I don't know if that last bit helps, but I'm just trying to give as much info as possible. Oh, and when I originally installed Ubuntu 11.04 last year, WirelessTether worked fine but then after I upgraded to 11.10 it stopped working. This wasn't a big issue for me as I could still connect to other networks and I ended up switching to EasyTether instead. But now with this new problem, I've downgraded to 11.04 because I thought that would solve the issue since it was working before, but it didn't.

Any help with this would be greatly appreciated. And sorry if this is too long, but I'm just trying to be detailed. Thanks!

---

