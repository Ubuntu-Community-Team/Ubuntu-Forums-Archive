---
title: "RTL8191SEvB ad hoc issues in *buntu 11.10"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by shaan7 on 2011-12-25
Hi, I have a ThinkPad edge 15 with the wireless card -
```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
```Usual connection to access points work fine, but ad hoc doesnt work (creating/joining). By doesn't work, I mean it connects to the network, but I can't ping anyone.

The peculiar thing is that it works in Ubuntu 11.04 but not on Ubuntu 11.10 (tested using LiveUSB). I tried searching the net and this forum but nothing related to adhoc.

I found the closest match on the realtek site to be [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2262).

As the model number isn't exactly same as mine, I'm not sure, should I try to build the driver in the above link?

---

### Post by BC59 on 2011-12-25
The driver RTL8191SE-VA2 should be equal to yours. Try to install it from the site. 

Are you sure there is no option in the application Additional drivers for your card?

---

### Post by shaan7 on 2011-12-25
> **BC59 said:**
> The driver RTL8191SE-VA2 should be equal to yours. Try to install it from the site. 


Cool, I tried it and it works! Thanks :D

> **BC59 said:**
>  
Are you sure there is no option in the application Additional drivers for your card?

Nope, I had checked it but it says No proprietary drivers are in use and the list is blank. Anyway the driver above solved it.

---

