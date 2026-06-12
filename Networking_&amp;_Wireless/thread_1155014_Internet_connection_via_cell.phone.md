---
title: "Internet connection via cell.phone"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Luca1963 on 2009-05-10
Hi,
I can't connect to the Internet using mySony-Ericsson V640i with Ubuntu 8.10 intalled on a Samsung N110 Notebook.

I have also Ubuntu 8.04 installed on a Dell Latitude and I connect to the Internet with the same phone and the same operator (H3G). I run wvdial with the following file:

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud =460800
Init = AT&F
Init2 = AT+CGDCONT=3,"IP","tre.it",,0,0
# Init3 = ATQ0 V1 E1 S0=0 &C1 & D2 +FCLASS=0
# Init2 = AT+CGATT=3, "IP", "apn.tre.it",,0,0
ISDN = 0
Modem Type = Analog Modem
Carrier Check = no
Phone = *99***3#
Username = ''
Password = ''

and everything is OK.

I don't understand why the same file doesn't work on the Samsung N110 and Ubuntu 8.10

On both PC (Samsung and Dell) I have also Windows XP and I connect using a tool that is provided with the cellular phone.

I wonder why the command file (wvdial.conf) should depend on the version of Ubuntu or the PC... 

Any suggestion ?

Thanks a lot

Luca

---

### Post by GeorgeVita on 2009-05-10
Hi **Luca1963**,
possibly 8.10 "sees" differently your phone-modem and attaches another /dev/ttyxxx port.

Please post here any "error" message trying to connect with the 8.10 system.

Also do some other tests from a terminal window:

**lsusb** will show the vendorID and productID (could be used to "trim" network manager in 8.10)
**ls /dev/ttyU* /dev/ttyA*** will list the associated serial ports
**dmesg** (some seconds after attaching the modem) will show system activity and what are the differences between 8.04 and 8.10

Post some of the above if you need more assistance.

Regards,
George

---

