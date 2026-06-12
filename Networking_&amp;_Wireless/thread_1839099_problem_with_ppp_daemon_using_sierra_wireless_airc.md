---
title: "problem with ppp daemon using sierra wireless aircard 312U"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by aus293 on 2011-09-04
I am in rural Australia trying to connect to the internet with a sierra wireless aircard 312U. Telstra is the ISP, ubuntu 10.10 64 bit OS.  Have tried many suggestions from webpages before coming here. Have tried connecting with wvdial.  Had no joy with the network manager, am almost connected using wvdial.  However, I cannot get online.  Here is the terminal output:

steven01@steven01:~$ sudo wvdial
[sudo] password for steven01: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 21000000
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Mon Sep  5 12:49:20 2011
--> Pid of pppd: 1736
--> Using interface ppp0
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> pppd: &#65533;[7f]
--> Disconnecting at Mon Sep  5 12:49:22 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.


Have looked at man pages and messages file.  However, I'm stuck here.  Would love to become a better informed Ubuntu advocate. Can anyone help me. Thanks in advance.

---

### Post by whatthefunk on 2011-09-04
Try pppoeconf in the terminal.

```
sudo pppoeconf
```

Its pretty straight forward.

---

