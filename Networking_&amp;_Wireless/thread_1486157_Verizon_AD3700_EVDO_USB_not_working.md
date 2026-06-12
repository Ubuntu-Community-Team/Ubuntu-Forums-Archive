---
title: "Verizon AD3700 EVDO USB not working"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by jbeck22 on 2010-05-17
I'm running ubuntu 10.04 with all the latest updates.  I have the Verizon AD3700 USB World Modem...seen here
[IMG]http://www.coolest-gadgets.com/wp-content/uploads/verizon-ad3700.jpg[/IMG]

I have tried modeswitch, wvdial, ppp and several other things on my own.
Here is the output from lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 19d2:fff2 ONDA Communication S.p.A. 
Bus 001 Device 002: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Here my machine "sees" the modem:
dmesg | grep -e "modem" -e "tty":
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 009: ID 19d2:fff2 ONDA Communication S.p.A. **
Bus 001 Device 002: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Can anyone help me out?  I never get Network Manager to notify me that there is a new connection available or indicate in any way that the modem is present.

Thanks for your help!

---

### Post by alexfish on 2010-05-17
hi

you have post the results of the lsusb command twice , I think

try the dmesg command again and post the results

Code:

dmesg | grep -e "modem" -e "tty"

thanks in advance

alexfish

---

### Post by jbeck22 on 2010-05-17
That's what I get for not checking my copy/paste...here is the output of dmesg...

dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[   14.248051] USB Serial support registered for Qualcomm USB modem
[   14.249410] qcserial 1-3:1.0: Qualcomm USB modem converter detected
[   14.249858] usb 1-3: Qualcomm USB modem converter now attached to ttyUSB0

---

### Post by alexfish on 2010-05-17
hi

not quite what I expected

looks like a ZTE device but can't find it listed in the kernel or in the usb modeswitch data

although looking through the results the modem is recognised , but only on one port is registered

[ 14.248051] USB Serial support registered for Qualcomm USB modem
[  14.249410] qcserial 1-3:1.0: Qualcomm USB modem converter detected
[  14.249858] [COLOR=Blue]usb 1-3: Qualcomm USB modem converter now attached to ttyUSB0[/COLOR]

have you tried wvdial to use  Modem = /dev/ttyUSB0

also have you use this modem in windows

---

### Post by jbeck22 on 2010-05-17
The modem works great in Windows 7 (my other OS of choice).

here is my output from wvdial /dev/ttyUSB0:
wvdial /dev/ttyUSB0
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer /dev/ttyUSB0] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
~
[03]    [1c]_~~
[17]    LF~~
[03]    [1c]_~~
[17]    LF~~
[17]    LF~~
[03]    [1c]_~~
[03]    [1c]_~~
[03]    [1c]_~~
[17]    LF~~
[03]    [1c]_~
this just repeats.

I tried to connect to any webpage, google, etc, but nothing will connect.

---

### Post by alexfish on 2010-05-17
hi

you need to configure wvdial ; try the below from the terminal

Code:

sudo gedit /etc/wvdial.conf

then add these lines 


 [Dialer verizon]

Modem = /dev/ttyUSB0
Baud = 480000
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777

Username = [email]8885551212@vzw3g.com[/email]
# Username replace with your device's actual area code and phone number

Password = vzw

ISDN = 0 

save the file and exit

to test 

code:

sudo wvdial verizon


the above seem to be the standard dialling codes for verizon , but can't say if this will work

---

### Post by jbeck22 on 2010-05-18
still not working:

gedit /etc/wvdial.conf <--made suggested changes

root@jbeck-laptop:~# wvdial verizon
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
root@jbeck-laptop:~# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 19d2:fff2 ONDA Communication S.p.A. 
Bus 001 Device 003: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@jbeck-laptop:~# dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[    9.016885] USB Serial support registered for Qualcomm USB modem
[    9.026038] qcserial 1-3:1.0: Qualcomm USB modem converter detected
[    9.026674] usb 1-3: Qualcomm USB modem converter now attached to ttyUSB0


