---
title: "Change channel with network manager"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by lunxer on 2009-05-13
Hello

I have a ubuntu box that i would like to share its Internet connection (via eth0) to a wireless device with a wifi pci card, a 
RaLink RT2561/RT61 rev B 802.11g.

I googled some and found out that i needed to:
sudo apt-get install dnsmasq-base
 
I did this and clicked the applet for network manager (the one in the notification area) 
and created a new network, without any security for now.

The bar for this newly created network was empty (theres a neighboring network with about ½ strength)

When i connect with my wireless device, i get the lowest possible possible signal strength and test show that i get 
about 0.5-0.8 Mbit download and 5.0-8.0 Mbit Upload.

I tried to change the channel on wlan0 on the sharing box to 10, but when i press the applet to connect to 
my network (to be able to share my internet) it resets to channel 1.

How do i change the channel from resetting to 1? Or can i try anything else to get better signal?

---

