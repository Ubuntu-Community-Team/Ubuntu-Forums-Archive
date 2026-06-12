---
title: "trouble connecting to open wireless network"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by trubblemaker on 2006-01-06
I've come to the end of my rope.

My Broadcom wireless card (with ndiswrapper 1.7 & linux-headers) was working with Ubuntu Breezy, on an unecrypted network I rebooted and it stopped working.

I'm unable to resolve names.

I made sure that the wireless card has the correct ESSID (UBC), correct frequency, I can see multiple "channels" and even tried manually setting the access point (corresponding to my essid) to one I found from running 
```
iwlist wlan0 scan
```
when I run 
```
dhclient wlan0
```

i see it search and I get a message back the finishes something like

```
SIOCADDRT: Unable to connect to network.
```

I would paste the message itself but I have to boot into windows to use the wireless card, also proof that the card itself works. and that the network is still working.

As an aside, it's normal for me to have to turn off eth0 when I log on, and manually select the unencrpyted essid to access the internet.  I look at the packets in and out and I noticed that although I can receive packets (1000) I send out maybe only a few ( 18 ) in a 15 min. period.

Thanks so much for reading.

---

