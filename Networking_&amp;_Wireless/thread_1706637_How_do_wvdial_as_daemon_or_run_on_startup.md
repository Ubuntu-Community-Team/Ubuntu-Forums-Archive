---
title: "How do wvdial as daemon or run on startup"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by Farrukhjon on 2011-03-14
Hi friends!, Help me. I have installed USB modem (ZTE) on my Ubuntu Server 10.04 and its works fine. But only manual start ./wvdial, how do wvdial as daemon or run on startup.

Config: /etc/wvdial.config

[Dialer Defaults]
Modem Type = Analog Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","internet"
Phone = *99***1#
Username = xxx
Password = xxx

Thanks in advance!

---

