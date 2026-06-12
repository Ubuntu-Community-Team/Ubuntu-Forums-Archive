---
title: "slow wifi"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by StanleyBE on 2013-04-15
When I plugged in my new USB Wifi dongle (Micronext 300M with RTL8191SU chipset), Ubuntu 12.04 recognized it immediately with the rtl8712u driver.
However, speeds were horribly slow to the point of being unusable. 

Things I tried, in this order:
- [Tried]("http://www.alexj.me/12/fixing-slow-wiereless-speeds-in-ubuntu/") wicd instead of network-manager.
- Upgrade to newest driver from [Realtek website]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=229&DownTypeID=3&GetDown=false&Downloads=true#2292"). But there is no support for kernels later than 3.0.2. The drivers fail to make/build.
- Blacklisted rtl8712u and installed Windows drivers using ndiswrapper. The XP drivers worked, but I had the same problem: it was really slow.
- Upgraded to latest Ubuntu 12.10. 

The problem persists. For what it's worth: I'm using a very nearby Airport Extreme with WPA2 security...

---

### Post by StanleyBE on 2013-04-15
For future reference and to whom it may concern: I solved the issue after a lot of trial and error. 
It appears the 'auto' mode for the wifi channels on the airport extreme is far from the best setting. 
After experimenting with manual settings on channels 1 through 13, channel 2 came out as the clear winner. 
Speed went up from 0,1 mbps to almost 5 mbps! Hopefully it stays that way...

---

