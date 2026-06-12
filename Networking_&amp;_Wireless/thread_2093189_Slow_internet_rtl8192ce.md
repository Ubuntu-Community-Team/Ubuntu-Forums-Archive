---
title: "Slow internet rtl8192ce"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by rodny1 on 2012-12-10
Im running ubuntu 12.10 with wireless card rtl8188ce/rtl8192ce and my internet works at normal speed (800 kB/s) for 1 min, after 1 minute the speed drops to 150 kB/s and i have to reconnect to reset my speed to normal. In windows the wireless works fast all the time.

---

### Post by ahallubuntu on 2012-12-10
This card has known problems with the built-in kernel driver in Ubuntu 12.04 and 12.10 .  You can try building the latest driver from Realtek.

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

You'll have to build this in a terminal, though.

---

### Post by rodny1 on 2012-12-10
> **ahallubuntu said:**
> This card has known problems with the built-in kernel driver in Ubuntu 12.04 and 12.10 .  You can try building the latest driver from Realtek.

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

You'll have to build this in a terminal, though.
I did the following and i still dont works.
1. downloaded the driver.
2. extracted the tar.gz
3. sudo make
4. sudo make install
5. restarted my computer

I think the problem can be that i never activated the new dirver (ie im still using the old one).

The driver i downloaded works for kernel 2.6.24 (and later, up to 3.2.x). Is it a good idea to downgrade my kernel to version 3.2 or will songthing other stop working?

---

