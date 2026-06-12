---
title: "Linksys WUSB54GC"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by Nostigex on 2010-07-11
When I first used this USB adapter (Linksys WUSB54GC, version unknown) with 10.04 a couple of weeks ago, it worked fine. Could surf the web and everything. Then, after 3 or 4 days, suddenly I could no longer access the internet. I can still connect to the wireless network, but Firefox gets stuck on "Looking up ____________..."

---

### Post by Steve603z on 2010-07-11
are you able to access the internet when plugged directly into the LAN? are you able to access the internet using other Access Points? If you use a live CD, can you access the internet?

sounds to me like a DNS issue

I would try opening a command prompt and trying to ping google.com see if it can resolve google.com to an IP address

then try pointing your web browser to [http://208.69.38.170/](http://208.69.38.170/) which is OpenDNS's system status page, if this works, you know it's a DNS issue. 

if OpenDNS's system status page opens, I would right click on the signal strength icon > edit connections > wireless > [your SSID] > edit > IPv4 Settings:

then if "Method" is set to "Automatic (DHCP)" try changing it to "Automatic (DHCP) addresses only" and under DNS server I would type ```
208.67.222.222, 208.67.220.220
``` 
if it's something other than "Automatic (DHCP)" I would try changing it back to "Automatic (DHCP)"

---

### Post by Nostigex on 2010-08-19
After a lot of playing around with the position of the USB stick (using extension cables) I've found that the problem has to do with the reception percentage. If the network is more than 50%, then I can access the internet just fine. If it's below 50%, even at 48% or so, then nothing. I'm confused by this because if the computer can connect to the network at all, it seems like it should be able to access web content...

---

### Post by Nostigex on 2010-08-24
Anyone have an idea what could be going on here?

---

