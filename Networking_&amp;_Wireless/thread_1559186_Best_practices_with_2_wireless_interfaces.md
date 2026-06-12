---
title: "Best practices with 2 wireless interfaces?"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by fabjoa on 2010-08-23
Hey Ubuntu community   

I have two wireless interfaces in my laptop, one is a WiFi card inside the laptop and the other is a USB-antenna (see my iwconfig at end of post). I'd like to know if it's possible to split the connection. For example, I have to launch an operation that is retrieving images from a server, sending them to another one that will gd-convert them from jpg to png then ftp the results to a third server and there are about 12 thousands images, so it takes a lot of bandwidth resources. My question: is that possible to ask one interface to do this operation while i can use the other interface to do other stuff, like browse the web?

TX   



lo no wireless extensions.

eth0 no wireless extensions.

wlan0 RT2860 Wireless ESSID:"vallespir" Nickname:"RT2860STA"
Mode:Managed Frequency=2.412 GHz Access Point: 00:24:D1:13:C4:17 
Bit Rate=54 Mb/s 
RTS thr:off Fragment thr:off
Link Quality=86/100 Signal level:-58 dBm Noise level:-81 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

wlan1 IEEE 802.11bg ESSID:"vallespir" 
Mode:Managed Frequency:2.412 GHz Access Point: 00:24:D1:13:C4:17 
Bit Rate=48 Mb/s Tx-Power=20 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=60/70 Signal level=-50 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by Iowan on 2010-08-23
Although I don't know the specifics, I suspect that careful routing should be able to accomplish that - the interfaces would need to be in separate subnets...

---

