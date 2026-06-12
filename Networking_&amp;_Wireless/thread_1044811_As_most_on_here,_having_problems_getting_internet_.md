---
title: "As most on here, having problems getting internet connection"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Jeff769 on 2009-01-19
I have the  WiBee XS-2204S USB 2.0 802.11b/g Wireless LAN Adapter looking to put that on my old HP omnibook xe3. I tried getting the internet with my belkin card, but was unsucessful. So I bought this usb listed above to try and fix problem. I have heard some say on here that usb's that connect without hassle. Want someones expertise before I even make a move. Please let me know what I have to do step by step if possible. I really want Ubuntu 8.10 to work with internet.....oh by the way it worked briefly with belkin, even thought belkin never lit up showing any sort of connection. When I updated Ubuntu, that is when it stopped completely...

---

### Post by MaindotC on 2009-02-07
I have the WiBee which use the RTL8187 chipset.  You can download the latest driver from the company's website.  It contains a bunch of files - one of them is the README file that shows how to build the driver and execute the makefile for installation.  I know you want a nice simple .deb file but I followed the directions that came with the driver and it works perfectly.  Just follow that README file and let me know how it goes.

---

### Post by MaindotC on 2009-02-08
Sory about above post - actually the rtl8187 driver or whatever its called is included in the latest Hardy kernel.  Plugin in the WiBee and in a terminal type:
```

lsmod | grep rtl

```
You should see something like this:
```

amd64@amd64-desktop:/var/log$ lsmod | grep rtl
ieee80211_rtl          86664  1 r8187
ieee80211_crypt_ccmp_rtl     9088  1 ieee80211_rtl
ieee80211_crypt_tkip_rtl    13056  1 ieee80211_rtl
ieee80211_crypt_wep_rtl     7680  1 ieee80211_rtl
ieee80211_crypt_rtl     7944  4 ieee80211_rtl,ieee80211_crypt_ccmp_rtl,ieee80211_crypt_tkip_rtl,ieee80211_crypt_wep_rtl
amd64@amd64-desktop:/var/log$

```

There's more to it than that though.  I'm going to re-open a post on this so if you're watching, check my posts.

---

