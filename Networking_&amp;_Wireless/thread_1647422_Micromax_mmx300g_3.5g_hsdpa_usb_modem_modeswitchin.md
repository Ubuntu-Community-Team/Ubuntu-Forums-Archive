---
title: "Micromax mmx300g 3.5g hsdpa usb modem modeswitching problem"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by im.saravanan on 2010-12-17
Hi friends
i m using ubuntu 10.04. I have  MICROMAX MMX300G 3.5G HSDPA USB MODEM. i have installed usbmodeswitching software from ubuntu software center. 

The good thing is the the product id is switched from 05c6:f000 to 05c6:9000 the moment its plugged in. But sudo wvdialconf wvdial.conf does not find any modem. The result of "usb-devices" command before and after modeswitching is as follows:-

usb-devices output _**BEFORE**_ switching

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#= 16 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  [COLOR=Magenta]Vendor=05c6 ProdID=f000[/COLOR] Rev=00.00
S:  Manufacturer=Micromax
S:  Product=Micromax
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

_**MANUAL MODESWITCHING**_

saravanan@saravanan-desktop:/etc$ sudo usb_modeswitch
[sudo] password for saravanan: 

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 016 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: Micromax
   Model String: HSDPA Modem     
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Micromax
     Product: Micromax
  Serial No.: 1234567890ABCDEF
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent

Checking for mode switch (max. 20 times, once per second) ...
 Waiting for original device to vanish ...
 Original device can't be accessed anymore. Good.
 Searching for target devices ...
[COLOR=Red]Error: could not get description string "product"[/COLOR]  <-----IS THIS OK?
 Found correct target device

Mode switch succeeded. Bye.

usb-devices --output     _**AFTER**_ switching

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#= 17 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:[COLOR=Magenta]  Vendor=05c6 ProdID=9000[/COLOR] Rev=00.00
S:  Manufacturer=Micromax
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

IS IT BECAUSE THE MODEM HAS NO DRIVER (NONE)CAN ANYONE HELP ME?

---

### Post by im.saravanan on 2011-08-16
Hi see this link. the problem is solved in ubuntu 11.04.

[http://ubuntuforums.org/showthread.php?t=1824882&highlight=mmx300g](http://ubuntuforums.org/showthread.php?t=1824882&highlight=mmx300g)

---

