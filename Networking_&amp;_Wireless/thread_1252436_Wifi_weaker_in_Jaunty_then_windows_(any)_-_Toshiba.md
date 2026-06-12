---
title: "Wifi weaker in Jaunty then windows (any) - Toshiba Satellite A215 S7437"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by Parastatic on 2009-08-28
Hello I have Toshiba Satellite A215 S7437, when i am running windows my wifi works perfectly. Can go everywhere in my home and not have to worry about it. Now the problem is, when I am running Ubuntu Jaunty x64 my wifi does work, but! it will detect the access points but will says the connection is weak and list it at 1mb/s. e.g. everything times out unless I get really close to the access point. I waited until now to switch to Linux because I wanted my laptop to be supported and technically it is, but the wifi does not work nearly as it should. Any help would be greatly appreciated. Thanks in advance.


Got it working with some help last night, thank you.

Used ```
sudo iwconfig wlan0 retry 999999
```    
Works for the time being, enough to get me to switch over completely.

---

