---
title: "Problem with get connection on ZTE AC682"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by jibon_24 on 2011-12-28
Hello everyone,

I am using ubuntu 11.10 from Bangladesh with ZTE AC682 cdma in Citycell Network. For connecting it in my ubuntu I follow this instruction [http://r3m1ck.us/other/tips-tricks/how-to-connecting-smartfren-zte-ac682-in-linux](http://r3m1ck.us/other/tips-tricks/how-to-connecting-smartfren-zte-ac682-in-linux)

But the problem is when i give this code :```
[COLOR=#00ff00]**sudo wvdialconf**[/COLOR]
```
it give this output:```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- L&#65533;[0c][10]T&#65533;[0c][10]\&#65533;[0c][10]d&#65533;[0c][10]
ttyUSB1<*1>: failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- L&#65533;[0c][10]T&#65533;[0c][10]\&#65533;[0c][10]d&#65533;[0c][10]
ttyUSB1<*1>: failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: China TeleCom
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB2.
Modem configuration written to /etc/wvdial.conf.
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```
But problem is this line ```
Found a modem on /dev/ttyUSB2
``` But in instruction it was ```
Found a modem on /dev/ttyUSB0.
```
When i edit [COLOR=#00FF00][B]wvdial.conf file:
[/B][/COLOR]```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB2
Username = waps
Password = waps
Baud = 9600
```
& try to connect the modem using ```
[COLOR=#00ff00]**sudo wvdial**[/COLOR]
``` it do not work. I am surprised to see that ubuntu detect my modem as GSM instated of CDMA. Please help me. Thanks in advance.

---

### Post by jibon_24 on 2011-12-28
There is no one who can help me please !!!!!!!

---

### Post by pdc on 2011-12-28
you actually don't need to use wvdial;

if you use network manager, the settings for your provider are already in there;

left or right click on network manager
edit connections
mobile broadband
add
country (bangladesh)
provider (citycell)

add your username and password

and it should work .......

---

### Post by jibon_24 on 2011-12-28
Thanks @[pdc]("http://ubuntuforums.org/member.php?u=18016") for your reply:P. But i have already tried to follow this instruction before but nothing was happened:(. For this reason now i am trying to use wvdial. Any other ideas:confused:. Thanks again.

---

### Post by jibon_24 on 2011-12-30
Hello no one for help pzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz

---

### Post by nugroho.redbuff on 2012-01-02
there so many tutorial about connecting AC682 CDMA Modem with Ubuntu box. Yet, not all of them work. My modem has the same trouble too,  it can not easily get barrier signal.
But I have solution for you. May be you need to use Mobile router just like TP-LINK MR 4220. It helpfully so much.:popcorn:

---

### Post by jibon_24 on 2012-02-01
Still have the problem. No one can help me plz..

---

### Post by alexfish on 2012-02-01
Hi

your dev/ttyUSB* does not indicate been configured as true cdma , normally shows as ttyACM*
need some info

can post results of
```
usb-devices 
```locate the lines which indicate the device and only those lines

can also test MM can download a script called mm-test.py
this should reveal more about the device

```
wget http://cgit.freedesktop.org/ModemManager/ModemManager/plain/test/mm-test.py
```or paste  in the browser

then use copy and paste or save as. (name the script "mm-test.py") in home directory
to test a device open up a terminal
```
python ./mm-test.py --no-scan
```alexfish

---

### Post by adnan360 on 2012-08-17
Actually it seems that it is a bug. See: [https://bugs.launchpad.net/ubuntu/+source/eject/+bug/980472](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/980472)

In 11.04 and older versions a simple sudo eject /dev/sr1 would work. It would turn 19d2:ffde to 19d2:ffdd. But from 11.10 and later (at least upto 12.04), the command gives error message
> not an sg device, or old sg driver

I have found from [this link]("http://linuxwireless.org/en/users/Drivers/zd1211rw/Driverless") that the problem is due to Linux version 2.6.19-rc1 or later. I think it is due to the new way that Linux handles the "ttyUSB"s. Before, I have seen a few (2-5) ttyUSB* entries. But from 11.10 there are many (2-30) "tty*" entries (not "ttyUSB*" entries).

---

