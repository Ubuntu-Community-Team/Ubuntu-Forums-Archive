---
title: "Micromax Q75 to connect as gprs modem - Please help"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by jsmanian on 2010-10-23
Hello,

        I am trying to connect my q75 micromax mobile with my computer as modem using wvdial. But I could not connect as modem. I insalled wvdial, gnome-ppp and mode switch through synaptic package manager. 

This is the message I got from terminal window. After this, there is no connection. I closed the terminal window using ctrl+C command. My mobile is dual sim phone. I want to connect through one ISP provider for GPRS. How to set this in wvdial configuration file.  Please help me to resolve this.

> subramanian@subramanian:~$ sudo wvdialconf
[sudo] password for subramanian: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- ERROR
ttyACM0<*1>: Modem Identifier: ATI -- MTK2
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
subramanian@subramanian:~$ sudo gedit /etc/wvdial.conf
subramanian@subramanian:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!}!} }2}"}&} }*} } }#}$@#}'}"}(}"U[03]~
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Oct 24 01:57:12 2010
--> Pid of pppd: 2961
--> Using interface ppp0
--> pppd: pX[19] &#65533;^[19] 
--> pppd: pX[19] &#65533;^[19] 
--> pppd: pX[19] &#65533;^[19] 
--> pppd: pX[19] &#65533;^[19] 
--> pppd: pX[19] &#65533;^[19] 
--> local  IP address 27.57.213.230
--> pppd: pX[19] &#65533;^[19] 
--> remote IP address 10.64.64.64
--> pppd: pX[19] &#65533;^[19] 
--> primary   DNS address 202.56.230.5
--> pppd: pX[19] &#65533;^[19] 
--> secondary DNS address 202.56.240.5
--> pppd: pX[19] &#65533;^[19]This is the output for lsusb command

> subramanian@subramanian:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 009: ID 0e8d:0003 MediaTek Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

This is my wvdial conf file

> Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyACM0
Username = < >
Password = < >
Baud = 460800with regards,
jsmanian

---

### Post by alexfish on 2010-10-23
Hi

according to the info

--> remote IP address 10.64.64.64
--> pppd: pX[19] &#65533;^[19]
--> primary DNS address 202.56.230.5
--> pppd: pX[19] &#65533;^[19]
--> secondary DNS address 202.56.240.5
--> pppd: pX[19] &#65533;^[19]

your connected to the Internet

if firefox not working

[LIST]
[*][SIZE=1][COLOR=#000000]if the browser is not working check the "Work Off line" is unchecked {notable with Mozilla Firefox}[/COLOR][/SIZE][SIZE=1] **[Fix it HERE]("http://kb.mozillazine.org/Toolkit.networkmanager.disable")**[/SIZE]
[*][SIZE=1]Tip for the Mozzila Firefox fix ,After opening Firefox, try opening page "about:config"... Filter for "toolkit.networkmanager.disable"[/SIZE]
[*][SIZE=1]Change the line to ....." toolkit.networkmanager.disable;true "[/SIZE]
[/LIST]
[SIZE=1]are there other problems

alexfish
[/SIZE]

---

### Post by jsmanian on 2010-10-23
Hi,

  Thanks for your help. This helped me to solve this issue. And also I tried procedure mentioned in this link also.

[http://ubuntuforums.org/archive/index.php/t-931872.html](http://ubuntuforums.org/archive/index.php/t-931872.html)

Thanks for you time and help:P

with regards,
jsmanian

---

