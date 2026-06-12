---
title: "TP-Link TL-WN821N Wireless N USB Adapter"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by polar11 on 2010-10-15
TP-Link TL-WN821N - (I think Atheros chipset)

Can anyone confirm if this will this work with xbuntu 10.04 or xbuntu 10.10?

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)
this suggests it will not work and dont waste your money

[http://linux-wless.passys.nl/query_part.php?brandname=TP-Link](http://linux-wless.passys.nl/query_part.php?brandname=TP-Link)
and this confirms it works without issue!!


If not can anyone recomend a cheap either g or n usb wifi adapter? If possible I just want one that I can just plug in and it works!

thanks

---

### Post by polar11 on 2010-10-16
anyone?

---

### Post by petephili on 2010-11-06
I have one of those running on Ubt 10.04 and it can start up without install additional driver, but the thing is it will get disconnected in a random amount of time, just like what others said in forum. Others mentioned there is a patch to fix the problem.

---

### Post by polar11 on 2010-11-15
thanks for the post petephili, i got one and it worked out of the box with:
xubuntu 10.10
xubuntu 10.04
kubuntu 10.10

all worked fine N wifi dongle for £8 (from the online retailer sharing its name with a rather large south American river)

no issues with it randomly disconnecting? yet??

---

### Post by GuiGuy on 2010-11-26
> **polar11 said:**
> 
no issues with it randomly disconnecting? yet??

I have one of these and just put it on my "Things bought and almost instantly regretted doing so"

It's junk. I have tried it on several networks and range of OSs. Connection speed is erratic, fluctuating between 200kbps and 11mbps, which makes complete nonsense of 300mbps claim.

A waste of money.

---

### Post by Fairfax on 2010-11-27
I'm having many problems with the TL-WN821N on Ubuntu 10.04 and 10.10, including erratic connections and great variations in connection speed, as noted above by others. I'm about to return it to Amazon, because it's simply too unreliable for extended use. It is detected out of the box by both 10.04 and 10.10, and initially all seems well, but then the problems begin . . .

I'm using it on a 802.11g network, and there's the added problem that it connects to the router with two MAC addresses! It's possible that this is not unusual, and I'm only noticing it because of problems, but it seemed strange to me! Specifically, I configured my router to assign a fixed IP address to the MAC address detected by the router's DHCP server, and then found that the TL-WN821N was also connecting with a second MAC address, and therefore also being assigned an IP address by the DHCP server. Consequently the system is now reachable by two IP addresses, but unreliably so. Any enlightenment would be useful; apologies if I'm being WiFi naive.

---

### Post by Fairfax on 2010-12-01
I've solved the problem of two MAC addresses -- my stupid error. That said, the fundamental problems of the TL-WN821N are still present: it cannot  provide a reliable connection.

---

### Post by min_max9000 on 2011-01-14
> **polar11 said:**
> TP-Link TL-WN821N - (I think Atheros chipset)

Can anyone confirm if this will this work with xbuntu 10.04 or xbuntu 10.10?

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)
this suggests it will not work and dont waste your money

[http://linux-wless.passys.nl/query_part.php?brandname=TP-Link](http://linux-wless.passys.nl/query_part.php?brandname=TP-Link)
and this confirms it works without issue!!


If not can anyone recomend a cheap either g or n usb wifi adapter? If possible I just want one that I can just plug in and it works!

thanksI got this device to work on 10.0.4 just yesterday but I had to use compat-wireless and do away with ndiswrapper. Still haven't got it running on 802.11 n though, just b/g so far. One hurdle at a time I suppose.

---

### Post by min_max9000 on 2011-01-14
> **polar11 said:**
> TP-Link TL-WN821N - (I think Atheros chipset)

Can anyone confirm if this will this work with xbuntu 10.04 or xbuntu 10.10?

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)
this suggests it will not work and dont waste your money

[http://linux-wless.passys.nl/query_part.php?brandname=TP-Link](http://linux-wless.passys.nl/query_part.php?brandname=TP-Link)
and this confirms it works without issue!!


If not can anyone recomend a cheap either g or n usb wifi adapter? If possible I just want one that I can just plug in and it works!

thanksI got this device to work on 10.0.4 just yesterday but I had to use compat-wireless and do away with ndiswrapper. Still haven't got it running on 802.11 n though, just b/g so far. One hurdle at a time I suppose.

---

### Post by min_max9000 on 2011-01-14
> **polar11 said:**
> TP-Link TL-WN821N - (I think Atheros chipset)

Can anyone confirm if this will this work with xbuntu 10.04 or xbuntu 10.10?

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB)
this suggests it will not work and dont waste your money

[http://linux-wless.passys.nl/query_part.php?brandname=TP-Link](http://linux-wless.passys.nl/query_part.php?brandname=TP-Link)
and this confirms it works without issue!!


If not can anyone recomend a cheap either g or n usb wifi adapter? If possible I just want one that I can just plug in and it works!

thanksI got this device to work on 10.0.4 just yesterday but I had to use compat-wireless and do away with ndiswrapper. Still haven't got it running on 802.11 n though, just b/g so far. One hurdle at a time I suppose.

---

