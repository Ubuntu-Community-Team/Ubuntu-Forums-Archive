---
title: "can connect w cmd line but not gui - good clue"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by maaark38 on 2010-12-07
I have been working through many of the suggestions on this forum the past few days trying to get my Broadcom 4312 to connect to my WiFi.  The problem is that my adapter never seems to receive a DHCPOFFER.

I have progressed to the point where I can reliably connect using the following two commands:

iwconfig eth7 essid SSIDNAME key MYWEPKEY
dhclient eth7

But using the GUI (wicd) I still cannot connect, /var/log/daemon.log never shows a DHCPOFFER coming back.

Any speculation on why I can connect with the cmd line but not the GUI ?

Thanks.

---

