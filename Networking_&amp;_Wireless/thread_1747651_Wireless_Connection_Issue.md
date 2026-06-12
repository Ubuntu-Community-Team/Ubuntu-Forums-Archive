---
title: "Wireless Connection Issue"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by Jake.Debord on 2011-05-02
Having problems connecting to my wireless router... I can connect with security turned off, but when I enable WPA I run into issues.

I have looked around quite a bit and keep seeing a "Network Manager" gui tool that was supposed to be included with my Ubuntu 10.10 but I don't see it. I have a network connections menu that I can play around with and try to set up manually but can't get it to work. I have everything entered correctly (to my knowledge) and still no luck.

I installed "Wifi Radar" and can view my network with it, but when I try to connect with it, it gets stuck on "Acquiring IP Address DHCP"

Any help is appreciated.
TIA

*Additional Information"
Netgear WG311 Wireless NIC Card using WINXP driver.
ndiswrapper to install it
using wifi radar to manage connection
network broadcasts SSID and has WPA security enabled.

---

### Post by josephmills on 2011-05-02
hi there could you open you terminal and tye in 
```

iwlist auth 

```
and paste here thanks

---

### Post by Jake.Debord on 2011-05-04
Thank you for trying to help, but I figured it out on my own. I was missing wlan0 in my configs. Just a noob mistake I overlooked in the tut I was reading...

---

