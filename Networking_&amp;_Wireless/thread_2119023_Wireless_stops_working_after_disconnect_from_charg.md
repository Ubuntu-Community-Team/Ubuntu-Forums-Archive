---
title: "Wireless stops working after disconnect from charger"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by Compgeke on 2013-02-22
I have a Dell Latitude E6400 running Xubuntu 12.10. Whenever I disconnect from the power cord the wireless stops working, trying to access a webpage just says "Sending Request" from within Chromium and pings just time out, however the second I plug the charger back in everything works fine again.

I have tried running "sudo /sbin/iwconfig eth1 power off" with no change. The wireless card is a Broadcom 4322 based Dell card, and iwconfig reports (on AC or battery):

compgeke@TouchNDie-Mobile:~$ iwconfig eth1
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:206  Noise level:165
          Rx invalid nwid:0  invalid crypt:33  invalid misc:0

The only affected network interface seems to be the wireless card, the 3G WWAN card works on battery and the wired ethernet works on battery.

---

