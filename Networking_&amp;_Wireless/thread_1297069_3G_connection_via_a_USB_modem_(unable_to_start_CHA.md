---
title: "3G connection via a USB modem (unable to start CHAP authentication)"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by sivahuang on 2009-10-21
I searched the forum but could not find similar thread.

Here is the problem I met. I am trying to establish internet connection through a USB modem by wvdial. The carrier is Chunghwa telecom in Taiwan and here are my settings:

Ubuntu 8.04 LTS (newly installed)
USB modem VID: 05C6; PID: 9002

[B]1. modprobe usbserial vendor=0x05c6 product=0x9002
2. wvdial.conf[/B]
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
;Modem = /dev/ttyUSB2
Modem = /dev/modem
Modem Type = Analog Modem
Baud = 460800
ISDN = 0
New PPPD = yes

Dial Command = ATM1L3DT
Phone = *99#
Username = username
Password = password
Abort on Busy = 1
Abort on No Dialtone = 1
Carrier Check = 0
Check Def Route = 0
Check DNS = 0
DNS Test1 = 0
Auto Reconnect = 1
Stupid Mode = 1

**3. wvdial log**
root@Vanadiel:/home/siva# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Oct 21 23:14:42 2009
--> Pid of pppd: 9266
--> pppd: [08]&#65533;[06][08]
--> Using interface ppp0
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]  [COLOR=Red]**<--- I was expecting CHAP authentication starts...**[/COLOR]
--> pppd: [08]&#65533;[06][08]  [COLOR=Red]**<--- but it didn't...**[/COLOR]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> pppd: [08]&#65533;[06][08]
--> Disconnecting at Wed Oct 21 23:15:13 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Wed Oct 21 23:15:14 2009
root@Vanadiel:/home/siva# 


I tried Novatel MC950D by the exact same config file and procedure. I can see CHAP authentication starts and completed successfully, and the internet connection is established.

Is there any step I missed? 


-Siva
[EMAIL="-siva.huang@gmail.com"]-siva.huang@gmail.com[/EMAIL]

---

