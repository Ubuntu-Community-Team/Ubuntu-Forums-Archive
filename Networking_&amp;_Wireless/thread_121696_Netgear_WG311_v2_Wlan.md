---
title: "Netgear WG311 v2 Wlan"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by kafitz22 on 2006-01-25
I have been having problems with my wireless card.

First off, I know my card is not easily configurable due to Netgear not releasing its source publicly.

I posted this in the "Absolute Beginners forum", and was advised to post here. This is mmy post from yesterday:

"I apologize in advance if this is a stupid question, but then again, that's why I'm posting in this section.

I have a Netgear WG311 v2 Texas Instuments ACX111 wireless card. It works just fine, but when I don't use the internet for a little while, the connection drops and I can seem to reconnect without rebooting my computer. Is there anything I can do from terminal or any program I can get from Synaptic so I can reconnect?"

If anyone has any ideas of how to refresh my wireless connection, it would be greatly appreciated.

Thanks,
Kyle

---

### Post by drummer on 2006-01-25
deconfigure and then reconfigure the interface with this:```
sudo ifdown wlan0
sudo ifup wlan0
```
Although I have the same card and it works fine out of the box and I rarely have problems. It has only dropped a few times and I think this normally works.

---

### Post by kafitz22 on 2006-01-25
That's what I was told before. The problem is, when i do that, I seem to get a whole slew of errors and it doesn't seem to reconnect.

---

### Post by kafitz22 on 2006-01-25
Hmm...after killing my internet connection several times, it seems that it is some sort of glitch in Gaim.

---

