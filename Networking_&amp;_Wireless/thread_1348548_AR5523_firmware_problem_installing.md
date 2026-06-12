---
title: "AR5523 firmware problem installing"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by File_ on 2009-12-07
I am trying to install firmware for my TP-LINK TL-WN620G usb wireless adapter. When I enter command lsusb it gives next output: 
"Bus 001 Device 007: ID 0cf3:0002 Atheros Communications, Inc. AR5523 (no firmware)"

I am following next tutorial: [http://wiki.debian.org/ar5523](http://wiki.debian.org/ar5523) 
I applied patch and I entered MAKE command. And when that finished, I went to next step...
It says: cp ar5523/ar5523.ko /lib/modules/$(uname -r)/updates/drivers/net/wirelesss
I can't find any file with that name (ar5523.ko) in that folder?
I found that file in ar5523.tgz but when I copy it it says:
" FATAL: Error inserting ar5523 (/lib/modules/2.6.29.4/updates/drivers/net/wireless/ar5523.ko): Invalid module format"
 

Can someone help me?

---

### Post by File_ on 2009-12-30
Is there any help?

---

