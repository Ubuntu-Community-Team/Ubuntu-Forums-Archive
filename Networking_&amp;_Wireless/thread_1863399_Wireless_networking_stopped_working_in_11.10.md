---
title: "Wireless networking stopped working in 11.10"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by andy.stevens on 2011-10-17
Hi,
 
I've been running 11.04 on an Acer Aspire One (A110 aka ZG5) netbook for some time now, which happily connects to my wireless network.  However, when I boot from the USB stick I created from the recently-released 11.10 ISO, although it starts up okay the wireless networking doesn't appear to be working.  I don't get as far as scanning for the network; whenever I select Enable Wireless from the network manager applet I just get a message in the log
ADDRCONF(NETDEV_UP): wlan0: link is not ready
and it remains disabled.
 
Has anything changed with the driver?  I can see messages that mention ath5k and cfg80211 in dmesg, but they're the same for both versions (I've filtered and diff'ed those lines in each case to check...) so I'm guessing either it's a bug that's been introduced in the driver, or there's some configuration setting somewhere that's different.  Where else should I check?
 
 
Andy

---

