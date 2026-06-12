---
title: "Connecting Ubuntu Laptop brings Entire Network Down"
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by amaac on 2012-03-02
[B]So I recently installed Ubuntu on an old laptop of mine. Every time that i connect the ubuntu laptop to my network it brings the entire network down. Wireless or wired. 
My router is a buffalo xtreme n with DD_WRT on it.  The ubuntu laptop actually connects but after going online for a few minutes the entire network goes down and the router hands out invalid 169 addresses. I have to unplug my router and restart it to bring things back.

I am not sure what the problem could be. I feel like it is collisions bringing the network down but the laptop is configured for DHCP. 
Machine Brand and Model (PC/Laptop)[/B]:  

Acer Travelmate 5730 Laptop
    [B]
Wireless Brand, Model and Wireless Chipset:[/B]
```

Ethernet controller: broadcom corporation NetXtreme BCM5764 Gigabit Ethernet PCIe (rev 10)
kernel driver in use: tg3

network controller: intel corporation wifi link 5100
kernel driver in use: iwlagn

``` 
**Ubuntu Version: **
Ubuntu 11.10

[B]Kernel/architecture (including 32 vs. 64 bit): 
3.0.0-16generic i686
 [/B]

---

### Post by amaac on 2012-03-02
Thankyou everyone for all of your help. I kept thinking that my problem was with the Ubuntu laptop when i never thought to search for the DD_WRT firmware issues with ubuntu. I removed DNSmasq and i have been connected for a while now. I am marking this as solved and i apologize for not searching correctly.   My answer was found not too far away. [http://ubuntuforums.org/showthread.php?t=1932546](http://ubuntuforums.org/showthread.php?t=1932546)

---

