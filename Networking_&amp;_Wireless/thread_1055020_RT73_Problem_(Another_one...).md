---
title: "RT73 Problem (Another one...)"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by Papo1988 on 2009-01-30
Hi guys, i have tried searching so im sorry if this has already been answered. I have just recently aquired a dell mini 9 (inspiron 910) and i had a spare rt73 card kicking about from a broken laptop. I wish to use this for penetration testing using the Aircrack tools. Here is the problem:

The default rt73 driver supplied in ibex finds and connects to wireless networks perfectly but no injection. I have followed various guides on installing the k2wrlz drivers and they compile and install but it iwlist or airodump find no wireless networks.... Any ideas?

All help greatly appreciated.

Papo1988

---

### Post by xpod on 2009-01-30
I have a WUSB54G wireless USB dongle(uses rt73usb) that seems to encounter similar issues when trying to use Aircrack suite from the repos(although that was back in 8.04) but using the [Backtrack Live CD](http://www.remote-exploit.org/backtrack.html) seemed to all work fine out the box so to speak.As does my 3CRUSB(zd1211) Dongle
I`m no expert on the subject but i certainly managed to access my own WEP encrypted networks within minutes.Hence the reason i would never dream of using WEP and do what i can to make sure people use WPA and as complicated a password as possible.

---

### Post by Papo1988 on 2009-01-30
Thanks for your reply. Its not using the aircrack suite thats the problem. The new driver wont even function as a normal wireless card... No networks are detected.

---

