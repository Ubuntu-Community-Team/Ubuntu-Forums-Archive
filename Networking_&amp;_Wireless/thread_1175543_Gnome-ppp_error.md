---
title: "Gnome-ppp error"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by teking66 on 2009-06-01
OK here is my issue.

As root I can use gnome-ppp with out any problems.

When logged in as my user I get this problem, this is from the Gnome-ppp log;

--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT7625441
--> Waiting for carrier.
ATM1L3DT7625441
CONNECT 460800 
--> Carrier detected.  Waiting for prompt.
** Ascend TNT Terminal Server **
Login: 
--> Looks like a login prompt.
--> Sending: [EMAIL="teking66@localnet.com"]teking66@localnet.com[/EMAIL]
[EMAIL="teking66@localnet.com"]teking66@localnet.com[/EMAIL]
Password: 
--> Looks like a password prompt.
--> Sending: (password)
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.

---

### Post by strife242 on 2009-06-01
I'd guess that your user account does not have enough permissions.
as user, try using "sudo" in front of your command.

If this helps then, depending on how things is setup, you can give the user permissions to use the application.

---

