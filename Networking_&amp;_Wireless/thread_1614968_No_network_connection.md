---
title: "No network connection"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by Amockineuropa on 2010-11-06
I have a little Acer One PC that I use for travel. For the past 2 years I have had Windows and Ubuntu on it as a dual boot. Everything was fine in paradise.

So I decide since I NEVER used Windows that I would just load the new Ubuntu 10.04 on the entire HD. If was not hardwired to my router at the time. Everything seemed to load just fine. 

Then I discovered that I had NO wired or wireless connection/option. 

I tried to reload the OS but this time with it hard wired to the router but it made no difference for either. 

The "enable networking" is enabled as is the enable wireless tab but still nothing. 

Any ides?

---

### Post by uncaspi on 2010-11-06
See if the cards are listed using sudo /sbin/ifconfig

Then we take it from there:)

---

### Post by bigfootnmd on 2010-11-06
Acer Laptops and netbooks often use ATHEROS WIFI chips.
Ubuntu 10.10 has native ATHEROS drivers.
Download Ubuntu 10.10 and make a start up disk (using the tool in system) and put it on a USB.
Boot off of the USB and odds are that Ubuntu 10.10 will find your WIFI chip and tell you that there are connections available.

Good luck

Also use the sEARCH function on this page.

---

### Post by Amockineuropa on 2010-11-06
I did try the search option but found no comments that directly addressed MY particular problem. I loaded 10.10 and during the loading process it said something about needing to load wireless info. I did not have time to copy the provided address down. I guess Ubuntu recognized that I need to install Atheros 3 rd party files. Not sure what files or how to do that.

---

### Post by Amockineuropa on 2010-11-07
Not sure WHY but when I reload 10.10 my wireless option started to work without a problem! Go figure.

---

### Post by bigfootnmd on 2010-11-07
The reason why your wifi is working is because Ubuntu 10.10 has native atheros drivers.
My experience at home as shown that things work best with my router set to channel 11.  Also, if you use WPA you need to try both AES and TKIP encryption to see which works best for you.

---

