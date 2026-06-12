---
title: "Rogers 3G not connecting after lucid update"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by mrpenguin on 2010-05-24
It took me a few weeks of searching around on the internet before I was finally able to connect my Rogers stick to connect on the internet with Ubuntu 

I updated my Netbook that had Remix on it but the next day after updating it I was not able to connect my rogers stick anymore.

Can anybody tell me what has changed on the new lucid update that is now preventing my rogers 3G stick to work ?

This is what I do or rather used to do to connect ...



> sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1

sudo gedit /etc/wvdial.conf


[Dialer rogers-nopin]

Phone = *99#

Username = wapuser1

Password = wap

Modem = /dev/ttyACM0

Baud = 460800

Init1 = AT+CPIN?

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = ATX3

Init4 = AT+CFUN=6

ISDN = 0

Modem Type = USB Modem

Init5 =AT +CGDCONT=1,"IP","internet.com","",0,0;

Auto DNS

Check DNS

sudo usb_modeswitch -v 0fce -p d103 -O

sudo wvdial rogers-nopin

---

### Post by pdc on 2010-05-25
I wonder if you try configuring by right-clicking on network manager; 

as in post #54 here

[http://ubuntuforums.org/showthread.php?p=9356474#post9356474](http://ubuntuforums.org/showthread.php?p=9356474#post9356474)

...... meaning you might not need wvdial; (which I would have thought would go on working with 10.04

I suspect you do not need usb_modeswitch now with 10.04; I noticed my ZTE MF636; (that needed ejecting) now just flips automatically and can be configured very easily ..

one sees very few posts on mobile broadband with 10.04; I was wondering if this was not due to the fact it was mainly "working" for people ..

---

### Post by CheshireMac on 2010-05-25
I'm having an issue with my Rogers stick too . . . the issue is that I have to boot into Windows first and connect there. Then rebooting to Ubuntu, it's connected, but drops the connection at seemingly random times. Once it disconnects, I'm unable to reconnect and have to do the whole thing over again. You can imagine my frustration. I've tried looking into the USB-Modeswitch thing, but I'm not sure I've done it correctly, or if I have, it hasn't worked. 
I'm running an Acer Aspire One, and I've tried a few things I've read as solutions on here, but to no avail. It's a really annoying way of connecting to the web, and I'd rather just be able to connect directly through Linux.

---

### Post by pdc on 2010-05-26
one assumes some "update" in 10.04 has upset the system

one can suggest

1) waiting for a fix

2) reporting a bug

3) try wvdial instead:

post #33 

[http://ubuntuforums.org/showthread.php?t=1360327&page=4](http://ubuntuforums.org/showthread.php?t=1360327&page=4)

has a working wvdial script; 

you get wvdial by 

> sudo apt-get install wvdial

and you copy and paste the wvdial script into the empty /etc/wvdial.conf file by 

> sudo gedit /etc/wvdial.conf

and pasting from #33 and saving and closing and then trying 

> sudo wvdial 

some have used

> sudo wvdial rogers no-pin

4) install another utility: sakis3g

[http://www.sakis3g.org/](http://www.sakis3g.org/)

I tried it today on a mandriva install on an Eee and it worked well; running a 3565-Z vodafone modem

---

### Post by mrpenguin on 2010-05-28
10.04 is driving me nuts

My Rogers Rocket stick used to work but now i get the following message 

"_Segmentation fault_"

> jaques@jaques-laptop:~$ sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1
[sudo] password for jaques: 

Looking for default devices ...
 Found default devices (1)
Accessing device 003 on bus 002 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: SEMC
   Model String: MMC Flash Card
Revision String:    0
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
####################Segmentation fault
jaques@jaques-laptop:~$ 


I really need to get this working because soon my rocket stick will be my only way to get on the internet

---

### Post by pdc on 2010-05-28
each linux distro is "free": so you are allowed to try another one; you need to be on-line, you tell us  ....  so ..........   download the new fedora 13: the gnome liveCD is less than 700MB; (as they all are); it has the latest network manager;

try it out on a usb-stick

[http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo](http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo)

or try the latest Mint 9: ubuntu has a USB stick creator; so that works for .deb based distros: download the mint .iso and burn it to a 1G or 2G USB stick; boot your computer from that; see if the Rogers works on that

ANOTHER WAY: as you don't seem to have considered the wvdial I have already suggested ..............

is sakis3g

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation)

