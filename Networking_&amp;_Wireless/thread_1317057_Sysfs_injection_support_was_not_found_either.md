---
title: "Sysfs injection support was not found either"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by Hb_Kai on 2009-11-06
Hey, 

I'm trying to use aircrack-ng with Ubuntu 9.10 and my Atheros AR2413 chipset using the ath5k driver and apparently, even according to some people on the #linux-wireless IRC channel, ath5k injection support works out of the box with the kernel I'm using (2.6.31) but when I try the injection test:

```

aireplay-ng -9 -e teddy -a 00:14:6C:7E:40:80  wlan0 
```

which gives me:

```

root@Henry:~# aireplay-ng -9 -e *ESSID* -a *BSSID* wlan0
17:06:42  Waiting for beacon frame (BSSID: *BSSID*) on channel 6
17:06:42  Trying broadcast probe requests...
17:06:44  No Answer...
17:06:44  Found 1 AP 

17:06:44  Trying directed probe requests...
17:06:44  00:22:3F:CD:57:DA - channel: 6 - 'ESSID'
17:06:50   0/30:   0%

```

According to aircrack-ng's wiki found [here]("http://www.aircrack-ng.org/doku.php?id=simple_wep_crack"), injection is not working properly if this returns a zero or zero percent and then says I need to patch my driver which, isn't the case with the newer version.


Am I missing something?

---

