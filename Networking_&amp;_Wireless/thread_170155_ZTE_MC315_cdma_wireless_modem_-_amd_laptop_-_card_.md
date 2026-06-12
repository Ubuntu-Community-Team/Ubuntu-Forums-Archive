---
title: "ZTE MC315 cdma wireless modem - amd laptop - card problem"
date: 2006-05-04
forum: Networking &amp; Wireless
---

### Post by paulipe on 2006-05-04
Ubuntu is able to recognize the card (cardinfo) on /dev/ttyS3 but if i use pppconfig, wvdial, minicom or modemu I am not able to connect to my isp.
wvdialconf tries and fails on all the baud rates
if i use pon (from pppconfig) it doesnt connect
wvdial (after manually setting /etc/wvdial.conf) gives the output
"sending atz
sending atq0
resending atz
modem not responding"

i was able to somehow do enough with modemu to run the AT command and get an OK reply, but not on minicom, primarily because I was having a tough time figuring out their interfaces.
I am not on my laptop now so I don't have the exact failures. If anyone has any ideas please respond. I might be able to post the exact failures later
its quite urgent
thanks
paul

---

