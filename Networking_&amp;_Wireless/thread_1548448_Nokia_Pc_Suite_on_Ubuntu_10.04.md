---
title: "Nokia Pc Suite on Ubuntu 10.04"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by LucianUk on 2010-08-08
root@ubuntu:/home/ubuntu# lsusb
Bus 002 Device 003: ID 0421:008f Nokia Mobile Phones 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5130 IMC Networks 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@ubuntu:/home/ubuntu# /sbin/modprobe usbserial vendor=0x421 product=0x08f
root@ubuntu:/home/ubuntu# wvdialconf create
Editing `create'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- Nokia
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"



root@ubuntu:/home/ubuntu# cat /etc/wvdial.conf
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = username
Password = password
Stupid Mode = 1




root@ubuntu:/home/ubuntu# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Aug  8 11:25:40 2010
--> Pid of pppd: 1960
--> Using interface ppp0
--> pppd: ?!A ?[18]A 
--> pppd: ?!A ?[18]A 
--> pppd: ?!A ?[18]A 
--> pppd: ?!A ?[18]A 
--> local  IP address 10.148.23.62
--> pppd: ?!A ?[18]A 
--> remote IP address 10.6.6.6
--> pppd: ?!A ?[18]A 
--> primary   DNS address 83.224.65.143
--> pppd: ?!A ?[18]A 
--> secondary DNS address 83.224.66.138
--> pppd: ?!A ?[18]A 


But I cannot connect to internet ... I have OFFLINE MODE 
I`m not sure but i think that is from this line
Bus 002 Device 003: ID 0421:008f Nokia Mobile Phones

A little help please ?!
I use Nokia 6220.

---

