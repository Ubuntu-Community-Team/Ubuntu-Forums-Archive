---
title: "Wireshark with network lan tap"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by keyboardmonkey on 2012-07-07
I am running Ubuntu 12.04, and I am trying to get wireshark with my network lan tap. This is the guide I used [http://www.enigmacurry.com/category/diy/](http://www.enigmacurry.com/category/diy/)

I checked the wiring on my lan tap and the connections are good, and I am able to still get internet when I use the host A and host B. I stripped little bit of the cable insulation on tap A and tap B. So, it does have better connection. When I go into wireshark I notice eth0 and eth1 do not display their mac address, and I had them in promiscuous mode. So, I typed ifconfig into terminal and they're still up, but I did notice eth0 had something I never seen under the hardware info it shows "interrupts: 51" I never seen that before so I am not sure what that is?

Do I need to change the settings for eth0 and eth1 for them to work properly? BTW eth1 is using usb ethernet adapter (Belkin F4U047)

---

