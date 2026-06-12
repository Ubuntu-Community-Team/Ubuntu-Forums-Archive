---
title: "problem with wvdial on ubuntu 9.04"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by himanee on 2009-10-02
hello,
i am a new member here and also not quite well known to ubuntu 9.04. i have successfully installed wvdial on ubuntu 9.04 but it is still giving problem to connect a netconnect modem. here are the errors occurring. can somebody please help me? i have changed wvdial.conf and usbswitch.conf appropriately. also in lsusb it detects the device with correct vendor id and product id.
 
himanee@himanee-laptop:~$ wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.
Scanning your serial ports for a modem.
Modem Port Scan<*1>: S0 S1 S2 S3 
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: HUAWEI TECHNOLOGIES CO., LTD
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
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: +GMI: HUAWEI TECHNOLOGIES CO., LTD
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf.tmp6501': Permission denied
/etc/wvdial.conf<Warn>: Can't write '/etc/wvdial.conf' ('/etc/wvdial.conf'): Bad file descriptor
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
 
 
 
himanee@himanee-laptop:~$ sudo wvdial
[sudo] password for himanee: 
--> WvDial: Internet dialer version 1.60
--> Warning: inherited section [Modem0] does not exist in wvdial.conf
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
himanee@himanee-laptop:~$ sudo wvdial netconnect
--> WvDial: Internet dialer version 1.60
--> Warning: inherited section [Modem0] does not exist in wvdial.conf
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Fri Oct 2 16:09:16 2009
--> Pid of pppd: 6520
--> Using interface ppp0
--> pppd: ï¿½T][08]ï¿½R][08]
--> pppd: ï¿½T][08]ï¿½R][08]
--> pppd: ï¿½T][08]ï¿½R][08]
--> pppd: ï¿½T][08]ï¿½R][08]
--> Disconnecting at Fri Oct 2 16:09:24 2009
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

---

### Post by Bartender on 2009-10-02
Well, it *looks* like you connected but wvdial did not present the correct username and password.

---

### Post by 85DropTopTA on 2009-10-02
first your wvdial.conf file did not save because you did not use "sudo" before your command.  if you look at the end it says access was denied 

also remember to delete the ";" before the username, password, and phone number lines in the wvdial.conf file.

my 3 simple steps to getting a evdo modem to work

sudo wvdialconf

sudo gedit /etc/wvdial.conf   

         insert your username password, and phone number 
         also delete the ; before those lines

sudo wvdial
           then you should be online

---

