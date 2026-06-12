---
title: "LG U990 + wvdial problem"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Fubrite on 2008-12-06
Hi,

I hope someone here will be willing and able to help me with this problem. I am reasonably new to Ubuntu and Linux, and am trying to set up mobile broadband through my LG U990 (Viewty) phone on Three network. It is connected through it's USB cable, and works perfectly under Win XP (same laptop - it's dual boot). I am using Ubuntu 8.04.

I have run wvdialconf and edited the file to read:-

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem = /dev/ttyACM0
# Phone = *99#
Modem Type = USB Modem
Stupid Mode = 1
Auto DNS = yes
New PPPD = yes
Baud = 460800
Dial Attempts = 2

[Dialer three]
Init1 = ATZ
Init5 = AT+CGDCONT=1,"IP","3internet"
Modem Type = USB Modem
ISDN = 0
Username = three
Password = three
Phone = *99#

I then run sudo wvdial and get:-

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Dec  6 21:58:42 2008
--> Pid of pppd: 21221
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> Using interface ppp0
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> Authentication (CHAP) started
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> Authentication (CHAP) successful
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#544;[06][08]&#544;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Sat Dec  6 21:58:45 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

and /var/log/messages has:-

Dec  6 21:58:42 Notebook pppd[21221]: pppd 2.4.4 started by root, uid 0
Dec  6 21:58:43 Notebook pppd[21221]: Using interface ppp0
Dec  6 21:58:43 Notebook pppd[21221]: Connect: ppp0 <--> /dev/ttyACM0
Dec  6 21:58:43 Notebook pppd[21221]: CHAP authentication succeeded
Dec  6 21:58:43 Notebook pppd[21221]: CHAP authentication succeeded
Dec  6 21:58:44 Notebook pppd[21221]: Modem hangup
Dec  6 21:58:44 Notebook pppd[21221]: Connection terminated.
Dec  6 21:58:44 Notebook pppd[21221]: Exit.


I have tried disabling all my network connections to no avail, and have spent the last two days googling with no results. Can someone please point me in the right direction?

---

