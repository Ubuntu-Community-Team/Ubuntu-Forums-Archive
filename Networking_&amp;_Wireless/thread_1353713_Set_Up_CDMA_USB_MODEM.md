---
title: "Set Up CDMA USB MODEM"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by nikhilbhardwaj on 2009-12-13
i've followed the guide which came with my nokia modem
setting up wvdial

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CRM=1
Stupid Mode = 1
Modem Type = USB Modem
 Phone = *****
ISDN = 0
 Password =******
New PPPD = yes
 Username = ******
Modem = /dev/ttyACM0
Baud = 460800
```

now to connect i must start wvdial each time from the terminal
and it does work no problems with that

and the network applet in the panel shows no network connection


I want to be able to just plug in the modem and connecting to the internet automatically
or by right clicking the network applet and connecting from there
is it possible

---