Here is my wvdial.conf file:
[Dialer verizon]
Modem = /dev/ttyUSB0
Baud = 480000
Init1 = ATZ
Init2 =ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = #777
Username = [email]xxxxxxxxxx@vzw3g.com[/email]
Password = vzw
ISDN = 0

---

### Post by alexfish on 2010-05-18
Can tell me what this is

Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth  Dongle (HCI mode)

---

### Post by jbeck22 on 2010-05-18
That is ny usb bluetooth dongle.
Should I remove it?

---

### Post by alexfish on 2010-05-18
yes it could be occupying the port wvdial is trying to use

but before you remove it . from the terminal enter this code and post the results

Code:

dmesg | grep -e "modem" -e "tty"

regards

alexfish

---

### Post by jbeck22 on 2010-05-18
with bluetooth USB dongle in:

**lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**dmesg | grep -e "modem" -e "tty"**
[    0.000000] console [tty0] enabled
[    9.016885] USB Serial support registered for Qualcomm USB modem
[    9.026038] qcserial 1-3:1.0: Qualcomm USB modem converter detected
[    9.026674] usb 1-3: Qualcomm USB modem converter now attached to ttyUSB0
[  464.411616] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0


with bluetooth USB dongle removed:

**lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b084 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**dmesg | grep -e "modem" -e "tty"**
[    0.000000] console [tty0] enabled
[    9.016885] USB Serial support registered for Qualcomm USB modem
[    9.026038] qcserial 1-3:1.0: Qualcomm USB modem converter detected
[    9.026674] usb 1-3: Qualcomm USB modem converter now attached to ttyUSB0
[  464.411616] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0

---

### Post by alexfish on 2010-05-18
don't know what to say

what happened to the verizon modem, did you unplug this as well

also can you tell me what is this

Bus 001 Device 003: ID 04f2:b084 Chicony Electronics Co., Ltd

---

### Post by jbeck22 on 2010-05-18
In order to make sure that I have provided the correct info let me summarize:
I'm assuming that the modem is this line: **Bus 001 Device 007: ID 19d2:fff2 ONDA Communication S.p.A.**
I'm not sure what **Bus 001 Device 003: ID 04f2:b084 Chicony Electronics Co., Ltd** could be unless it is the built-in webcam maybe?


_WITH modem and bluetooth connected:_
**lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 19d2:fff2 ONDA Communication S.p.A.
Bus 001 Device 003: ID 04f2:b084 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**grep -e "modem" -e "tty"**
[    0.000000] console [tty0] enabled
[    9.016885] USB Serial support registered for Qualcomm USB modem
[    9.026038] qcserial 1-3:1.0: Qualcomm USB modem converter detected
[    9.026674] usb 1-3: Qualcomm USB modem converter now attached to ttyUSB0
[  464.411616] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9110.407459] qcserial 1-1:1.0: Qualcomm USB modem converter detected
[ 9110.407737] usb 1-1: Qualcomm USB modem converter now attached to ttyUSB0
[ 9248.294251] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9252.460679] qcserial 1-4:1.0: Qualcomm USB modem converter detected
[ 9252.461178] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB0
[ 9339.215310] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9395.782955] qcserial 1-4:1.0: Qualcomm USB modem converter detected
[ 9395.783862] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB0


