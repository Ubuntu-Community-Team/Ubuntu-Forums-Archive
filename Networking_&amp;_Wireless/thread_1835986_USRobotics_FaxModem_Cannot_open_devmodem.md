---
title: "USRobotics FaxModem Cannot open /dev/modem"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by 7seastraveller on 2011-08-30
I need to install USRobotics 56K Serial Controller FaxModem (5686G) to my Ubuntu 10.04 Lucid to connect to other modems at remote sites to get data.
 
So far I had the following problems, please help!
 
Installed gnome-network-admin, from System->Administration->Network, No Connection tab, I only got "General", "DNS" and "Hosts".
 
Installed wvdial and dependencies, wvdial returns: Cannot open /dev/modem: No such file or directory.
 
If I use minicom, then everything is ok, I can connect and talk to the modem. So the modem is connected and working. But why wvdial not working?
 
By the way, USRobotics modem does not have Linux driver. I did download and installed the latest Linux Firmware for the modem.
 
Need help. Thanks!

---

### Post by 7seastraveller on 2011-08-30
Update to my problem:

Installed gnome-ppp, set device to /dev/ttyS0 instead of /dev/modem, as the modem is connected to serial port.

Now I got: (screen print) 
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATX3
0
--> Sending: ATQ0
0
--> Re-Sending: ATX3
0
--> Modem not responding.

If I run minicom, I got (screen print)
ATX3
OK
ATQ0
OK

I need to control the modem from my C program, it is the same as wvdial, modem not responding. 
Any ideas? 
Thanks in advance!

---

### Post by 7seastraveller on 2011-08-30
SOLVED: BUG IN WVDIAL

It turned out to be a bug in wvdial:

wvdial only interprets Verbal result codes when initializing modem, if it gets a Numeric result code, wvdial considers it as "Modem Not Responding" then stops. If it gets a Verbal result "OK", wvdial then sends request to use "Verbal result" and continues.

wvdial has a logic bug, it should request "Verbal result" first before measure the result in Verbal form.

Obviously minicom does not have this logic bug and that is why minicom works.

---

