---
title: "toshiba soft modem and wvdial"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by zasf on 2005-12-11
Hi all,

I have a toshiba M40-281 laptop with a internal soft modem. I'm trying to get connected to my ISP, so far the closest try is with vwdial.

```
matteo@zubuntu:~$ sudo wvdialconf wvdial.conf
Scanning your serial ports for a modem.

Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7
Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15
Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23
Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31
Port Scan<*1>: S32  S33  S34  S35  S36  S37  S38  S39
Port Scan<*1>: S40  S41  S42  S43  S44  S45  S46  S47
Port Scan<*1>: S48  S49  S50  S51  S52  S53
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```

wvdial finds my modem on /dev/ttySL0, then i edit /etc/wvdial.conf so that it add some stuff for italian tones, my user name and pw, speaker on, the it finally gets like this

```
matteo@zubuntu:~$ sudo cat /etc/wvdial.conf

[Dialer Defaults]
Modem = /dev/ttySL0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = ATX3
Init4 = ATM2
DialCommand = ATDT
ISDN = 0
Modem Type = Analog Modem
Phone = 7027020000
Username = <user here>
Password = <pw here>
```

then i type sudo wvdial, i dont hear anything, but the modem seems to connect.. and then asks for my user name :confused:

```
matteo@zubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATX3
ATX3
OK
--> Sending: ATM2
ATM2
OK
--> Modem initialized.
--> Sending: ATDT7027020000
--> Waiting for carrier.
ATDT7027020000
CONNECT 46667
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT7027020000
--> Waiting for carrier.
User Access Verification
Username:
Username:
Username: <I type user here and press enter>


Caught signal #2!  Attempting to exit gracefully...

--> Disconnecting at Sun Dec 11 14:09:00 2005
```

please, take a look at the code, what am i doing wrong???
Wvdial is not supposed to ask my username, since i wrote it in the wvdial.conf, anyway i write it and press enter.. but nothing happens, then i finally press Ctrl+C, any ideas?

Thank you

---

### Post by zasf on 2005-12-12
Here is the answer, found with the help of the ubuntu italian community:

```
matteo@zubuntu:~$ sudo cat /etc/wvdial.conf

[Dialer Defaults]
Modem = /dev/ttySL0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = ATX3
Init4 = ATL2
DialCommand = ATX3DT
Carrier Check = no
ISDN = 0
Modem Type = Analog Modem
Phone = 7027020000
Username = <username here>
Password = <pw here>
```

Hope this can help, thank you all anyway

---

