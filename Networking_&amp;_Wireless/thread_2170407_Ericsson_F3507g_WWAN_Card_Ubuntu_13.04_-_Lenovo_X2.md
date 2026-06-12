---
title: "Ericsson F3507g WWAN Card /Ubuntu 13.04 - Lenovo X200 /GPS problem"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by info-princeofpalms on 2013-08-26
My modem is returning a **CME Error: 263**. I realise this stands for, "Invalid block", but that's as much as I know. This is the first time I've tried using the WWAN card. Am I doing something wrong?

Here's my etc/wvdial.conf:

```
[Dialer Defaults]New PPPD = yes
Stupid Mode = 1
Modem Type = USB Modem


[Dialer on]
Modem = /dev/ttyACM0
Init1 = AT+CFUN=1
 
[Dialer off]
Modem = /dev/ttyACM0
Init1 = AT+CFUN=4  
 
[Dialer gps]
Modem = /dev/ttyACM1
Init1 = AT*E2GPSCTL=1,2,1
Init2 = AT*E2GPSNPD
```

I'm only interested in the gps functionality at present. Below is the error:

```
root@Lenovo-ThinkPad-X200:~# wvdial on--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: AT+CFUN=1
AT+CFUN=1
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
root@Lenovo-ThinkPad-X200:~# wvdial gps
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: AT*E2GPSCTL=1,2,1
+CME ERROR: 263
--> Bad init string.
--> Initializing modem.
--> Sending: AT*E2GPSCTL=1,2,1
+CME ERROR: 263
--> Bad init string.
--> Initializing modem.
--> Sending: AT*E2GPSCTL=1,2,1
+CME ERROR: 263
--> Bad init string.
root@Lenovo-ThinkPad-X200:~# 



```

I would greatly appreciate any help in resolving this. I've read every blog and Ubuntu forum thread on configuring the Ericsson F3507g WWAN Card, most of which don't appear to discuss gps connection problems. Thanks in advance!

---

