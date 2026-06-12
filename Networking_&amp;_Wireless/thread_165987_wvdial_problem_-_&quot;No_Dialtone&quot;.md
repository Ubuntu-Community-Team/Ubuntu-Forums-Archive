---
title: "wvdial problem - &quot;No Dialtone&quot;"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by gr0kzer0 on 2006-04-25
I'm trying to get my newly-enabled ltmodem working, with the following results:

> t0p@lapt0p:~$ sudo wvdial
Password:
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT08456042086
--> Waiting for carrier.
ATDT08456042086
NO DIALTONE
--> No dial tone.
--> Disconnecting at Tue Apr 25 20:11:45 2006
t0p@lapt0p:~$

This makes no sense to me. If I plug a phone into the phone wall socket, it gets a dial tone ok and works fine.

This is my /etc/wvdial.conf file:

> [Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = 08456042086
Username = foobar
Password = foobar


Anyone got _any_ idea what's going on here and how I might put it right?

---

### Post by xrmuser on 2006-04-27
Just make sure the rj-11 cable is compatible with your modem. I think you should try another rj-11 phone line that came from your modem, if you did not try it yet. Usually this wire is 1 meter long.

---

### Post by gr0kzer0 on 2006-04-27
Thanks for the reply! When u say try another cable... are there different kinds? I havent got the cable packaging anymore, but IIRC the only differencies in cables were length and what plug was on the end. Is there another difference? What's it called? I thought modem-phone socket cables were a standard, 'all the same' kind of thing?

---

### Post by mesocool on 2006-06-09
[QUOTE=gr0kzer0]I'm trying to get my newly-enabled ltmodem working, with the following results:



This makes no sense to me. If I plug a phone into the phone wall socket, it gets a dial tone ok and works fine.

This is my /etc/wvdial.conf file:



Anyone got _any_ idea what's going on here and how I might put it right?[/QUOTE]


I have the same problem. Actually, the driver works for my desktop internal modem, but for my laptop modem, it gives me "no dial tone" error message..

---

