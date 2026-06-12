---
title: "Nokia CS-19 Mobile broadband USB stick not supported by 10.10?"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by orwtech@gmail.com on 2011-01-13
:confused:
Hi

Have anybody succeded in using Nokia CS-19 Mobile broadband USB stick with ubuntu 10.10?

It is not reconized as a 3G adapter.

Nokia states that it was compatible with ubuntu 10.04 on their site:

[http://europe.nokia.com/find-products/accessories/all-accessories/home-and-office/imaging/nokia-internet-stick-cs-19/compatibility](http://europe.nokia.com/find-products/accessories/all-accessories/home-and-office/imaging/nokia-internet-stick-cs-19/compatibility)

Anyone know how I get this working 

Best regards 

Jesper

---

### Post by alexfish on 2011-01-13
Hi

check the device with this command from the terminal

Code:

usb-devices

locate the lines which indicate the device

if it only shows a cd or massstorage then it needs to be switched.
but there be a problem as it is not listed in the usb_modeswitch data

 Nokia's CS10 15 17 and 18 use the same message content, may work with CS-19 ?

if the usb_modeswitch works with the device CS-19  ID's and the message content from the above
perhaps making a file in the /etc/usb_modeswitch.d directory may work (use the device ids as the file name)

but suggest joining the usb_modeswitch forum

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by orwtech@gmail.com on 2011-01-14
:KS
 
Hi [alexfish]("http://ubuntuforums.org/member.php?u=934779")

Thank you! You guided me in the right direction.

Did what you suggested and found this link: 

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=524](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=524)

Rough thing I did:

$ sudo usb-devices

Got the result:

Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0421 ProdID=062c Rev=00.01
S:  Manufacturer=Nokia
S:  Product=Nokia Datacard
S:  SerialNumber=0.0.1
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

$ cd /etc/usb_modeswitch.d

$ sudo cp 0421:0610 0421:062c

$ sudo vi 0421:062c

Changed the file to look like this:

########################################################
# Nokia CS-19

DefaultVendor= 0x0421
DefaultProduct=0x062c

TargetVendor=  0x0421
TargetProduct= 0x0612

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

----------------

Edited the file
$ sudo vi /lib/udev/rules.d/40-usb_modeswitch.rules

Added the lines:
# Nokia CS-18
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="0627", RUN+="usb_modeswitch '%b/%k'" 
# Nokia CS-19
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="062c", RUN+="usb_modeswitch '%b/%k'" 


Plugged in the USB stick an it was detected and ready to use

Thank you again

Respect !

Jesper

---

