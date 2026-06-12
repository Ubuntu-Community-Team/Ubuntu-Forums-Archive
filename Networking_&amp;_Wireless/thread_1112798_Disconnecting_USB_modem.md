---
title: "Disconnecting USB modem"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by satksri on 2009-04-01
I am able to connect my USB Huawei EC 325 card by using WVDIAL.conf but cant disconnect, isnpite of using commnads like 'disconnect' 'quit' etc. Can some please help?
I have to physically disconnect.
Here is the out put, when I run wvdial command:

sachin@sachin-laptop:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT 230400
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Mar 31 09:14:09 2009
--> Pid of pppd: 6124
--> Using interface ppp0
--> pppd: P&#65533;&#65533; 
--> pppd: P&#65533;&#65533; 
--> pppd: P&#65533;&#65533; 
--> pppd: P&#65533;&#65533; 
--> local  IP address 123.239.145.65
--> pppd: P&#65533;&#65533; 
--> remote IP address 220.224.134.70
--> pppd: P&#65533;&#65533; 
--> primary   DNS address 202.138.97.193
--> pppd: P&#65533;&#65533; 
--> secondary DNS address 202.138.96.2
--> pppd: P&#65533;&#65533; 
quit
^CCaught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: P&#65533;&#65533; 
--> Connect time 5.3 minutes.
--> pppd: P&#65533;&#65533; 
--> pppd: P&#65533;&#65533; 
--> Disconnecting at Tue Mar 31 09:19:32 2009
sachin@sachin-laptop:~$

---

### Post by GeorgeVita on 2009-04-01
Hi **satksri**

When you connect using **wvdial** from a terminal window, to disconnect you press **CTRL-C** at the same window.

You have done it already:

> **satksri said:**
> ...
--> pppd: P&#65533;&#65533; 
--> secondary DNS address 202.138.96.2
--> pppd: P&#65533;&#65533; 
quit
**[COLOR="Red"]^C[/COLOR]**Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: P&#65533;&#65533; 
--> Connect time 5.3 minutes.
--> pppd: P&#65533;&#65533; 
--> pppd: P&#65533;&#65533; 
--> Disconnecting at Tue Mar 31 09:19:32 2009
sachin@sachin-laptop:~$

Regards,
George

---

### Post by satksri on 2009-04-01
Hey, George- thanks a lot. I am newbie and at 52, and been using win- so obvious was not so obvious! Thanks a lot!
satksri

---

