---
title: "Huawei EC 325 (Reliance)- Ubuntu 8.10,  On Compaq Presario Laptop 6000"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by satksri on 2009-03-30
Huawei EC 325 (Reliance) On Compaq Presario Laptop 6000
I have just switched from WinXP, to Ubuntu 8.10 (i386) on a compaq presario 6000 dual core laptop (AMD 64); I am using a USB Huawei data card- EC 325 (my service provider is Reliance). I am unable to connect to internet. can anyone help, please? The problem is last two lines in the output:

"Unable to run /usr/sbin/pppd.

--> Check permissions, or specify a "PPPD Path" option in wvdial.conf."


-------------------------------------------

First I edited my wvdial.conf; this is how it looks now:

Content of /etc/wvdial.conf



[Dialer defaults]

Modem = /dev/ttyUSB0
ISDN = off

Modem Type = USB Modem

Baud = 460800

Init = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777


Dial Attempts = 1

Dial Command = ATM1L3DT
Ask Password = off

Password = 9319923412
Username = 9319923412

New PPPD = yes
Auto Reconnect = off

Abort on Busy = off

Carrier Check = on

Check Def Route = on

Abort on No Dialtone = on

Stupid Mode = on
Idle Seconds = 0

Auto DNS = on


-------------------------------------------

Next when I ran sudo wvdial in terminal window, this is the output I got:

sachin@sachin-laptop:~$ wvdial

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

--> Sending: ATM1L3DT#777

--> Waiting for carrier.
ATM1L3DT#777
CONNECT 230400

--> Carrier detected. Starting PPP immediately.

--> Unable to run /usr/sbin/pppd.

--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

-----------------------------------------
I will appreciate any help..
sachin from Dehradun
satksri is offline Report Post   	Edit/Delete Message

---