_With ONLY Bluetooth connected_:
**lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b084 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**dmesg | grep -e "modem" -e "tty"**
[    0.000000] console [tty0] enabled
[    9.016885] USB Serial support registered for Qualcomm USB modem
[    9.026038] qcserial 1-3:1.0: Qualcomm USB modem converter detected
[    9.026674] usb 1-3: Qualcomm USB modem converter now attached to ttyUSB0
[  464.411616] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9110.407459] qcserial 1-1:1.0: Qualcomm USB modem converter detected
[ 9110.407737] usb 1-1: Qualcomm USB modem converter now attached to ttyUSB0
[ 9248.294251] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9252.460679] qcserial 1-4:1.0: Qualcomm USB modem converter detected
[ 9252.461178] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB0
[ 9339.215310] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9395.782955] qcserial 1-4:1.0: Qualcomm USB modem converter detected
[ 9395.783862] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB0
[ 9482.798012] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0


_With ONLY the modem connected_:
**lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 19d2:fff2 ONDA Communication S.p.A.
Bus 001 Device 003: ID 04f2:b084 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**dmesg | grep -e "modem" -e "tty"**
[    0.000000] console [tty0] enabled
[    9.016885] USB Serial support registered for Qualcomm USB modem
[    9.026038] qcserial 1-3:1.0: Qualcomm USB modem converter detected
[    9.026674] usb 1-3: Qualcomm USB modem converter now attached to ttyUSB0
[  464.411616] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9110.407459] qcserial 1-1:1.0: Qualcomm USB modem converter detected
[ 9110.407737] usb 1-1: Qualcomm USB modem converter now attached to ttyUSB0
[ 9248.294251] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9252.460679] qcserial 1-4:1.0: Qualcomm USB modem converter detected
[ 9252.461178] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB0
[ 9339.215310] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9395.782955] qcserial 1-4:1.0: Qualcomm USB modem converter detected
[ 9395.783862] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB0
[ 9482.798012] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[ 9518.064218] qcserial 1-4:1.0: Qualcomm USB modem converter detected
[ 9518.064660] usb 1-4: Qualcomm USB modem converter now attached to ttyUSB0


Thanks for all the help btw!

---

### Post by alexfish on 2010-05-18
hi


trying to think why the same driver is coming up!

now can you try wvdial ,see what happens

also can you describe your system , also does it have a built in modem

---

### Post by jbeck22 on 2010-05-18
> **alexfish said:**
> hi


trying to think why the same driver is coming up!

now can you try wvdial ,see what happens

also can you describe your system , also does it have a built in modem

I'm back to this when i try wvdial verizon...
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
~
[03] [1c]_~~
[17] LF~~
[03] [1c]_~~
[17] LF~~
[17] LF~~
[03] [1c]_~~
[03] [1c]_~~
[03] [1c]_~~
[17] LF~~
[03] [1c]_~
this just repeats.



my system is the Acer Aspire D250 Netbook.  there is no dial up modem, only wireless, ethernet and 3 usb ports.

---

### Post by alexfish on 2010-05-18
thought that would be the outcome

most zte device will configure in ubuntu , not in this case ,

you could try talking to verizon , explain that your having problems with the device,

and would like to try the serial terminal in windows, Don't tell them your using Linux , and that you need to know what port to use and the at commands to get it to work,

will let you know if I find further info

added ; was your comp one of these or something similar where you had to down load the drivers

[http://drivers.softpedia.com/get/MODEM/Qualcomm/Acer-Aspire-One-D250-Netbook-QUALCOMM-Gobi1000-3G-Module-Driver-1027-for-Win7.shtml](http://drivers.softpedia.com/get/MODEM/Qualcomm/Acer-Aspire-One-D250-Netbook-QUALCOMM-Gobi1000-3G-Module-Driver-1027-for-Win7.shtml)


bye for now

alexfish

---

### Post by pdc on 2010-05-19
> *I'm back to this when i try wvdial verizon*......

you are typing 

> sudo wvdial

aren't you?

alex is very knowledgable on these things and is guiding you: I looked at older Verizon EVDO advice setups and this one

[http://www.aselabs.com/articles.php?id=224](http://www.aselabs.com/articles.php?id=224)

went though what you did with wvdial; I wonder though about trying pppconfig as a change if the above is no good; the above guides you through

---

