---
title: "Mobile Broadband ZTE MF192 Stick under Linux"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by dawntreader201 on 2011-11-08
I want to use Mobile Broadband ZTE MF192 stick under Linux. I'v got it to Plug & Play with Zoom 3G Wireless-N Router so it must be possible in Linux. Any ideas.

---

### Post by mick222 on 2011-11-08
If you can find your carrier in the mobile broadband section of the Edit connections dialog it should connect .I,ve used a few phones on both three and vodaphone uk  and setup was much easier than on Windows.

---

### Post by dawntreader201 on 2011-11-08
Linux does not see this stick as a modem but as a CDROM drive

---

### Post by mick222 on 2011-11-08
Seen a similar problem with a Huawei dongle try installing usb_modeswitch from synaptic then reconect.

---

### Post by dawntreader201 on 2011-11-08
USB modeswitch comes as standard in Uduntu 11.10 still dosn't work

---

### Post by mick222 on 2011-11-08
Check this page out might help [http://sajjad.in/2011/10/getting-an-huawei-ec159-usb-modem-working-on-ubuntu-11-04/](http://sajjad.in/2011/10/getting-an-huawei-ec159-usb-modem-working-on-ubuntu-11-04/)

---

### Post by dawntreader201 on 2011-11-09
I have tried usb_modeswitch the -H switch is for huawei but I can't find one for ZTE tried with no manufacturer and got the result below, any ideas :-

~$ usb_modeswitch -v 19d2 -p 1514

Looking for default devices ...
 Found devices in default mode, class or configuration (1)
Accessing device 000 on bus 001 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1.
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

---

### Post by pdc on 2011-11-09
please copy and paste 

> dmesg | grep tty

into a terminal, and copy and paste results back here;

the | if you must type it is SHIFT-\

if you also type 

> lsusband tell us what you get

.........as a quick start fix for you to try.....

....if the ZTE gives you an icon on your desktop;

right-click and select "EJECT"

that may well flips its ID, so it is now seen as a modem ..

...and your system might prompt you to configure it .......

---

### Post by dawntreader201 on 2011-11-10
thank you

I tried 

thank you
I tried ejecting the ZTE MF192 it worked to a certain extent the light flashed blue but didn't log on to network.

result of dmesg | grep tty

mick-ubuntu@mickubuntu-Compaq-Mini-110c-1100:~$ dmesg | grep tty

mick-ubuntu@mickubuntu-Compaq-Mini-110c-1100:~$  dmesg | grep tty
[    0.000000] console [tty0] enabled
[16246.337038] cdc_acm 1-1:1.1: ttyACM0: USB ACM device
[16246.339105] cdc_acm 1-1:1.3: ttyACM1: USB ACM device
[16246.340266] cdc_acm 1-1:1.6: ttyACM2: USB ACM device
[17280.004508] cdc_acm 1-1:1.1: ttyACM0: USB ACM device
[17280.006941] cdc_acm 1-1:1.3: ttyACM1: USB ACM device
[17280.012539] cdc_acm 1-1:1.6: ttyACM2: USB ACM device
[21072.940304] cdc_acm 1-1:1.1: ttyACM0: USB ACM device
[21072.942725] cdc_acm 1-1:1.3: ttyACM1: USB ACM device
[21072.948655] cdc_acm 1-1:1.6: ttyACM2: USB ACM device
mick-ubuntu@mickubuntu-Compaq-Mini-110c-1100:~$ 



result of lsusb

mick-ubuntu@mickubuntu-Compaq-Mini-110c-1100:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 10f1:1a13 Importek 
Bus 005 Device 002: ID 03f0:2a1d Hewlett-Packard 
Bus 001 Device 023: ID 19d2:1514 ONDA Communication S.p.A. 
mick-ubuntu@mickubuntu-Compaq-Mini-110c-1100:~$

---

### Post by barefootpenguin on 2012-02-04
Did you ever figure this out? I'm trying to install the same device and am getting stuck at the same place as you did.

---

~$ usb_modeswitch -v 19d2 -p 1514

Looking for default devices ...
Found devices in default mode, class or configuration (1)
Accessing device 000 on bus 001 ...
Getting the current device configuration ...
Error getting the current configuration (error -1). Assuming configuration 1....

...etc.

---

Cheers!

---

