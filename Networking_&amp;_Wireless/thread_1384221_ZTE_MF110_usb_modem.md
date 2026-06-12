---
title: "ZTE MF110 usb modem"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by reallybadgrizzly on 2010-01-18
Hello,

my system is Kubuntu 9.04, x86, kernel 2.6.28-11-generic
I have a 3G usb modem ZTE MF110, WCDMA 2100 MHz and a problem connecting with it to the #g network available


I get a fatal error when I try to  install it
I locked at the readme.txt, and I have done everything that is written there, I have installed the dependencies qt3 and wvdial with the apropiate libs and I followd the instuctions
when i enter in the terminal ./install.sh immediatlly I get an error saying:
 ..................start install.................                                          
*** Check for root...ok...                                                                
./zr: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory                                                                                              

after that the installation goes on and at the end I get 

enter driver_install function
FATAL: Error inserting zte (/lib/modules/2.6.28-11-generic/kernel/drivers/usb/serial/zte.ko): Invalid module format
disselfirefox.pp driver_install.run nm.pp se End to /opt/ZMC/driver
install completed!!!
....After setup, you will find the ZMC in "Applications->Internet->ZMC". Click the ZMC and the application will run

i appreciat any help

---

### Post by alexfish on 2010-01-18
hi

Could you post details of the driver and where it was downloaded from

thanks in advance

---

### Post by reallybadgrizzly on 2010-01-19
at first I found the driver on the modem , the after googleing I found [http://http://www.filehost.ro/664504/PCL_ZTEDCV_tar_gz/]("http://http://www.filehost.ro/664504/PCL_ZTEDCV_tar_gz/") this , it is the same , the same error
 the progres of instalation and the error (I attached a txt file containing the same progres):
#####################

..................start install.................                                   
*** Check for root...ok...                                                         
./zr: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory                                                                                              
Get resouse file successfully.                                                                           
ZMC/                                                                                                     
ZMC/usr/                                                                                                 
ZMC/usr/share/                                                                                           
ZMC/usr/share/pixmaps/                                                                                   
ZMC/usr/share/pixmaps/ZMC.png                                                                            
ZMC/usr/share/applications/        
.......  and so on until
ZMC/Data/help/help.html
ZMC/Data/historyRecord.xml
ZMC/ZMC
ZMC/UpdateCfg.ini
ZMC/uninstall.sh
ZMC/bin/
ZMC/bin/9-cdrom.rules
ZMC/bin/ZMC
udevadm control commands requires the --<command> format, this will stop working in a future release
udevadm is exist!
******Begin to /opt/ZMC/driver
this is linux driver installtion
this is ubuntu9.04  formal kernel
enter driver_install function
FATAL: Error inserting zte (/lib/modules/2.6.28-11-generic/kernel/drivers/usb/serial/zte.ko): Invalid module format
disselfirefox.pp driver_install.run nm.pp se End to /opt/ZMC/driver
install completed!!!
....After setup, you will find the ZMC in "Applications->Internet->ZMC". Click the ZMC and the application will run
press any key to continue....

---

### Post by alexfish on 2010-01-19
hi

do you have 
(qt3 and wvdial). installed

just noticed in your post (yes)

have you configured the wvdial

---

### Post by reallybadgrizzly on 2010-01-19
I`ve run the #wvdialconf /etc/wvdial.conf command and the output is 

#########################
Editing `/etc/wvdial.conf'.                                                                              

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- ERROR
ttyUSB1<*1>: ATQ0 V1 E1 &C1 -- ERROR
ttyUSB1<*1>: ATQ0 V1 E1 &D2 -- ERROR
ttyUSB1<*1>: ATQ0 V1 E1 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: ZTE CORPORATION
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- ERROR
ttyUSB2<*1>: ATQ0 V1 E1 &C1 -- ERROR
ttyUSB2<*1>: ATQ0 V1 E1 &D2 -- ERROR
ttyUSB2<*1>: ATQ0 V1 E1 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: ZTE CORPORATION
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB1.
Modem configuration written to /etc/wvdial.conf.
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 +FCLASS=0"

##############################

At last I`ve installed the software Join Air, but the modem doesn`t initilize and the soft doesn`t see the modem
I`ve installed getllibs and run "getlibs -l libqt3-mt" this converts a 32bit library into a library that works in x86 and modified the line 

TWO_FRASE_CONFIG_FILE_MODEM=/PCCFG/Description.xml  in install.sh into
TWO_FRASE_CONFIG_FILE_MODEM=TWO_FRASE_TEMP_DIR/Description.xml

I read somewhere that a dude installed it like this, the installation: the error with libqt3 seems to be rezolved but the  
FATAL: Error inserting zte (/lib/modules/2.6.28-11-generic/kernel/drivers/usb/serial/zte.ko): Invalid module format
is still here

so ??? enyone?

---

### Post by alexfish on 2010-01-19
hi

Not sure if the configuration is correct {ttyUSB1}

In the mean time could you have a browse at this site

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

I am not certain if the Fatal Error is relevant at This stage

---

### Post by pdc on 2010-01-19
it would seem with this modem; that it needs to be "flipped" from being seen as virtual storage device, to being seen by linux as a modem;

so I am not clear if all the clever background software that you have installed has done some of this;

so maybe it would help you to type

> lsusb

and tell us what your device is seen as ..........

ie is it ..

> 19d2:0053

or 

> 19d2:0031

and you have tried to set up the /etc/wvdial.conf file

If you let us see what it looks like so type 

> gedit /etc/wvdial.conf

and copy and paste it all here .........

and if you tell us the country and the network you need to connect to; we can check on the APN settings that you need

---

### Post by reallybadgrizzly on 2010-01-20
hello and thank you for your time and effort,

When I connect the modem it mounts like a cd-rom automatically, and I`ve read that it must be umounted before use
mounted the output of lsusb is Bus 002 Device 012: ID 19d2:0053
and umounted Bus 002 Device 013: ID 19d2:0016

the output of #cat /etc/wvdial.conf 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB1
ISDN = 0
; Phone = <Target Phone Number>
; Password = <Your Password>
; Username = <Your Login Name>

I`m from Romania and the network I`ve been trying to connect to is RDS (digi)
I`ve managed to install the software after googleing for hours but I can`t connect the modem 
when I run driver-install.run in the /opt/ZMC/driver/ dir I get the same error when I install the join air 

FATAL: Error inserting zte (/lib/modules/2.6.28-11-generic/kernel/drivers/usb/serial/zte.ko): Invalid module format

---

### Post by alexfish on 2010-01-20
hi

you need to remove " ; " and fill the details

; Phone = <Target Phone Number>  
; Password = <Your Password>
; Username = <Your Login Name>

Example:

 Phone = *99#
 Password =  web
 Username = web

ask your service provider

if it fails then we will look at the Fatal error

---

