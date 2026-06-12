---
title: "get connected but still some problem"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by kaliyaodi on 2010-07-06
Hello,

I want to connect to the internet with my Nokia 2600c and Ubuntu 8.04.

I did wat the Howto said but I get this an error output. First my config:
```
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = tmobile
Password = tmobile
Stupid Mode = 1
```(I found on the t-mobile site I should make Username and Password tmobile)

Next the output of the wvdial (as sudo)

     Code:
```
reinier@reinier-laptop:~$ sudo gedit /etc/wvdial.conf
reinier@reinier-laptop:~$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Mon Dec  3 12:31:18 2007
WvDial<Notice>: Pid of pppd: 32537
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: Disconnecting at Mon Dec  3 12:31:24 2007
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds
```And the hole thing will try to reconnect without any result. I even got my phone connected but that doesn't work...

Got any suggestions?                                 Anybody?

---

### Post by mörgæs on 2010-07-07
I don't know much about analog modems, but in general I would try 9.10 and / or 10.04 rather than 8.04 as a first step. 

You could also try a lower baud rate.

---

