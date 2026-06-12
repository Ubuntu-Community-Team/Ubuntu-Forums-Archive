---
title: "configuring micromax 300 g"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by JayJawahar on 2010-08-07
Guys,

I am new to linux and I tried to connect my bsnl 3g usb modem  in linux. I surfed thro' forums and followed some procedures as listed

First I ejected my usb storage using eject /dev/sr1 command, it said ejected successfully 

then I used usb_modeswitch (lsusb report confirms mode switch) 

then I used mode probe command it says no error

when I dialed using wvdial it says modem intialised....... but carrier died and disconnected

all my lsusb, dmesg reports before and after usb mode switch; usb_mode switch and wvdial programs all are attached in the error.zip file

modem make:micromax,  model:MMX 300g, vendor id=1c9e, product id=9605

Can any one help me to configure it correctly????

---

### Post by pdc on 2010-08-07
your dmesg shows

> usb 2-1.2: generic converter now attached to ttyUSB0
[  371.892492] usbserial_generic 2-1.2:1.1: generic converter detected
[  371.892731] usb 2-1.2: generic converter now attached to ttyUSB1
[  371.892922] usbserial_generic 2-1.2:1.2: generic converter detected
[  371.894640] usb 2-1.2: generic converter now attached to ttyUSB2
[  371.894673] usbserial_generic 2-1.2:1.3: generic converter detected
[  371.895693] usb 2-1.2: generic converter now attached to ttyUSB3

so the device is seen as a modem;

1) perhaps you post your wvdial script 

2) and check your apn settings are correct: I see lots of those  "*oops, I had the wrong apn settings*" updates 

3) I note you post

> model:MMX 300g, vendor id=1c9e, product id=9605 

whereas the usb_modeswitch data would suggest

> **960****3** 

where did you get 9605 from?

Overall, I am surprised that you cannot configure this device from network manager, as you seem to have installed usb_modeswitch

---

### Post by JayJawahar on 2010-08-10
Thank you, pdc

Here are my answers

*1) perhaps you post your wvdial script *

Here is my wvdial (included in error.zip). I used two different configs  from the websites

[Dialer bsnl]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","bsnlnet"
Dial Command = ATDT
Carrier Check = no
Modem = /dev/ttyUSB1
Baud = 7200000
New PPPD = yes
Stupid Mode = 1
ISDN = 0
Username = " "
Password = " "
Phone = *99***1#    <------ or *99# 

[Dialer bsnlnet]
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Baud = 460800
Username = " "
Password = " "
Modem = /dev/ttyUSB1
Init1 = ATZ
Init2 = at+cgdcont=1,"ip","bsnlnet"
Stupid Mode = 1

but both are in vain, results also included in error.zip

Iam also having doubt in wvdial only but I dont know about these scripts I simply used configurations available in net.

*2) and check your apn settings are correct: I see lots of those  "oops,  I had the wrong apn settings" updates *

I am using same apn in my windows 7 it is working

In windows 

profile name : 3G
username = null
password = null
authentication = none
dial number = *99#
apn = bsnlnet


*3) I note you post, whereas the usb_modeswitch data would suggest, did you get 9605 from?*

When I checked in windows 7, by looking into properties-->diagnostics it shows both ids(vendor & product). Intially i used 9603 as given in websites but nothing happend, then when i connected  in windows i found it is 9605.

Note: I used latest usb_modeswitch conf files, in this I just added my product id in target class id, initially it had 9600,9603 & 9000 only.but it get switched correctly.

*Overall, I am surprised that you cannot configure this device from  network manager, as you seem to have installed usb_modeswitch*

some times network manager starts checking but get disconnected at last

I created a profile in network manager as modem -- usbmodem
chosen custom settings and apn = bsnlnet, dial number=*99#
and in authentication I deselected all and try to connected, but nothing happend.

---

