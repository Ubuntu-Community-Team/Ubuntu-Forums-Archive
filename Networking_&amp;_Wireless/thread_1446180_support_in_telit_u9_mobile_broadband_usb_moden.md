---
title: "support in telit u9 mobile broadband usb moden"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by amitloc on 2010-04-03
I'd tested this modem both on 9.10 and on 10.04 beta1 and the network manager didn't recognized it at all, the power to the modem (from the usb hum) disconnected often and even while using wine I just couldn't got it to work or even couldn't make ubuntu to recognize the modem

again i used a telit u9 which works fine on any windows 9
i couldn't find any evidence that someone managed get it work - but i couldn't fine someone who tried either. i believe that it would be wonderful to ubuntu if the issue of supporting mobile internet modems would be fixed in 10.04. i'm looking forward to the day i could use my u9 to browse the web using ubuntu.

by the way i'm using a Dell Inspiron 1525 laptop and my cellular vendor is pelephone israel.

thank you for your time and efforts, i'm looking forward to the solution and to 10.04
amit lockzhinsky Israel:p

---

### Post by pdc on 2010-04-03
1) why don't you type

> lsusb

in a terminal and tell us what you get .........

2) do you get an icon on your desktop when you insert this modem?

If so, right-click on the icon; go down the menu and select "eject" near the bottom;

pause a bit ...

... then in a terminal type

> lsusb

again, copy and paste what you get

---

### Post by DeadKennedys on 2010-07-13
.................@ubuntu:~$ lsusb 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 006: ID 05c6:f000 Qualcomm, Inc. [/COLOR]
Bus 001 Device 004: ID 04f2:b057 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

With modem Telit U9 by Pelephone





................@ubuntu:~$ lsusb 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b057 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Without modem


"wvdialconf" command
...............@ubuntu:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
Help please;)

---

### Post by pdc on 2010-07-13
many of these devices are initially seen as CD-ROM storage devices as they are loaded with software ..

so linux needs to change their ID so they are seen as modems ..

the programme usb_modeswitch does this ..

.. it needs to be installed as an extra ..

your device 

> 05c6:f000 Qualcomm, Inc. 

is recognised by usb_modeswitch 

> # Siptune LM-75 ("LinuxModem")
#
# Contributor: Antti Turunen

;DefaultVendor=  0x05c6
;DefaultProduct= 0x[B]f000
[/B]
;TargetVendor=   0x05c6
;TargetProduct=  0x**9000**

;MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

so if you download and install usb_modeswitch the device should be seen as a modem 

go here

[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)

go down to "Download usb_modeswitch" and if you are using 32bit ubuntu download the i386 version;

let the programme install as it is downloaded ....

reboot .....

try lsusb again it should now say 

> 05c6:**9000**

and you should be able to configure as per here

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

go halfway down page to 

"Create a mobile broadband connection" ..............

---

### Post by DeadKennedys on 2010-07-13
After installation i'm  dont see any change in terminal:
.................@ubuntu:~$ lsusb 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse  6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 001 Device 006: ID 05c6:f000 Qualcomm, Inc. [/COLOR]
Bus 001 Device 004: ID 04f2:b057 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


How i can to see end edit this information in terminal:
> # Siptune LM-75 ("LinuxModem")
#
# Contributor: Antti Turunen

;DefaultVendor=  0x05c6
;DefaultProduct= 0x[B]f000
[/B]
;TargetVendor=   0x05c6
;TargetProduct=  0x**9000**

;MessageContent="5553424312345678000000000000061b0   00000020000000000000000000000"                        ?
Sorry about stupid  question. |I'm novice in the Linux:p

---

### Post by pdc on 2010-07-13
so you have installed usb_modeswitch

best if you join their forum: Josh who oversees the programme oversees the forum too; you will get a quick response;

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

join up; get his help; if all gets going, let us know here

best wishes

---

### Post by DeadKennedys on 2010-07-15
After re-installing the usb-modeswitch created files /dev/ttyUSBx ,when X =  0-2.
Now i  see the connection point in list but it still don't connect to the Internet,and after few seconds make log out.The log-in, password and ports are correct ,i check it with my provider. The modem run correct  with Windows.


................@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse  6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 05c6:9000 Qualcomm, Inc. 
Bus 001 Device 003: ID 04f2:b057 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
................@ubuntu:~$ sudo modprobe usbserial vendor=0x05c6  product=0x9000
................@ubuntu:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600  baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600  baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: Telit
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<Info>: Device or resource busy

Found a modem on /dev/ttyUSB1.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp17463':  Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf'  ('/etc/wvdial.conf'): Bad file descriptor
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2  +FCLASS=0"
................@ubuntu:~$

---

### Post by pdc on 2010-07-16
so your device is now switching, so should be seen as a modem

> 05c6:9000 Qualcomm, Inc. 

where before you got 

> 05c6:f000 Qualcomm, Inc. 

you should now be able to configure and many would just use network manager first, before wvdial ......... curious why you want to use that

if you go half-way down this page

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

to create a mobile broadband connection: any joy?

I have attached a jpg of what a Pelephone default settings should be

let us know how it goes

---

### Post by DeadKennedys on 2010-07-16
I do create connection, and option in  connection as in youre screenshot. But  when i try to connect with Pelephon 3G connection , it's show " GSM Log Out", after trying connection.

---

### Post by pdc on 2010-07-19
I can only suggest you download and install sakis3g

[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

