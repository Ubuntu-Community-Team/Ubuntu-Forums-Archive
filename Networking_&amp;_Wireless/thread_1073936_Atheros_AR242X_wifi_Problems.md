---
title: "Atheros AR242X wifi Problems"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by diamondjim08 on 2009-02-18
Ok, with Ubuntu 8.10, I,ve got a new Acer Aspire 5515 with this seemingly very difficult wifi card, AR242X. I've tried everything in these posts with no results for wifi. WICD is loaded and works with hard wire but no wifi. Drivers checked show that the card is using the driver 5xxxx for AR242X. The origional driver was deactivated. My other notebook shows a wifi station present but this one can't see it.
iwconfig shows:
mashid@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan1 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.
What should I do next?
Thanks, <> Jim
diamondjim08 is online now   	Reply With Quote

---

### Post by mixtri on 2009-02-18
Hey Dude.
Follow this tutorial.
[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

Scroll down till you get to the entry by someone called "Reasoner" and follow his tutorial.

It's a case of getting the right drivers which I believe in your case to be ath_pci.

Once you have completed the tutorial run lspci -v in a terminal to see if the correct driver is loaded.

if it is then you should be able to get wifi access - if not, I would strongly advise you to install "WICD" Link- [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

I had exactly the same problem as you and was able to solve it it using both tutorials above.

However, WICD will only detect available networks when you have the right driver installed for your network wireless adapter, so if you are unable to detect any wireless networks after installing and running wicd; means you have the wrong drivers installed which might need to be blacklisted.

Good luck.:p

---

### Post by Crafty Kisses on 2009-02-18
Some people have had success by installing the following package:
```
sudo apt-get install linux-backports-modules-intrepid
```

---

### Post by binbash on 2009-02-19
Read this guide : 

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

