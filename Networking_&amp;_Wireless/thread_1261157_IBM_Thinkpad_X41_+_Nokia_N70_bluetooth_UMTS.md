---
title: "IBM Thinkpad X41 + Nokia N70 bluetooth UMTS"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by hawake on 2009-09-08
Hi All,
i have an IBM Thinkpad X41 with Ubuntu 9.04 just installed. Ubuntu has recognized all my hardware configuration but now i would like to connect through UMTS to Internet using my Nokia N70 Music Edition smartphone.

I followed this tutorial: [http://blog.linux-fueled.com/2007/10/11/ubuntu-connessione-gprsumts-tim-su-nokia-n70-tramite-bluetooth-con-gnomeppp/](http://blog.linux-fueled.com/2007/10/11/ubuntu-connessione-gprsumts-tim-su-nokia-n70-tramite-bluetooth-con-gnomeppp/) but when i try to connect, it find the device and it stops at "sending password" phase. After reboot now i get another error during the "Waiting for prompt" phase BEFORE the "sending password" one.

This is the log of GNOME-PPP:
```
ATZ
OK
--> Sending: AT+cgdcont=1,"IP","ibox.tim.it",,0,0
AT+cgdcont=1,"IP","ibox.tim.it",,0,0
OK
--> Modem initialized.
--> Sending: ATM1L1DT*99***1#
--> Waiting for carrier.
ATM1L1DT*99***1#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> PPP negotiation detected.
--> Unable to run /usr/sbin/pppd.
```How can solve this problem?
Thank you in advance,

Bye
hawake

---

