---
title: "Aireplay-ng Aspire one,Madwifi"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by robban35 on 2010-10-19
HI!
 
First time here and almost first time with ubuntu...
 
I have an Acer Aspire One -532h and i just installed ubuntu 10.
I am trying to crack my own Wep network at home with Aircrack-ng.
So after i installed Ubuntu and installed everything in "updatemanager", i installed Aircrack,Macchanger.
And as i look in "iwconfig" and ifconfig i see the Atheros driver Ath9k and Wlan0.
Now my 1st question.
Do i have to install madwifi or such for the aircrack to inject?
 
2:nd
I have tried to install madwifi also but when aireplay-ng want to inject ,the whole computer freezes.
How do i fix this?....have looked aound google and found that many have the same trouble...

---

### Post by LeMeun on 2010-11-13
I think you need to install the driver for your specific chipset from the aircrack-ng website. Can you run airmon-ng and have your card in monitor mode?

Try the injection test also, here the link:
[[COLOR="Blue"]_http://www.aircrack-ng.org/doku.php?id=injection_test_[/COLOR]]("http://www.aircrack-ng.org/doku.php?id=injection_test")

---

