---
title: "wlan0 will not autostart upon login"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by tonyps on 2010-06-14
Afternoon,

Hardware:
Toshiba Satellite A505D-S6958
Wireless: Realtek 8192e
Ubuntu 10.04, x86

lspci
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

Not sure whatever other info I can provide to get assistance.
I was using ndsiwrapper with XP driver, but always prefer to Linux drivers if they are available. So, I emailed Realtek web support and they sent me latest drivers for Ubuntu 10.04.
I followed their instructions and it works great! With, the exception of, I have to run
./wlan0up each time after I login to start the wireless.
I seem to remember having to modify a file some place, which was very easy to do, but for the life of me I cannot seem to remember what it was or what to put into it?????
Assistance greatly appreciated!!
Oh, and also, how do you tell if your wireless card is making use of the "n" speed, if the network your are on has it available?
Tony ...

---

### Post by bazzal1941 on 2010-06-14
Have a look at this description of how to fix a WPA problem in 10.04 with RT chips. One of the final steps tells you how to fix your problem.

Sorry I'm too lazy to look it up for you.

---

### Post by bazzal1941 on 2010-06-15
Sorry didn't give the link.

[http://ubuntuforums.org/showthread.php?t=1476007]("http://ubuntuforums.org/showthread.php?t=1476007")

---

