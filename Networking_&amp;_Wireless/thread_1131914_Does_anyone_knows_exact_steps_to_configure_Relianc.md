---
title: "Does anyone knows exact steps to configure Reliance EC-121 USB  Modem  on Ubuntu 8.04"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by ddeepak on 2009-04-21
Hi,

Does anyone has exact steps to configure Relience EC-121 USB Modem on ubuntu 8.04? 
I have edited /etc/wvdail.conf as:
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 M1 L1 X3 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Abort On No Dialtone = False
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB0
Username = <put reliance no>
Password = <put reliance no>

but when i run "sudo wvdial"  it gives following error:
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

Plz guide me to setup this modem on ubuntu 8.04.

Thanks,
Deepak

---

