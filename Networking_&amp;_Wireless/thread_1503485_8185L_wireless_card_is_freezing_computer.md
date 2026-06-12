---
title: "8185L wireless card is freezing computer"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by Thq on 2010-06-06
New linux user here. The first two times I entered the wireless key on the prompt that appeared shortly after login, the computer froze completely.  ctr-alt-f1 ctr-alt-backspace did nothing.  The third time, I closed the first prompt and after 10 minutes I tried connecting again.  It didn't freeze, at first. The internet worked.  It took about 10 minutes later for it to freeze.  Now, whenever I  boot up, it freezes a few seconds after login.  I can boot recovery mode, but I don't know what to do from there.  Heres some info I got from the recovery mode:


Computer Brand: Sony PCV RX850

Ubuntu 10.4 32 bit  2.6.32-21-generic i686

Realtec 8185L chipset

iwconfig
	IEEE 802.11bg  EssID: off/any
	Mode: Managed Access Point: Not Associated tx-power= 20 dBn
	Retry long limit: 7 RTS thr: off Fragment thr: off
	Power Management: off

lsnw –C network
	Configuration: broadcast=yes driver=rt18180 latency=32 max latency=64
	ningnt=32 multicast=yes wireless=IEEE802.11bg

iwlist scan
	no scan results

sudo /etc/init.d/networking restart
	reconfiguring networking interfaces… [ok]

Please help.

---

### Post by Thq on 2010-06-07
bump

---

### Post by Thq on 2010-06-08
If I don't get a reply, I might try to reinstall Ubuntu.  That'll stop it from freezing, but not fix the wireless.

---

### Post by Thq on 2010-06-12
I reinstalled and changed drivers but it still freezes on startup.  I tried disabling the wireless in recovery mode with this ```
sudo iwconfig eth1 txpower off
```
but I don't think it worked, though the wireless icon is gone from the top bar, It STILL FREEZES.

I really don't want to reinstall again.  Please help.

---