HOWEVER: if ROGERS is CDMA based? (Do you know?) .......... it will not work but for GSM it installed easily; recognised my modem, and dialled to the right network .............

what think you? mon ami?

---

### Post by mrpenguin on 2010-05-29
I have used wvdial ... If you look at the first post of this threat you will See exactly how I used to be able to connect my Rogers rocket stick to the Internet, that way worked perfectly till I updated to 10.04 and now it don't work anymore.

I do not want to use another distro, I have ubuntu on my laptop and remix on my netbook and it was working perfectly fine till I updated to 10.04

---

### Post by alexfish on 2010-05-29
> **mrpenguin said:**
> I have used wvdial ... If you look at the first post of this threat you will See exactly how I used to be able to connect my Rogers rocket stick to the Internet, that way worked perfectly till I updated to 10.04 and now it don't work anymore.

I do not want to use another distro, I have ubuntu on my laptop and remix on my netbook and it was working perfectly fine till I updated to 10.04

can you post the results of this command from the terminal

Code:

dmesg | grep -e "modem" -e "tty"

---

### Post by mrpenguin on 2010-05-29
> **alexfish said:**
> can you post the results of this command from the terminal

Code:

dmesg | grep -e "modem" -e "tty"

I dont know what that is but here is the results 

> jaques@jaques-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
jaques@jaques-laptop:~$ 


---

### Post by pdc on 2010-05-30
so I think alex will tell you that 10.04 is not recognising your modem as a modem; strange; 

if you enter

> lsusb in a terminal to see what your system is recognising your device as;

from here

it should say 

> 5010

before being flipped and 

> 4400 if successfully flipped and seen as a modem

if it shows as 4400, it should give you a ttyUSB0 (or maybe ttyACM0 ?)

the ID comes from here

[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup)

if you search on Novatel MC950D you should find its entry

---

### Post by mrpenguin on 2010-05-31
This is what I am getting from the lsusb command

> jaques@jaques-netbook:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0fce:d103 Sony Ericsson Mobile Communications AB 
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The  Sony Ericsson Mobile is my Rogers Rocket stick

I would still like to know what "segmentation fault" means when I try to do a usb mode switch that always worked with 9.04 but not with 10.04

> jaques@jaques-netbook:~$ sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1

Looking for default devices ...
 Found default devices (1)
Accessing device 004 on bus 001 ...
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: SEMC
   Model String: MMC Flash Card
Revision String:    0
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212606100
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
####################Segmentation fault


---

### Post by pdc on 2010-05-31
well; I can't see this 

> 0fce:d103

in the usb_modeswitch.setup file

[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup)

The only entry there for sony ericsson I can see is 

> # Sony Ericsson MD400
#
# Special procedure, takes around 25 secs. on the whole

;DefaultVendor=  0x0fce 
;DefaultProduct= 0xd0e1

;TargetClass=    0x02

;SonyMode=1
;Configuration=2


and when I see

> ooking for active driver ...
No driver found. Either detached before or never attached
Trying to send Sony control message
OK, control message sent, waiting for device to return ...
####################Segmentation fault 

the device is not flipping and 

> dmesg | grep tty

has shown that

I recommend you join the usb_modeswitch forum;

Josh oversees the software and replies daily to folks: he is very knowledgable

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

what I cannot understand is I cannot see an entry for this device in the usb_modeswitch.setup file .......

---

### Post by mrpenguin on 2010-06-01
Thanks, going to check that out tonight. 

What I don't understand is what did update 10.04 change on my laptop to make it not work anymore because it was working perfectly on 9.04

---

### Post by alexfish on 2010-06-02
> **mrpenguin said:**
> Thanks, going to check that out tonight. 

What I don't understand is what did update 10.04 change on my laptop to make it not work anymore because it was working perfectly on 9.04


hi

you may have to alter the

Modem = /dev/ttyACM0

in the wvdial.conf  to match one of the ports listed by the command

Code:

dmesg | grep -e "modem" -e "tty"

---

### Post by mrpenguin on 2010-06-02
Thanks all I got it working thanks to Josh at usb modeswitch forum

I had an old version of usb modeswitch version 0.1.12 on my computer, no idea why its old sinse I installed it only a couple of days ago after reinstalling 10.04

I installed 1.1.12 and now it works ....

---

### Post by pdc on 2010-06-02
great; enjoy

---

