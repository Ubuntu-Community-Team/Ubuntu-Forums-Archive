---
title: "AR9380 Variant - Very slow connection speeds"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by iniquiTrance on 2012-05-01
I'm running Ubuntu 12.04 LTS. My new build uses a TP-LINK TL-WDN4800 PCI-E wireless adapter. Apparently, the chipset is an Atheros AR9380. I'm getting extremely slow connection speeds, whereas everything is super fast in Windows. 

Any help would be much appreciated.

---

### Post by Spectre5 on 2012-05-08
Turns out that you answered this yourself, it seems?  I found your review on Neweegg ([http://www.newegg.com/Product/Product.aspx?Item=N82E16833704133&Tpk=N82E16833704133](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704133&Tpk=N82E16833704133)), which I'll repeat here for any other poor sap that stumbles into this thread.

> In terminal, type:
sudo -s gksu gedit /etc/modprobe.d/ath9k.conf
Then in the text file that opens, add the following line:
options ath9k nohwcrypt=1
Save the file, close it, and reboot. Connection speeds should be good now.

I'm going to buy this card tonight, so I hope that this works for me too...

---

### Post by bash321 on 2012-06-18
did this fix work for your wireless card???
I'm just wondering as I am looking to buy one of these cards.

bash321

---

### Post by Spectre5 on 2012-06-18
Actually I don't think it was even needed.  It worked great right away for me.  I tried apply these commands and the performance remained the same (which is very good).  Although I went ahead and left that line in the file, so maybe if I kept using it I would have eventually had problems without it.

---

### Post by wildmanne39 on 2012-06-18
Hi, most of the time those commands are need for that driver and it usually fixes the issue.
Thanks

---

