---
title: "DHCP Problem"
date: 2006-01-21
forum: Networking &amp; Wireless
---

### Post by pharmdad2007 on 2006-01-21
Hi there,
I have a wireless network set up at home, and I have successfully used ndiswrapper to configure my wireless card and connect to the network.  However, I can only connect if I enter a static IP on my laptop, even though my wireless gateway is set up for DHCP.  When I try to connect using DHCP, it will connect to the network, but never get an IP address.  So I am perfectly happy with using a static IP, but the problem is this:  I want to connect to the wireless network at school as well, but they don't allow you to use a static IP, so in order to connect there I need to get this DHCP problem solved.  I think there must be some communication problem between my laptop and the DHCP server, but I don't know what it is.  Any help would be greatly appreciated!
Thanks in advance,
Jesse

---

### Post by kasemodz on 2006-01-21
what chipset are you using? I had a realtek rtl8185 chipset and I tried everything but I had the same exact problem as yours. Somehow when I did dmesg it always said no ip-v6 routers found. I somehow have a strong feeling that may be causing all the problem. I disabled it but I still couldn't get it to work. You can try though. Remember to post back if it works.

---

