---
title: "Hawking HWDN3 Realtek RTL8192CU chipset issue PLEASE HELP!"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by googeek on 2013-05-16
I have tried multiple ways to get this thing going and I am pulling my hair out here.
Tried NDISWRAPPER.
I have tried installing the realtek drivers and blacklisting the old ones.
So far all I can get is that Network Manager does pick it up, but no networks display and I know it's in range.

I need someone to help me step by step as I'm totally new to building, etc.

I see this as solved elsewhere, so I must be doing something wrong :(

PLEASE PLEASE, any help will be greatly appreciated.

---

### Post by MIJ-VI on 2013-10-12
> **googeek said:**
> I have tried multiple ways to get this thing going and I am pulling my hair out here.
Tried NDISWRAPPER.
I have tried installing the realtek drivers and blacklisting the old ones.
So far all I can get is that Network Manager does pick it up, but no networks display and I know it's in range.

I need someone to help me step by step as I'm totally new to building, etc.

I see this as solved elsewhere, so I must be doing something wrong :(

PLEASE PLEASE, any help will be greatly appreciated.

The Realtek RTL8192CU driver works under Ubuntu 13.10-beta2 
 
The rtl8192cu-based StarTech USB150WN1X1 (which hasn't worked for me since Ubuntu 12.04.1 / Linux 3.2.x) has been working fine under ubuntu-13.10-beta2-desktop-amd64 in conjunction with a Belkin F5D6230-3 (802.11b) WiFi router: 
 
USB Wireless Network Adapter - USB to Wireless N Adapter | 802.11N | StarTech.com 
[http://www.startech.com/Networking-I...1R~USB150WN1X1](http://www.startech.com/Networking-I...1R~USB150WN1X1) 
 
Belkin F5D6230-3, specs at DuckDuckGo 
[https://duckduckgo.com/?q=Belkin+F5D6230-3%2C+specs](https://duckduckgo.com/?q=Belkin+F5D6230-3%2C+specs)

```
*-network 
       description: Wireless interface 
       physical id: 1 
       bus info: usb@1:5 
       logical name: wlan0 
       serial: 00:9e:95:9c:54:b8 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.11.0-9-generic firmware=N/A ip=192.168.2.31 link=yes multicast=yes wireless=IEEE 802.11bgn
```

---

