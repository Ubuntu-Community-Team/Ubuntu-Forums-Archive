---
title: "Wrong wireless driver installed (RTL8187 instead of RTL8180E)"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by elv5034 on 2012-02-11
I'm having trouble with wifi tethering and I think this is because I may have the wrong wireless driver installed, but I don't know how to change it. With the lsmod command, it's showing rtl8187, lsusb shows RTL8187B Wireless Adapter, lspci and system testing both show RTL8101E/RTL8102E PCI Express Fast Ethernet controller. Originally, the wireless tether didn't connect at all. I then downloaded the rtl8101e Windows driver and installed it with ndiswrapper and now the network manager says it's connected, but I have no internet access. I tried blacklisting rtl8187, but that didn't work and I ended up with no wireless connections at all and had to undo it. I can see all the wireless connections available now, but I still can't do Wireless Tether. 

Any help with this would be greatly appreciated. And sorry if this is too long, but I'm just trying to be detailed. Thanks!

---

