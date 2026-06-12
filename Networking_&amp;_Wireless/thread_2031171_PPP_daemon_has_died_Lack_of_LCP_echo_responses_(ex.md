---
title: "PPP daemon has died: Lack of LCP echo responses (exit code = 15)"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by saravanang86 on 2012-07-21
Hi.,

 When i am connecting Reliance netconnect+ i got NEW CDMA COnnection got detected and i gave my reliance option and usrname and passwrd in my mobile communication then i tryed in my terminal wvdial ,I got internet connection for few minutes then it will gone...
My ubuntu version is :
Linux subuntu 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
My /etc/wvdial.conf configuration is :
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
 Phone = #777
 Password = 9XXXXXXXX
 Username = 9XXXXXXXX (here i hide my username and password :) )


when i type wvdial :

root@subuntu:/home/saravanan# wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
NO CARRIER
AT+CSQ?
+CSQ:0,99
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 3100000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sat Jul 21 19:22:06 2012
--> Pid of pppd: 3600
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> local  IP address 115.184.52.71
--> pppd: &#65533;[7f]
--> remote IP address 220.224.141.145
--> pppd: &#65533;[7f]
--> primary   DNS address 220.226.6.104
--> pppd: &#65533;[7f]
--> secondary DNS address 220.226.100.40
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> Connect time 3.0 minutes.
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> Disconnecting at Sat Jul 21 19:25:08 2012
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)

Here i attached my syslogfile.doc ..
kindly guide me...

regards
Saravanang

---

