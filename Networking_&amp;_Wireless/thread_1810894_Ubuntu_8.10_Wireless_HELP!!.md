---
title: "Ubuntu 8.10 Wireless HELP!!"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by jjmono987 on 2011-07-23
I've just installed Ubuntu 8.10. I'm connected right now with a wired connection.

When I type in iwconfig into the terminal I get:

> lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thr: off Fragment thr=2352 B
Power Management: off
Link Quality: 0 Signal level: 0 Noise level: 0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions

How do I got about connecting to my home wireless network. I have a broadcom wireless card in my laptop. I think ubuntu recognizes my wireless card, but I don't know how to connect...

---

### Post by nm_geo on 2011-07-23
> **jjmono987 said:**
> I've just installed Ubuntu 8.10. I'm connected right now with a wired connection.

When I type in iwconfig into the terminal I get:



How do I got about connecting to my home wireless network. I have a broadcom wireless card in my laptop. I think ubuntu recognizes my wireless card, but I don't know how to connect...

You know 8.10 is no longer supported right?  I would recommend 10.04 LTS ..

---

### Post by jjmono987 on 2011-07-23
so if i upgrade to 10.04 LTS it should help me with connecting to my wireless on the laptop i am using with the broadcom wireless card

---

### Post by nm_geo on 2011-07-23
> **jjmono987 said:**
> so if i upgrade to 10.04 LTS it should help me with connecting to my wireless on the laptop i am using with the broadcom wireless card

Sorry let's do it here

l```
lspci -nn | grep 0280
```It will not hurt a bit if youy can get 8.10 working might help when you upgrade.

10.04 LTS will be supported until April 2013..

---

### Post by wildmanne39 on 2011-07-23
Hi, you will still have to install your wireless driver, but with that old of ubuntu you can not get any software updates including security updates.

It might be hard to get the driver installed because of the fact the none of the packages for that version is in the repositories anymore.

---

