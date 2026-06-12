---
title: "Problem with connecting using Huawei K3520 modem on a Vodacom Network"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by Darth_Zere on 2010-04-10
Hi

I'm having a problem connecting with my modem. I have been to this post:

[http://ubuntuforums.org/archive/index.php/t-1244135.html](http://ubuntuforums.org/archive/index.php/t-1244135.html)

and did not have any success. 

It picks up "Vodacom Default1" on the netwrok manager, but when I click on it it says:

"GSM network: Disconnected - you are now offline"

I tried wvdial heres my wvdial.con under /etc:
[Dialer Defaults]
Phone = *99***1#
Username = username
Password = password
Stupid Mode = 1
Dial Command = ATDT

[Dialer hsdpa]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem


and when I type "wvdial hsdpa" in the terminal i get:

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
ERROR
--> Invalid dial command.
--> Disconnecting at Sat Apr 10 13:48:16 2010


tried many other methods to no avail. Please help.

PS: It works on windows but just started using ubuntu and don't want to keep on going back to XP to use the net.

---

### Post by pdc on 2010-04-10
what does 

> lsusb

give you in a terminal; copy and paste the results here

what does 

> dmesg | grep tty 

in a terminal give you?

If there are no ttyUSB0 etc results, your system is not recognising your device as a modem 

you can see in the post you quoted that the poster got amidst the dmesg printout ...

> [I]option 4-2:1.0: GSM modem (1-port) converter detected
[ 90.893328] usb 4-2: GSM modem (1-port) converter now attached to[/I] **ttyUSB0**

finally what does

> uname -r give as 9.10 ubuntu seems to need newer kernel versions to work with mobile broadband ..

---

### Post by Darth_Zere on 2010-04-10
Hi pdc

Thank you for your help.

Her is what "lsusb" gives:

Bus 001 Device 002: ID 5986:0102 Acer, Inc Crystal Eye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Her is what "dmesg | grep tty" gives:

[    0.001367] console [tty0] enabled
[ 3650.647610] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 3650.652529] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 3650.656445] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB2
[ 3650.656582] usb 5-1: GSM modem (1-port) converter now attached to ttyUSB3


Her is what "uname -r " gives:

2.6.31-20-generic

Thanks again

---

### Post by pdc on 2010-04-10
so all the positives;

a basic huawei modem: good

> 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

and your system recognises the device as a modem

> GSM modem (1-port) converter now attached to ttyUSB0

and you have the latest kernel version installed

> 2.6.31-20-generic

 so either one uses network manager; or some other means:

so for network manager you did this:

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

.. half-way down page; how to create mobile broadband ..

.. sometimes settings are wrong;

google on your country + provider (which is?)

and look for apn settings; check those are right;

wvdial: they need more ruminating on: what the above first ..

.. by the way ...

.... how did you set up your /etc/wvdial.conf file?

---

### Post by Darth_Zere on 2010-04-10
I tried using Network Manager by searching for my networks APN settings and putting it in NM. It did not work. My network is Vodacom (South Africa). The search said that my APN is

internet

I set up my /etc/wvdial.conf file by typing: 

> sudo wvdialconf /etc/wvdial.conf

and got:

> Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

it then did not work and then I copied and pasted one from the link in my first post. Not sure what to do now. Do you have any ideas??

---

### Post by pdc on 2010-04-10
yes for vodacom I get

>  Vodacom

WAP/GPRS:
APN: internet
Username: leave blank
Password: leave blank
Email smtp: smtp.vodacom.co.za

I don't have immediate answers for getting this working on Ubuntu 9.10;

I would google on your device; 

depends what you want to do: if you primarily want to get online; if you have the ability to download a distro such as crunchbang; as an iso; and put it on a USB stick and try; or an older version of ubuntu; eg 9.04 seemed more reliable;

---

### Post by pdc on 2010-04-10
can you try another wvdial script

> [Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN*= 0
Baud = 460800
Dial Attempts = 1
Username = 
Password = 


Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","internet"
Phone = *99#
Stupid Mode = 1

I have edited it to reflect your apn settings;

if you save it as /etc/wvdial.conf and if you save your existing one as another name and so still exists .....

to open the file

> sudo gedit /etc/wvdial.conf would be the command; copy and paste the above

try by issuing 

> sudo wvdial from the terminal, and if any joy, control-c cuts the connection

---

### Post by Darth_Zere on 2010-04-11
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by Darth_Zere on 2010-04-11
It worked. I also needed to put something in the username and password. The problem seemed to be the phone I was using *99***1#.  Thank you so much pdc much appreciated.

---

### Post by pdc on 2010-04-11
glad to hear it worked; 

in the script I suggested to you, it defined the apn settings of your provider; and had differing Hayes commands;

enjoy!

(and thanks for being very organised and entering solved: that's great!)

---

