---
title: "Connection speed all over the place, freezing"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by yallaen on 2011-08-13
I have struggled with this issue now since I loaded Ubuntu, and it's really getting me mad. I've got some files I need to d/l, and the d/l keeps aborting >:(

I'm running ASUS laptop N53SN with onboard NIC card. I have a reliable network connection where I'm at. Others are on the same network segment, and can connect just fine. They also run Skype occasionally and have no issues. I on the other hand, am pulling my hair out.

First, with Skype, I keep getting freezes, dropouts, static. My wife will be talking then say "oh, I lost you", then after several seconds, we have to say "are you there"..until the connection reestablishes. Now before you say it's a Skype issue..

So I've been trying to d/l some technical files as well. These files are about 25 meg in size. Everytime I start the d/l, it aborts at various times. My d/l speeds are all over the map, sometimes as high at 70 KBytes (it's not blindingly fast, but it's the best we got here), even up to occasional 80KBytes, but then it will drop to 10 or 11 KBytes, then down to 5 or 6..then back up. THere's no one else on this network segment at 2am. Then, the d/l will abort, and say that the source code could not be read. 

I've also seen my VPN connection fail from time to time, using PureVPN. With no one else having the issues, I'm wondering if my NIC card is going bad, or if there's something wrong with Ubuntu 11.04?

---

### Post by varunendra on 2011-08-14
We'll need the outputs of the following:
```
ifconfig -a
``````
iwconfig
``````
sudo lshw -C network
``````
cat /etc/resolv.conf
```

---

