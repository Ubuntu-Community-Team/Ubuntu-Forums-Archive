---
title: "problem connecting to internet"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by gbmtoday on 2009-10-01
Hello everyBody
 
i have conexant hcf modem
I install the deb package for it
when I do " pon.wvdial" the modem starting to dialing and write this in terminal 
but it does not connect to internet succsesfully, and it dial again after few seconds
 
 
 
```

--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT9716007
--> Waiting for carrier.
ATDT9716007
CONNECT 460800 
--> Carrier detected.  Waiting for prompt.
********************************** WARNING ************************************
        Any use of system or trying to breach the security may be LOGGED
        or monitored without further notice, and that the Resulting Logs
        may be used as EVIDENCE in court.
*******************************************************************************
User Access Verification
Username: 
--> Looks like a login prompt.
--> Sending: csp4658562
csp4658562
Password: 
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed.
Username: 
--> Looks like a login prompt.
--> Sending: csp4658562
csp4658562
Password: 
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed.
Username: 
--> Looks like a login prompt.
--> Sending: csp4658562
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Oct  1 22:36:25 2009
--> Pid of pppd: 6653
--> Using interface ppp0
--> pppd: &#65533;&#65533;,[08][18]&#65533;,[08]
--> pppd: &#65533;&#65533;,[08][18]&#65533;,[08]
 

```
 
 
 
anybody now how to solve this problem and connect to internet ???!!!
  
plz help me :-(

---

### Post by GeorgeVita on 2009-10-06
Hi **gbmtoday**, I am not sure if I can help, so just an idea:

Usually the user/pass negotiation is done via ppp methods. When using wvdial, you should add the line "Stupid mode = Yes" into configuration file **/etc/wvdial.conf** (can be edited with: gksudo gedit /etc/wvdial.conf). I am not sure if 'pon.wvdial' uses the same configuration file.

Regards,
George

---

