---
title: "3g modem not working with wvdial"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by susiriss on 2010-06-07
Hello Guys,
           I'm posting this after lot of trials to get my Huawei E220 modem to work with my Ubuntu 10.04 - 64-bit laptop. Modem works fine with Network Manager applet, but when I try it with wvdial, i get the following output but the modem never connects to the carrier.

```
$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","mobitel3g"
AT+CGDCONT=1,"IP","mobitel3g"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
^BOOT:82228292,0,0,0,6

```

This ^BOOT message continues to repeat but nothing happens after that.

my wvdial.conf looks like this.

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","mobitel3g"
Stupid Mode = 1
Dial Attempts = 3
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB1
Username = " "
Password = " "
Baud = 9600
```

What puzzles me is why I'm getting this ^BOOT message. The APN name and the dial number works fine with NM applet.

Is this a 64-bit related issue? I got this working for Lucid 32-bit version with Wvdial with another PC.

any idea ??

thank you !

---

### Post by aryangor on 2010-06-07
I use Karmic 32 bit - here is my wvdial.conf:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99*1#
Password = none
Username = simobil

hope it helped!.. :)

---

### Post by susiriss on 2010-06-07
@aryangor, Only difference is the line " New PPPD = yes". But even with that, the problem is still there.

---

### Post by susiriss on 2010-06-08
Fixed by myself !!!

In case anyone found the same problem, what I did was built it by myself from source. The problem was with the version in Ubuntu repos. Don't know the exact reason, but it works.

---

