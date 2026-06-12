---
title: "huawei E169 setup for optus network"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by BlackKnight7891 on 2009-11-01
Hey guys im having trouble getting my E169 connected to the internet provider.

to begin with i couldn't get the modem detected within ubuntu 9.10 as a modem but following the directions below sorted that out thanks dj-toons.
[http://ubuntuforums.org/showthread.php?t=1306441](http://ubuntuforums.org/showthread.php?t=1306441) 

Now i have that sorted and Gnome PPP installed,

ran the command 

sudo wvdialconf /etc/wvdial.conf

below is my config file
=====================================
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","888a1" 
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
New PPPD = yes
Modem = /dev/ttyUSB0
Username = default
Password = default
Baud = 9600
==============================
When i start the connection sometime it establishes a link but doesnt recieve any connection information.

otherwise i see the below log

==================================
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
--> Sending: AT+CGDCONT=1,"IP","888a1"
AT+CGDCONT=1,"IP","888a1"
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
^BOOT:18464705,0,0,0,72
ATM1L3DT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
NO CARRIER
--> No Carrier!  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Mon Nov  2 10:49:51 2009
=============================================


What have i done wrong:(

---

### Post by BlackKnight7891 on 2009-11-03
okay, i've given up with 9.10 for now trying to get this working.

Installed ubuntu 9.04, modem seems to be recognised and the connection wizard took me through all the steps.

I have my APN set in the configuration and ipv4 set to "Automatic (PPP)"

I have also manual set the DNS servers which didnt change the out come.


Log file
======================
/var/log/messages
pppd 2.4.5 started by root, uid 0
user interface ppp0
Connect: CHAP authentication succeeded
Connect: CHAP authentication succeeded
Modem hangup
Connection terminated
Exit
=====================

I dont have wvdial installed yet on this build

---

### Post by pdc on 2009-11-03
have you googled on Optus and linux and Huawei 169?

I tried to get set up using a Virgin 169 modem recently whilst in Oz; (I got 3 and Vodafone to work well)

I got the types of errors you did; my googling led me to disabling chap etc etc .......... a wilderness ..........

whirlpool forums in Oz have a linux support page : see if you google that; some good Ozzie linux support there

---

