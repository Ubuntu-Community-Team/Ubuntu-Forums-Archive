---
title: "giving access point name in wvdial.conf"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2011-07-24
I am searching for wvdial.conf
how can I write APN (access point name) my service provider does not have any kind of authentication,(username and password are blank)
they specify only an access point name.

```

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Phone = *99***1#
ISDN = 0
Username = " "
Init1 = ATZ
Password = " "
Modem = /dev/ttyUSB1
Baud = 9600

```
wvdialconf generated above file in which since my username and password are blank so I used ```
" "
``` but Access Point Name how to give it that I am not clear.Without that my USB modem will not work.

---

### Post by jamesbon on 2011-07-25
Ok I have done a lot of Googling and learned the commands with respect to it and /etc/wvdial.conf should have Init3 commands as I added below.
In your case the same may be Init2 etc.So that you might need to manually edit.
My access point name is TATA.DOCOMO.INTERNET so replace this with yours also my ISP does not give a username password 
so I have used " " 

```
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Phone = *99***1#
ISDN = 0
Username = " "
Password = " "
Init1 = ATZ
Init3 = AT+CGDCONT=1,"IP","TATA.DOCOMO.INTERNET"
Modem = /dev/ttyUSB2
;Baud = 9600
Baud = 960000
Auto DNS = 1
Dial Command = ATDT
Carrier Check = yes
Stupid Mode = 1
```
My Baud rate is wrong so you replace with yours.

After this use wvdial and you should be able to connect.

---

