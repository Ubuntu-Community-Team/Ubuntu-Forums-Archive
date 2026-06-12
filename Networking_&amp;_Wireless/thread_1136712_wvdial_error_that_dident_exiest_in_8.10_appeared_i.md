---
title: "wvdial error that dident exiest in 8.10 appeared in 9.04"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by jarrah-95 on 2009-04-25
my diller is 
[Dialer hsdpa]

Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
and it comes up with the error
jarrah@jarrah-laptop:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ  Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATZ  Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Manufacturer: huawei
Model: E220
Revision: 11.117.03.00.00
IMEI: 358193012082914
+GCAP: +CGSM,+DS,+ES
COMMAND NOT SUPPORT
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ  Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATZ  Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Manufacturer: huawei
Model: E220
Revision: 11.117.03.00.00
IMEI: 358193012082914
+GCAP: +CGSM,+DS,+ES
COMMAND NOT SUPPORT
--> Modem not responding.

i dont know if it matters but im using a wireless 3g modem

---

### Post by ModelM on 2009-04-25
This line:
> **jarrah-95 said:**
> 
Init2 = ATZ Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0


should be two lines:

Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

---

### Post by jarrah-95 on 2009-04-25
ive chainged those lines and when i run it it said to put a username and password and number in so i did and this is what come up
jarrah@jarrah-laptop:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Waiting for prompt.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Pipe failed: Too many file open

---

### Post by GeorgeVita on 2009-04-25
Hi,

Add a line to your /etc/wvdial.conf file:

**Stupid Mode = Yes**

Run wvdial as superuser: **sudo wvdial hsdpa**

Post again ALL file /etc/wvdial.conf (after edits) and any other error message.

Also do you know the APN for your provider?
Have you tried Network Manager instead of wvdial?

Regards,
George

---

### Post by jarrah-95 on 2009-04-25
i dont know the apn and the network maneger dosent work [http://ubuntuforums.org/showthread.php?t=1135073](http://ubuntuforums.org/showthread.php?t=1135073)
but ill try the stupid mode but i dont think that will work as that comes into effect after the connection and this problem is eather connecting or pre connection
thanks

---

### Post by jarrah-95 on 2009-04-25
thanks it worked perfictley all i had to do is use sudo to connect (must be new in 9.04 that pppd is owned by  root)
thanks

---

### Post by alfielee on 2009-05-11
> **jarrah-95 said:**
> i dont know the apn and the network maneger dosent work [http://ubuntuforums.org/showthread.php?t=1135073](http://ubuntuforums.org/showthread.php?t=1135073)
but ill try the stupid mode but i dont think that will work as that comes into effect after the connection and this problem is eather connecting or pre connection
thanks
If using prepaid with OPTUS then make username & password blank & the APN is preconnect

---

### Post by MarkBWoods on 2009-06-09
I have the same problem with my dialup. The modem works perfectly with a live Puppy Linux 4.0 cd. With my Ubuntu 9.04 it dials, I get the static, then the silence, and the same error this user posted. I tried adding the line in my WVDial.conf file but it didn't fix it. The post did not say  where in the file to add the line, but I tried several different ways. I am very much a newbie to Linux so I apologize for my lack of knowledge. When I run WVDial as a super user as mentioned, I get an error that there is no phone number, username, or password specified. When I used the GnomePPP, regardless of the settings, I get the same problem. Have I missed something? Or is there anything else I can try?  Thank you!!!

---

### Post by GeorgeVita on 2009-06-09
Hi **MarkBWoods**,
please supply some info about your modem (manufacturer/model), country/provider and if recognized by the system (Network Manager setup wizard started?).

You can check again: boot without the modem, right click Network Manager icon (beside speaker icon) and then Edit Connections, Mobile Broadband, click and delete if any. Close, attach the modem and wait for the wizard to start (max 1 minute).

If not started, open a terminal window (Applications, Accessories, Terminal) and type: **dmesg** and press <enter>
copy the last lines regarding modem, usbserial, option driver, ttyUSBx or GSM and post them here.

Also from terminal: **lsusb** and press <enter>
find the line that shows your modem especially the hex numbers (vendorID : productID)

If you have already tried with **wvdial** you should have a file **/etc/wvdial.conf** (keep characters as they are because the system uses case sensitive syntax **A is not a**).
Post here this file.

Regards,
George

---

