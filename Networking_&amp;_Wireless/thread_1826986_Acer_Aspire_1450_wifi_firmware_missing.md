---
title: "Acer Aspire 1450 wifi firmware missing"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by mrjelle88 on 2011-08-17
Hello everybody,

My laptop has a strange problem. The wifi adapter doesn't work. The system tray icon says there is a wifi adapter present, but next to it: device not ready (firmware missing). Does anybody know what this exactly means and/or how to solve it?

(screenshot in attachment)

---

### Post by chili555 on 2011-08-17
We can solve it with a bit more information. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by mrjelle88 on 2011-08-18
There's a problem with my very old laptop, my friend put in other memory and now I keep getting kernel panic, so I will have to wait for my friend to put back the old memory(RAM) before I can run that command. I'll post it here as fast as I can.

---

### Post by mrjelle88 on 2011-08-18
jelle@jelle-Aspire-1450:~$ lspci -nn | grep 0280
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
jelle@jelle-Aspire-1450:~$

---

### Post by TBABill on 2011-08-18
If you have Internet access via wired connection, are you able to go to Additional Drivers and enable the driver? If you are on 10.04, it was called Hardware Drivers instead.

---

### Post by mrjelle88 on 2011-08-18
I tried it, but there' s only a driver for the modem which is already running.
I added a screenshot.
I also have a problem with bleutooth, I don' t think it has to do with each other but maybe it does.

---

### Post by chili555 on 2011-08-18
Can you temporarily get a wired ethernet connection? If so, please open Synaptic Package Manager and search for b43. Install b43-fwcutter and firmware-b43-installer. After installation, detach the ethernet cable, reboot and enjoy your wireless.

---

### Post by mrjelle88 on 2011-08-18
Thanks a lot, it works great!

Send from my wifi enabled acer aspire 1450 :D:D:D

---

### Post by mgrah on 2012-01-02
This solution also worked for Asus Aspire 3003 LMI.

---

