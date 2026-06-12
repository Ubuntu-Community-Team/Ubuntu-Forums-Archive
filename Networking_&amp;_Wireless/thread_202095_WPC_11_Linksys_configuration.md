---
title: "WPC 11 Linksys configuration"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by punkybouy on 2006-06-22
My linksys wpc11 card version 4 lights up but I can't connect.  Ubuntu is 6.06.  I installed KWiFiManager and it sees my network.  I have essid entered and also Wep key.  My question is in the configuration of the card for "access point" I have the mac address of my wireless router.  Is that correct?  I tried using the IP of the router but that didn't work.  The mac address enters without error and Kwifimanager now shows the routers mac as the Access Point but it also says Access Point:unknown.  If KWifimanager sees the network wouldn't that mean that the driver is loaded and working?  I have not gone the ndis wrapper route yet.  Ubuntu sees the card as a Realtek 8180L.
I also tried a hard coded IP address for the card taking DHCP out of the picture but still no luck.
WEP key is entered with dashes after every fourth decimal: ab12-12ed- etc

---

### Post by x64Jimbo on 2006-06-22
Is your network using a "shared" WEP system instead of "open"? 
If so, you have two options - you can either change it to "WEP - Open Authentication" or you can do your wifi configuration manually with iwconfig and include the option "restricted"

---

### Post by punkybouy on 2006-06-23
Its WEP and open.  Thanks for the reply.  Any other ideas?

---

### Post by punkybouy on 2006-06-23
Why does iwconfig tell me the Access Point is Not Associated?

---

### Post by punkybouy on 2006-06-23
Ah ha, I found an entry in /var/log/kernel.log that the driver is experimental.  So How do I unload this driver and prevent it from loading in the future?

---

### Post by iamdigitalman on 2006-06-25
yes, I also have this card, but my network is WPA-PSK TKIP. I also tried WEP and no restrictions to no avail. installed kwifimanager, but still nothing. apparently, my card is working, but it's not boadcasting it's own IP address. thus, it cannot connect to the AP, even though I manually enter the ESSID. is there any way to force the card to boadcast the IP so it can make a connection? the driver is fully loaded, and it appears to make several attempts to connect at startup, but that is unsussesfu.

thanks. -digital ;)

---

