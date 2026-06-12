---
title: "ppp daemon keeps dying"
date: 2005-03-22
forum: Networking &amp; Wireless
---

### Post by goblin on 2005-03-22
Hi, I am trying to connect using Wvdial but I keep getting the ppp daemon keeps dying with the following problem....

root@ubuntu:/home/mike # wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Modem initialized.
--> Sending: ATDT087308880
--> Waiting for carrier.
ATDT087308880
CONNECT 460800
--> Carrier detected.  Waiting for prompt.

login:
--> Looks like a login prompt.
--> Sending: mtgedye
mtgedye
Password:
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Wed Mar 23 09:27:53 2005
--> pid of pppd: 4604
--> Using interface ppp0
--> pppd: ISDN
--> pppd: ISDN
--> pppd: ISDN
--> pppd: ISDN
--> Disconnecting at Wed Mar 23 09:28:28 2005
--> The PPP daemon has died: PPP negotiation failed (exit code = 10)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 10)

However I can often manage to connect via  computer>system configuration> networking which as far as I can tell uses the same ppp0 that Wvdial uses though can be unstable and dropout several times before settling down for serious surfing.

Why does the pppd above list ISDN when I am using plain old dial up and where/how can I change this, and again isn't this using the same ppp0 as the other successful way?

Also pon ppp0 has the same outcome as Wvdial, and ModemLights just does nothing. grrrrrrr

Cheers Goblin

---

