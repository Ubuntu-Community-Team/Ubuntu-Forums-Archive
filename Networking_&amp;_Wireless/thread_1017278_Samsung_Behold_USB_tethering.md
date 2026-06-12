---
title: "Samsung Behold USB tethering"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by malachakla on 2008-12-20
Hello y'all,
I decided to write in as I'm at my wit's end after 6+ hours struggling.
I'm trying to use my T-Mobile (US) Samsung Behold T919 as a modem through USB.
It is in modem mode, and is recognised as a ttyl device by wvdial.
I set it up using wvdialconf and whenever I dial I get an "Invalid dial command" error.
Am I missing a specific init string? Perhaps my phone isn't meant to be a modem?
[B]
Below is what flashed by when running wvdialconf:[/B]

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- ERROR
ttyACM0<*1>: Modem Identifier: ATI -- Manufacturer: SAMSUNG ELECTRONICS CORPORATION
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2"


[B]Here are the settings in wvdial.conf:
[/B]
[Dialer Defaults]
Modem = /dev/ttyACM0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Modem Type = USB Modem
Phone = *99#
ISDN = 0
Username = t-mobile
Password = t-mobile
Baud = 460800

---

