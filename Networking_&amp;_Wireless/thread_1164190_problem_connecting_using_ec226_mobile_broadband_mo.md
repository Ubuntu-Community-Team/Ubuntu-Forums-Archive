---
title: "problem connecting using ec226 mobile broadband modem"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by joeizang on 2009-05-19
Hi guys,

I have some wired thing going on with my office. I just setup a server on ubuntu server 8.10 and I am to connect it to the internet using the ec226 gsm modem. The OS sees the modem and assigns tty/USB0 to the modem but if I connect it gives me an exit error code of 2. Went through the man pages and it just says this the result of 2 or more mutually exclusive options being used. Now are these options in the wvdial.conf file and which would it most likely be? Here is the error it gives when dialing.





sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX0
ATX0
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATM0
ATM0
OK
--> Modem initialized.
--> Sending: ATM1L3DT#777
--> Waiting for carrier.
ATM1L3DT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue May 19 12:46:05 2009
--> Pid of pppd: 14682
--> Disconnecting at Tue May 19 12:46:05 2009
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

---

### Post by GeorgeVita on 2009-05-21
Hi **joeizang**, please try to connect without the ethernet connected and with the wireless (if any) disabled.
If still having the problem supply more data:

- Country, Provider, type of data account (if there are more than one)
- /etc/wvdial.conf


Regards,
George

---

