---
title: "Wireless only starts when plugged in."
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by gitboxrhys on 2012-09-26
So I just upgraded to Ubuntu 12.04 64 bit. 
Whenever I boot up my computer (Dell Inspiron N7010) The wireless wont recognize any Networks. The only way to connect is to shut down the computer plug in a network cable and then reboot. Not sure what there is That I can do to fix this.

---

### Post by gordintoronto on 2012-09-26
Is the wireless on? From what I have read, Fn + F2 might help.

When you are connected, have you run Additional Drivers? It might find a driver for the wireless.

If you open Terminal and enter the command: lspci
about a dozen lines should be displayed. One of them should contain "802" and that describes your wireless adapter. It might give you information you can use in Google.

By the way, there is a Dell forum here. You might have gotten a faster or better answer there.

---

### Post by gitboxrhys on 2012-09-26
The Wireless is on. I would rarely have this problem in the past, but when I turned the Wifi switch off and on it would work. but it doesn't seem to work like that this time.

Broadcom Corporation BCM4313 802.11b/g/n  is what I have as a wireless card

---

