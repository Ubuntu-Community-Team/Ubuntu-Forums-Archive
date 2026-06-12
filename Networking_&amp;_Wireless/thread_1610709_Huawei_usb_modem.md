---
title: "Huawei usb modem"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by tonymoloney on 2010-11-01
My daughter bought a Huawei usb modem so that she could get wireless internet on her Kubuntu system.
She had no success with this system so she has given it to me to see if I can get it to work on Ubuntu.

Following is the output of wvdial:

tony@tony-laptop:/etc$ wvdial
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
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
tony@tony-laptop:/etc$ 

If i put a username/password in wvdial.conf I get the folowing:


tony@tony-laptop:/etc$ wvdial
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
--> Sending: ATDT555a1
--> Waiting for carrier.
ATDT555a1
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT555a1
--> Waiting for carrier.
ATDT555a1
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT555a1
--> Waiting for carrier.
ATDT555a1
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Mon Nov  1 14:27:52 2010
tony@tony-laptop:/etc$ 


 until I abort the job.

555a1 is the number that huawei uses to connect to the net via Windoze and it works there.

Any ideas anyone.

In case you hadn't noticed, this is an Australian query. Her ISP is Westnet who use Optus as their carrier.

---

### Post by gradinaruvasile on 2010-11-01
Does it work via network-manager?

Also there is a tool named sakis3g that does not need any dependencies, it is quite good on detecting/auto-configuring 3g modems and connecting them.
You can get it here:

[http://www.sakis3g.org/](http://www.sakis3g.org/)

It is simple to use, just read the documentation.

---

### Post by halj32 on 2010-11-01
First what country are you in??
the number is usually *99#
then the network name
it's also best to just use network manager
click on network manager,
then in mobile broadband
( I use 3G  UK)
number  *99#
APN  3Connect  (whatever network you use)
thats it
also have a look here it might help
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Mobile%20Broadband%20cards](https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Mobile%20Broadband%20cards)

also you may need to install   usb-modeswitch

goodluck

---

