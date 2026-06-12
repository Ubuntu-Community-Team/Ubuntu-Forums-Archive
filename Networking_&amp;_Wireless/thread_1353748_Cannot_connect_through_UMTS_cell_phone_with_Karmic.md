---
title: "Cannot connect through UMTS cell phone with Karmic"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by fraCPH on 2009-12-13
After upgrading to Karmic my Ubuntu refuses to connect.
I use an UMTS Samsung phone.
This is the configuration that used to work on Intrepid:
wvdial.conf
```
[Dialer Defaults]
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","datacard.tre.it",,0,0
Phone = *99#
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
; Password = <Your Password>
; Username = <Your Login Name>

``` 
and this is the output of "sudo wvdial"
```
fra@fra-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+CGDCONT=1,"IP","datacard.tre.it",,0,0
AT+CGDCONT=1,"IP","datacard.tre.it",,0,0
OK
--> Modem initialized.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
```
just in case you ask, nothing changes if I add "stupid Mode = yes"
Can anybody help me ?
Thank you in advance

---

### Post by GeorgeVita on 2009-12-13
Hi **fraCPH**, edit your configuration file: ```
gksudo gedit /etc/wvdial.conf
``` and try the following parameters: ```
[Dialer Defaults]
Modem = /dev/ttyACM0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = AT+CGDCONT=1,"IP","datacard.tre.it",,0,0
Phone = *99***1#
Stupid Mode = 1
``` Notes: 3G/GPRS Phone number added, dummy user/pass used, stupid mode = 1 added

Post any progress to follow up.

Regards,
George

---

### Post by fraCPH on 2009-12-13
Worked smoothly with your conf.
Thank you very much. :)

---

