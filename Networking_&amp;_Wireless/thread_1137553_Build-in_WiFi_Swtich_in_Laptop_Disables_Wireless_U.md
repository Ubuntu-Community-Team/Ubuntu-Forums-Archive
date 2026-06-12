---
title: "Build-in WiFi Swtich in Laptop Disables Wireless USB card in network manager"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by marcon00 on 2009-04-25
Hello,

Back in 8.10,when i run my USB Wireless i had my build-in wifi off,through the switch so it wont cause any conflicts while connected to anynetwork.

Meanwhile, in 9.04, if i switch off my build-in card through the side button, i get Disable WIreless in network manager and my additional Wifi USB stops working as well.

I dont want that to happen :\

Thanks in advance.

---

### Post by marcon00 on 2009-04-26
*hickup*

---

### Post by utnubu(k) on 2009-06-08
Got the same problem and wonder that ther're no more replies to this problem. I guess it's a bug and would like to get back the old behaviour. 
At the moment i do a quick workaround by disabling the internal with ```
# sudo ifconfig wlan0 down
``` but it's really annoying to do this from time to time.

Thanks in advance!

---

### Post by utnubu(k) on 2009-07-30
Still not fixed :(
Seems noone else has those problems - how can i get back the old behaviour of 8.10 ?
Do I have to file a bug report?

edit: Seems that bug appeared already in a previous version - maybe the patch got messed up with the update to jaunty?
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/286164](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/286164)

---

