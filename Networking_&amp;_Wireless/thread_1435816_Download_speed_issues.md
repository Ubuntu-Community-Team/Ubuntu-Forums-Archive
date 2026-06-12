---
title: "Download speed issues"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by aussiedaddy on 2010-03-21
I am having problems with download speeds in Ubuntu 9.10.  Downloads start at a healthy speed and then drop to almost zero.  This affects apt-get install, Pan newsreader etc.  With apt-get install if I terminate the download (with [Ctl][C] ) and restart it I get another burst at high speed then again back to almost nothing.  It makes updates a nightmare.  With Pan newsreader I get high speed for most files but when downloading some of the larger files the speed drops right back to almost nothing after a while.  I am on wired ethernet (no wireless).  Typically I will get about 1.1MB before the speed drops - although I think it may be a function of time rather than data.  I am talking to my ISP via a Netgear FWAG114 router and a NetComm NB5 ADSL modem operating in bridge mode.  Although a number of users appear to have experienced very similar symptoms here I haven't found an answer that works.

Thanks for any light you can shed on this problem

REgards
aus

---

### Post by johnson.d on 2010-03-22
You can use the following command to change the MTU setting of the Network Interface to 1400 and try again.

$ sudo ifconfig ethX mtu 1400

---

### Post by aussiedaddy on 2010-04-09
Thanks johnson.d 

Your suggestion seems to solve the problem and will save me heaps of time and frustration.  I am very grateful.

I'll now adjust /etc/network/interfaces accordingly.

Out of interest, how did you know what to adjust?

Once again thank you
aussiedaddy

---

