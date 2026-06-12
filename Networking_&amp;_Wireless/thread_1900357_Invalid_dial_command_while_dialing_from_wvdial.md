---
title: "Invalid dial command while dialing from wvdial"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by uniquerockrz on 2011-12-26
I have a Micromax 3G USB modem (model no. 352G) but when I try to dial up using wvdial, I get an error "Invalid Dial Command". I have usb_modeswitch installed and NetworkManager can detect my modem, but I can rarely connect through network-manager, so try to do with wvdial. My wvdial.conf file is as below:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1
Modem Type = Analog Modem
Check Def Route = 1
Phone = *99#
ISDN = 0
Password = abc
New PPPD = yes
Username = abc
Modem = /dev/ttyUSB1
Baud = 9600
Stupid Mode = 1

```

Here is the terminal output:

```

--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1
ATQ0 V1 E1 S0=0 &C1
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
ERROR
--> Invalid dial command.
--> Disconnecting at Mon Dec 26 15:22:13 2011

```

For dial command, I have tried to explicitly specify them as ATDT, ADT, but none of them seem to work.:confused:

Please note I can connect sucessfully with my phone using wvdial, something wrong with the dial command of the modem instaed. How do I get to know which one is for my modem?

---

