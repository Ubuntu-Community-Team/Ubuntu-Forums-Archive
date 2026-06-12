---
title: "Dial-up works for several minutes then hangs up"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by linuxguiri on 2006-01-10
Hi. I've scoured the forums looking for already existing solutions to this, but haven't found any. Hope someone has some ideas on this:

I can use gnome-ppp to connect to the internet, but I almost invariably lose the connection after several minutes especially when I'm using Firefox. It tends to stay connected when I'm using Synaptic or Terminal to download a package or upgrade ubuntu though.

Here's the log from gnome-ppp:

```
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT212-0250
--> Waiting for carrier.
ATM1L3DT212-0250
CONNECT 460800 
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Jan  9 21:48:55 2006
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> pid of pppd: 12047
--> Using interface ppp0
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> local  IP address 64.24.105.86
--> pppd: TZ
--> remote IP address 64.24.104.227
--> pppd: TZ
--> primary   DNS address 216.126.136.250
--> pppd: TZ
--> secondary DNS address 216.126.128.40
--> pppd: TZ
--> pppd: TZ
--> Connect time 8.4 minutes.
--> pppd: TZ
--> pppd: TZ
--> pppd: TZ
--> Disconnecting at Mon Jan  9 21:57:21 2006
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
```


I'd be very grateful for any ideas. It's very frustrating having to reconnect to the internet every 5 minutes and reloading webpages.

---

