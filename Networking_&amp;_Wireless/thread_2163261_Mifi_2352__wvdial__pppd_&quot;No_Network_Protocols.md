---
title: "Mifi 2352 / wvdial / pppd &quot;No Network Protocols runnung&quot;"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by christian2002 on 2013-07-17
Hi,

i have a problem with my Mifi 2352 UMTS Modem.
I managed to disable the useless ZeroCD and the modem is detected by Linux.

Now i tryed to connect to my provider "Vodafone".
I used wvdial, but the pppd gived up.

I used this configuration which works perfect on my Huawei E172.

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","web.vodafone.de"
Init4 = AT$QCPDPP=1,0
# Modem Type = USB Modem
Baud = 10000000
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Password = web
Username = web
Stupid mode = 1

```

I tryed to change the Speed, change the Modem Type Value and tryed /dev/ttyUSB1 and /dev/ttyUSB2 ,too.
But i always get the same Errors from pppd.

_**/var/log/messages**_

```
Jul 17 23:35:43 Onemini pppd[6114]: pppd 2.4.5 started by root, uid 0
Jul 17 23:35:43 Onemini pppd[6114]: speed 10000000 not supported
Jul 17 23:35:43 Onemini pppd[6114]: Using interface ppp0
Jul 17 23:35:43 Onemini pppd[6114]: Connect: ppp0 <--> /dev/ttyUSB0
Jul 17 23:35:43 Onemini pppd[6114]: CHAP authentication succeeded
Jul 17 23:35:43 Onemini pppd[6114]: CHAP authentication succeeded
Jul 17 23:36:14 Onemini pppd[6114]: [COLOR=#ff0000]IPCP: timeout sending Config-Requests[/COLOR]
Jul 17 23:36:14 Onemini pppd[6114]: Connection terminated.

```

```
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","web.vodafone.de"
AT+CGDCONT=1,"IP","web.vodafone.de"
OK
--> Sending: AT$QCPDPP=1,0
AT$QCPDPP=1,0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT HSDPA 7.2
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Jul 17 23:42:51 2013
--> Pid of pppd: 6157
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> Using interface ppp0
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> Authentication (CHAP) started
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> Authentication (CHAP) successful
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> [COLOR=#ff0000]Terminate Request (Message: "No network protocols running" )[/COLOR]
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> pppd: 0[18]» [08] » `[18]» °[18]» Ð[18]»
--> Disconnecting at Wed Jul 17 23:43:24 2013
--> The PPP daemon has died: Pty program error (exit code = 9)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

```

Does anyone know, what i need to do ? Do i need another Init String or is it a driver problem (Drivername "option1") ?
I can send commands to the Modem using minicom. It seems the drivers and communication with the modem ist ok.

Please no hints like "use Wifi instead" :-) I know, the Mifi 2352 is a Wireless Router, too. But i need the USB Modem feature of the device ;-)

Greetings,

Chris

---

### Post by wildmanne39 on 2013-07-17
Thread closed. Please do not post duplicates, it dilutes community effort.
[http://ubuntuforums.org/showthread.php?t=2163262](http://ubuntuforums.org/showthread.php?t=2163262)

---

