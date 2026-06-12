---
title: "Dial-up Issue Oneiric Gnome-ppp"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by Moturhead on 2012-04-28
Hi, 

I am a new ubuntu user and connect to the internet using wi-fi broadband on my notebook. But I need to setup a dial-up connection through my phone which can keep me online while I travel. 

I have tried connecting to dial-up using pppconfig, wvdial and gnome-ppp. I do not know whether they use the same files for connecting but I have only been able to connect using Gnome-ppp. But the connection is intermittent and disconnects every five seconds or so. The exit code is 16 which I checked in man and got to know that the modem hangs itself up. 

I am connecting my phone to ubuntu as a usb modem. And as I am new I might have skipped a step or two.

Please suggest a solution or an alternative to this. I have put down the Gnome-ppp log. 

Thanks.



--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99***1#
--> Waiting for carrier.
ATM1L3DT*99***1#
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&}*urW}'}"}(}"mX~
--> PPP negotiation detected.
--> Starting pppd at Sat Apr 28 21:55:55 2012
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 2459
--> Using interface ppp0
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> Disconnecting at Sat Apr 28 21:56:01 2012
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99***1#
--> Waiting for carrier.
ATM1L3DT*99***1#
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!Q} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&}*u69}'}"}(}"#W~
--> PPP negotiation detected.
--> Starting pppd at Sat Apr 28 21:56:07 2012
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 2470
--> Using interface ppp0
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> Disconnecting at Sat Apr 28 21:56:09 2012
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99***1#
--> Waiting for carrier.
ATM1L3DT*99***1#
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!@} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&}*uvM}'}"}(}"p}$~
--> PPP negotiation detected.
--> Starting pppd at Sat Apr 28 21:56:20 2012
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 2481
--> Using interface ppp0
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> pppd: xu!
--> Disconnecting at Sat Apr 28 21:56:25 2012
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 20 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.

---

