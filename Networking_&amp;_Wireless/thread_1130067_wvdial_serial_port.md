---
title: "wvdial serial port"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by hasan iqbal on 2009-04-19
hi guys,
i'm newbie. i'm trying to set up a wvdial configuration file. but there was no field for serial port. but when i'm dialing it tells that there is a serial port error & my username, password, & my phone number is wrong. 

how can i fill them correctly?
thnx in advance.

---

### Post by AlanR8 on 2009-04-19
Try this. Backup your original file and paste the contents below:

> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = A
Username = B
Stupid Mode = 1

This works on Vodafone in the UK where the dial-up "number" is *99#. Connect your phone, select the correct mode on the phone then open a terminal type sudo wvdial then the password and your phone should connect.

---

