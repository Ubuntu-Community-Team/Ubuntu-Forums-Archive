---
title: "Unable to connect to internet in 8.10"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by mahendra.pardeshi on 2009-03-06
hi,
I have install ubuntu 8.10 and want to connect to internet.
I am using  tata indicomm **SXC-1080 CDMA 1x USB MODEM**.


Update the **wvdial.conf** file as.

[B]
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = #777
Username = internet
Password = internet
[/B]

After this save file and try to connect to internet by typing **wvdial ** and press enter on terminal.

fallowing text was printed in side terminal.

xyz@ubuntu:~$ wvdial


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
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.

Does any one have any idea about this.

---

### Post by hyperyoda on 2009-03-06
> **mahendra.pardeshi said:**
> hi,
I have install ubuntu 8.10 and want to connect to internet.
I am using  tata indicomm **SXC-1080 CDMA 1x USB MODEM**.


Update the **wvdial.conf** file as.

[B]
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = #777
Username = internet
Password = internet
[/B]

After this save file and try to connect to internet by typing **wvdial ** and press enter on terminal.

fallowing text was printed in side terminal.

xyz@ubuntu:~$ wvdial


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
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT#777
--> Waiting for carrier.

Does any one have any idea about this.

Is this regular dialup? Make sure the phone line is connected and check your modem init string for problems. Try setting up connection with pppconfig. Also try running wvdialconf. This will autodetect settings, then stick them in /etc/wvdial.conf

Zach

---

### Post by halovivek on 2009-03-06
Try using this [one]("http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html")

---

### Post by mahendra.pardeshi on 2009-03-18
Thanks for reply.
It solve my problem using **gnome-ppp**.

---

