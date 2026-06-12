---
title: "Atmel card gives shoddy performance -- how can I use it properly?"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by Twinxor on 2006-07-12
The cheap wireless card I got for my laptop has been giving me a ton of trouble:

1) Dropping connections all the time, while I'm using it!

I'll just be browsing the forums or whatever, and lose my connection. Sometimes going into GNOME's Network Settings and just clicking Properties (without changing anything!) will fix it. Sometimes I have to do ifdown and ifup to make it work, even though I haven't changed any settings that should break it. Sometimes it just won't work at all, and only time can fix it. Whee!

2) Won't connect to other networks!

Coffeehouses around here offer unencrypted wireless APs that I can scan for just fine. But I almost never can connect to them. Using iwconfig, I've made sure the card  is set to the right essid, channel, encryption mode... but it still won't really work. The one time I got it working, it just mysteriously started talking to the network after I'd given up on it half an hour before. Can I figure out what's wrong?

3) What the heck is 802.11-DS?

Seriously, what is this? These are the settings that make it work, sort of, at home:

```
root@plateau:~# iwconfig eth1
eth1      IEEE 802.11-DS  ESSID:"default"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:06:9E:79
          Bit Rate:11 Mb/s
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:5106-6555-81   Security mode:restricted
          Power Management:off
          Link Quality=58/100  Signal level=21/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:60
```

Help? I really want this to work. The card is a pretty generic one using an Atmel at76c50x chipset. Ubuntu automatically configured its [native driver](http://atmelwlandriver.sourceforge.net/news.html), though the driver seems to hardly be complete.

---

### Post by Twinxor on 2006-07-17
Any ideas would be appreciated...

---

