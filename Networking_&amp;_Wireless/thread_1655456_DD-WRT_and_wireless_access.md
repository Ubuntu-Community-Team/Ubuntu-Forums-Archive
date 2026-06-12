---
title: "DD-WRT and wireless access"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by raven on 2010-12-29
This is for educational reasons

feedback:
I read that WEP is hacked in 10 min or less and MAC address filtering is no security at all.
so for educational reasons I wanted to see if I can hack my own wireless AP
I have the SSID
I have the WEP key

I have a DD-WRTV24 on linksys WRT-54GS used as a wireless client
I have a 2wire modem/wireless router 2701HG-B from my ISP

for the first step and not to complicate the issue, I have the SSID and the WEP phrase
so I don't need to hack them with kismet or any of this sort.
that being said the only hurtle that I cannot understand is with all informations that I have (WEP key and MAC to spoof) I still cannot connect and have access to internet...

so the issue is bypassing the MAC filter on the 2wire modem/wireless router
anyone have any ideas ??

---

### Post by raven on 2010-12-30
it seem that the DD-WRT cloning is not working as I thought it should/understood
even when I access my AP 2wire and put a MAC address in the allow list to see if I can connect by cloning this same MAC it does not connect and connot obtain an IP.

conclusion
the cloning feature of DD-WRTV24 is not able to connect to an AP when trying to clone a permitted MAC address in the AP allowed list.

---

