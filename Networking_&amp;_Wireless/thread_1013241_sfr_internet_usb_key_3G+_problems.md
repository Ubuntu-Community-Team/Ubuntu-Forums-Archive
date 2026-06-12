---
title: "sfr internet usb key 3G+ problems"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by Payteer on 2008-12-16
Hello, 
I am on 8.10 and using a thinkpad x61.  I have just signed up to SFR internet 3G+.  This is in France I know, but someone might know how to get working.  SFR support the eeepc with linux so I thought it should work, but it doesn't, can some one point me in the right direction.  The key is flashing red, but I can not get it started.

Thanks

---

### Post by alzaf on 2008-12-16
I copied the contents of a webpage into a text file for reference, lost the link though. You can either set up /etc/wvdial.conf as below or set up a mobile broadband connection in network manager. The best way is to install it on windows first so you can get the details ie Phone number, username and password.

Details of webpage:
Luckily, this is very straight forward. If you plug your USB "dongle" in before you start Ubuntu, it will recognise it off the bat. However, the one drawback is it doesn't if you hot plug. I've yet to get the time to tie down why this is, but it's a minor inconvenience.

Next I configured the wvdial software by putting the following into /etc/wvdial.conf

[Dialer Defaults]
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = 
Modem = /dev/ttyUSB0
Username = 
Dial Command = ATDT
Password = 
Baud = 460800
Init3 = AT+CGDCONT=1,"IP","general.t-mobile.uk"

Now by running wvdial in a terminal session I see: -

troyski@troyski-laptop:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=1,"IP","general.t-mobile.uk"
WvDial Modem<*1>: AT+CGDCONT=1,"IP","general.t-mobile.uk"
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#
WvDial Modem<*1>: CONNECT
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Tue Nov 20 09:21:46 2007
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 9880
WvDial<*1>: Using interface ppp0
WvDial<*1>: local  IP address 10.33.187.125
WvDial<*1>: remote IP address 10.64.64.64

---

### Post by Payteer on 2009-01-12
hello again,  well i understand it is the same as vodafone's dongle so i installed the vodafone thingy from betavine and it works some of the time and other times crashes the computer or shuts it down completely and other time it is perfect.  i am on intrepid so I understand WvDial doesn't work on this system unlike 8.04

---

