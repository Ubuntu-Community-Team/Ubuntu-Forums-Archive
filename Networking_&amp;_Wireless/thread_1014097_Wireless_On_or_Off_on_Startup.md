---
title: "Wireless On or Off on Startup"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by P235 on 2008-12-17
Hello, I need a little help with my wireless connection.  When I input the lspci command I receive the following about my wireless card:

04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)


This is not the first time I have set up a computer with Linux, so I installed ndiswrapper, ndisgtk, and downloaded the driver for my card from this forum.  My wireless connection worked and there was relatively little difficulty installing the multimedia packages, updates, etc.  But, when I restarted my computer, the wireless connection was down – as if it did not work at all.  I input the “iwlist wlan0 scan” command, nothing.  I typed in the “iwconfig wlan0” command and saw that the wireless was not connected to any network, so I tried re-inputting the connection settings for my essid and what not.  I also tried reinstalling the driver, "/etc/init.d/networking restart", and "ifup/down wlan0" with no result.  I was a little irked, but later on I shutdown the computer and started it up again only to find that my wireless was working.  Now whenever I start up Ubuntu and the wireless does not start up right away, I shut down and start up my computer until it does.  

Also, whenever I restart the computer into Ubuntu, I notice that my peripherals – like my mouse – do not always start up even though it is connected to the usb port.  I have to unplug and plug-in my mouse at the login screen to get it going again.  My headphones experience a similar problem upon start up sometimes.

I have read others suggesting to toggle the wireless switch or button, but when I switched my wireless off – my laptop has a wireless on/off switch on the side – nothing happens.  I have yet to try using the Fn key to toggle my wireless though.  Right now my connection works, but it would be great if my laptop's wireless connection can be consistently ready to go upon start up.

I am using a Toshiba Satellite L300D - 01Q model with Ubuntu 8.0.4.1.

---

