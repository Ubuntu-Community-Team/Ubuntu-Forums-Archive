---
title: "Gnome PPP is connecting at a very low speed"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by ub07 on 2012-07-17
I connect to the internet through dial-up using Gnome PPP. Everything was fine until yesterday when Gnome PPP started connecting at a much lower speed, approximately 5 times lower than normal. It connects normally in Windows, and it connects normally on a different computer running X/Ubuntu with the same modem.

Gnome PPP registers the correct modem speed when I do a "detect modem" and the correct speed is listed in the wvdial.conf file.

For those who read my other thread, the computer with the problem is not the computer that I removed the network manager from. That was this computer that I am on now, and it is working fine.

I am at a loss to explain why Gnome PPP suddenly started connecting at a much lower speed when everything else is connecting at the proper speed. 

Any help would be appreciated.

---

### Post by ub07 on 2012-07-18
I was wrong about the connection speed. I am getting about 2.5 kb/s download where I was getting about 5.0 kb/s. It is still a factor of 2 which is a lot when you are using dial-up.

I'd like to add that I'm using a Zoom 3095 modem. Now it is connecting consistently at the lower speed, but the problem does not exist under Windows with the same modem. Could there be a problem with the initialization string?

Here is the Gnome PPP log where I x-ed out identifying information:

```
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DTxxx-xxx
--> Waiting for carrier.
ATM1L3DT483-4052
CONNECT 9600
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas37.2in1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: xxxxx@xxxxxxxx.com
xxxxx@xxxxx.com
Password: 
--> Looks like a password prompt.
--> Sending: (password)
LDAP authenticated against xxxxx@xxxxxxx.com
    Entering PPP Session.
    IP address is x.xxx.xxx.xxx
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Wed Jul 18 14:59:38 2012
--> Pid of pppd: 6089
--> Using interface ppp0
--> local  IP address x.xxx.xxx.xxx
--> remote IP address xxx.xxx.xx.xxx
--> primary   DNS address xx.xxx.173.4
--> secondary DNS address xx.xxx.164.76
```

---

### Post by ub07 on 2012-07-19
I'm going to mark this solved even though the solution is a bigger mystery than the problem. 

To solve this problem, you have to set the modem speed (in Gnome PPP and wvdial.conf) to a value that is less than the maximum speed of the modem. When you tell Gnome PPP to detect the modem, it will come back with a modem speed of 460800. If you set it to 400000, it will connect at a higher speed than if you leave it at 460800. I have no idea why this is true, but it solves the problem.

---

