---
title: "Huawei E272 Module vodafone USB internet problem"
date: 2012-10-04
forum: Networking &amp; Wireless
---

### Post by learnbash on 2012-10-04
Hello folks,

Below is my lsusb detail. I am now in capetown southafrica.

```


Bus 006 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270 HSDPA/HSUPA Modem


```Below is my wvdial.conf detail

```


[Dialer vodafone]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","internet";


```but when i am trying to connect with vodafone it give error. Please see below

```


wvdial vodafone
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
ERROR
--> Bad init string.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
ERROR
--> Bad init string.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
ERROR
--> Bad init string.


```Please help me out to resolve this issue. I have usb_modeswitch already install.

---

### Post by learnbash on 2012-10-04
I have a pin code on my sim, so what option i should add in my setting?

---

### Post by alexfish on 2012-10-04
```
Init1 = AT+CPIN= <your pin>
```

Regards

alexfish

---

### Post by learnbash on 2012-10-04
> **alexfish said:**
> ```
Init1 = AT+CPIN= <your pin>
```Regards

alexfish

I use this setting still having error.

```


[Dialer vodafone]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = AT+CPIN = 0000
Init2 = ATZ
ISDN = 0
Modem Type = Analog Modem
Init5 = AT+CGDCONT=1,"IP","internet";


```

Below is error

```


--> Sending: ATZ
OK
--> Sending: AT+CGDCONT=1,"IP","internet";
AT+CGDCONT=1,"IP","internet";
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
NO CARRIER


```

---

### Post by learnbash on 2012-10-04
I use another setting as well, but it is also not working.

```



[Dialer Defaults]
Modem = /dev/ttyUSB0
Phone = *99***1#
;Phone = *99#
Stupid Mode = 1
Username = vodafone
Password = vodafone
Dial Command =

[Dialer pin]

Init1 = AT+CPIN= 0000


[Dialer option]

Modem = /dev/ttyUSB0
Baud = 460800
Init2 =
Init3 =
ISDN = 0
Modem Type = Analog Modem


[Dialer internet]

Init5 = AT+CGDCONT=1,"IP","internet";


```

---

### Post by alexfish on 2012-10-05
need to see what this modem is about

post results of these commands from the terminal

```
usb-devices
```Locate the lines which indicate the device and only those lines
```

ls -al /dev/serial/by-id
```

alexfish

---

