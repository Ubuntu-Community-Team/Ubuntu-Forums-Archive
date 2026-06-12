---
title: "Problem with dial up connection"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by nandipinto on 2006-01-16
Hi All,

I got the following error when trying to initiate dial-up connection using my Nokia 6235 CDMA phone as (USB) modem.

--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT +CRM = 1
AT +CRM = 1
OK
--> Sending: AT+cso=33
AT+cso=33
OK
--> Modem initialized.
--> Idle Seconds = 300, disabling automatic reconnect.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
~[7f]}#@!}!}!} }9}!}$}!t}"}&} } } } }#}%B#}%}%}&[0c]n` 8#~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jan 16 15:18:53 2006
--> pid of pppd: 9101
--> Disconnecting at Mon Jan 16 15:18:54 2006
--> The PPP daemon has died: Fatal pppd error (exit code = 1)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.



my wvdial.conf:

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 115200
Init1 = ATZ
Init2 = AT +CRM = 1
Init3 = AT+cso=33
FlowControl = CRTSCTS
Area Code =
Phone = #777
Username = test
Password = test
Ask Password = 0
Dial Command = ATDT
Stupid Mode = 1
Compuserve = 0
Force Address =
Idle Seconds = 300
DialMessage1 =
DialMessage2 =
ISDN = 0
Auto DNS = 1


Could anyone tell me why I keep getting this error?


Best regards,


nandipinto

---

### Post by gray380 on 2006-09-22
Hi,

try change the Baud to 460800

brg,
Serhiy.

---

