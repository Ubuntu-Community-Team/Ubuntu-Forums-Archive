---
title: "Verizon Wireless UM150 USB Modem"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by greglough on 2009-10-12
Just puchased a Dell Mini 10 with Ubuntu 8.04.
 
How can I get my VZ 150 air card to work with this machine?
 
I am very new to the Ubuntu world - please, please spoon feed.
 
Thanks

---

### Post by Nostalos on 2009-10-12
I can't speak for the 150 or 8.04 as I have a UM175 and started using it with 8.10.  Under which network manager can be configured for dialup via Network Manager.   Under both 8.10 and 9.04 network manager detects it as a CDMA Modem.

Under 8.04 I can't remember if it has CDMA Modem support or not.  But even if it does not you can still configure a PPP dialer such as KPPP or Gnome's variant.   You will need to determine the comport Ubuntu see's when you plug in the modem.  The "dmesg" command will help with that.   You will just need to provide the number to dial and login info.  The number to dial is #777  and I do not beleive a login id/password are required for VZW.   


One thing to note, is that if you have not connected with the modem before you will have to connect it to a windows box first for initial programming through the Verizon Software.

---

### Post by greglough on 2009-10-13
USB Modem has been recognized and rec'd IP address.

Still unable to connect to the internet - am I missing a step?

Shouldn't I be able to immediately run FireFox?

---

### Post by Nostalos on 2009-10-14
where are you seeing that from and how are you connecting?  network manager?  PPP Dialer?    Basically it works just like the old days of dialup.  No Net till you manually connect.

---

### Post by greglough on 2009-10-14
from the terminal I connect the USB modem using:

  	 	 	 	 	 	  greg@greg:~$ sudo wvdial
 [sudo] password for greg:  
 --> WvDial: Internet dialer version 1.60
 --> Cannot get information for serial port.
 --> Initializing modem.
 --> Sending: ATZ
 OK
 --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 OK
 --> Modem initialized.
 --> Sending: ATDT#777
 --> Waiting for carrier.
 ATDT#777
 CONNECT
 --> Carrier detected.  Waiting for prompt.
 --> Don't know what to do!  Starting pppd and hoping for the best.
 --> Starting pppd at Wed Oct 14 11:07:54 2009
 --> Pid of pppd: 6457
 --> Using interface ppp0
 --> pppd: &#1047;[06][08]&#65533;&#65533;[06][08]
 --> pppd: &#1047;[06][08]&#65533;&#65533;[06][08]
 --> pppd: &#1047;[06][08]&#65533;&#65533;[06][08]
 --> local  IP address 75.219.76.83
 --> pppd: &#1047;[06][08]&#65533;&#65533;[06][08]
 --> remote IP address 66.174.161.64
 --> pppd: &#1047;[06][08]&#65533;&#65533;[06][08]
 --> primary   DNS address 66.174.95.44
 --> pppd: &#1047;[06][08]&#65533;&#65533;[06][08]
 --> secondary DNS address 66.174.92.14
 --> pppd: &#1047;[06][08]&#65533;&#65533;[06][08]


After the above runs, I open FireFox and no connection?

---

### Post by Nostalos on 2009-10-14
ahh Gotcha.  Since you are not using network Manager gnome/firefox assumes you are still offline and won't connect. 

Solutions:

1.  Under the File Menu in Firefox I believe there is an option to "Work Offline"  to get Firefox Working.

2.  Uninstall Network Manager.  (not recommended)

3.  Upgrade to 8.10 or 9.04 so the connection will be tracked via network manager.

---

### Post by greglough on 2009-10-19
Thanks for the help, but "Work Offline" is not the answer.
I've seen the same problem described in other forums - but no solution posted.

---

