---
title: "Error in wvdial while using auto reconnect..."
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by siddharth352001 on 2010-09-09
i am a mass internet downloader who would not mind keeping computer ON for downloading for days....

no of the problem with my internet connection is that it's connectivity drops when i m away......
so i enabled the function of auto reconnect by editing wvdial.conf

Auto Reconnect = 0

so when ever my connection get's disconnected, wvdial try to reconnect it....
but then following error occurs....


--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","bsnlnet"
AT+CGDCONT=1,"IP","bsnlnet"
OK
--> Modem initialized.
**--> Cannot open /dev/rfcomm0: Input/output error**

so i have to reconnect it manually after killing wvdial....
am i missing some thing....?

---

### Post by nickypatel on 2011-05-28
Hi,

I am using Ubuntu 7.10, and trying to connect to internet via tata indicom(epivalley) modem. 
I have following entry in my wvdial.conf fil.

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = AT+CRM=1
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = #777
Modem = /dev/modem
Username = internet
Password = internet
Baud = 460800

but while excuting wvdial command, i am getting initialization error.

WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CRM=1
WvDial Modem<*1>: AT+CRM=1
WvDial Modem<*1>: ERROR
WvDial<Err>: Bad init string.


can anyone please suggest what exactly is missing or if a different string needs to be initialized.

thanks in advance.

---

