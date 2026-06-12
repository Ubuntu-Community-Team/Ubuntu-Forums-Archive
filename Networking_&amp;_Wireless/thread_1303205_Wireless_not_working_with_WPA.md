---
title: "Wireless not working with WPA"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by squee-g on 2009-10-28
I have a bit of an interesting problem, I'm running 9.04 (x86_64) on my Gateway MX-6440 laptop, and I'm having trouble with the wireless connections.  I can connect to a wireless network that is unencrypted or uses WPA2.  But I cannot connect to a network that uses WPA or WEP encryption (I can see them, just not connect to them).

I know that there are many other similar topics, but none of them seem to help.  If you have any ideas or suggestions, please let me know.  I'm a bit of a n00b to linux, so please list any commands I should run.  Help!  Additional notes below.  Thanks in advance!

[LIST]
[*]Broadcom 4318 card (is listed when doing lshw -C network)
[*]Using ndiswrapper for the driver on the card
[*]Can see WPA/WEP networks, cannot connect to them (fails while validating authentication--Yes, I've checked and double-checked the password).
[*]Works just fine when using wind0wz.  (yuk!)
[*]Tried using NetworkManager and Wicd, both have the same effect (now using network manager).
[/LIST]

---

