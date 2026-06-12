---
title: "Issue with reliance netconnect cdma usb modem"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by sumitjha06 on 2010-10-17
I am net to linux(ubuntu 10.10). for me everthing works except for my reliance netconnect zte model. i don't have any other source og netconnection to update package. i saw lot of posts for this issue but i was not able to resolve the issue. if i can get a step by step guide, that will be really helpful

please help,

---

### Post by dineshs on 2010-10-17
Have you tried Network manager?
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab Mobile broadband and proceed
(While configuring tick Available to users)
After configuring click on the same icon to connect/disconnect
If there is no progress please post the results of
```
lsusb
```and```
dmesg | grep -e "modem" -e "tty" 
```

---

### Post by raunhar on 2010-10-19
I too am having the same problem with the ZTE AC2736 device,  Ubuntu is 10.04. with the latest Kernel
lsusb shows the device as 
Bus 006 Device 002: ID 19d2:fff5 ONDA Communication S.p.A. 

dmesg
$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
[ 2280.321188] usb 6-1: generic converter now attached to ttyUSB0

The NW manager does not show the device under Mobile Broadband

The CrossplatformUI-V.1.0-38 (deb file that is on the driver CD) also does not get installed.

The manual says that the device is compatible with LINUX OS.

Really looking for a solution.

---

### Post by dineshs on 2010-10-19
raunhar,
Have you seen
[http://www.idlecool.net/usb-modeswitch-issue-with-reliance-netconnect-zte-mg880-cdma-1x-ubuntu-linu/](http://www.idlecool.net/usb-modeswitch-issue-with-reliance-netconnect-zte-mg880-cdma-1x-ubuntu-linu/)

---

### Post by raunhar on 2010-10-19
tried it, but ALAS not worked.

---

### Post by kiers on 2010-12-12
raunhar, guys,  its not your fault. I too have 10.04 UNE. I have successfully installed the ztemt app.

(It is reliance adag group fault) (they are ignoring Ubuntu in a poor country like India).  

(If we indians think indian customer service is BAD, of course other developed countries will also feel worse about it). ( i myself have gotten tired of shoddy indian customer service!) (indian corporation have ONE WAY relationship with Indian customers: take money, that's all) 

THIS issue has been REPEATED ad nauseam all over google etc, and it is all mostly Indians instigating, because of lack of concern by the elite corporate rajas.

Heres what u do:
open synaptic package manager
install gcc (the c compiler)
install kernel package (kernel devlopment tool kit)
install update udev utility
install usb-modeswitch
install usb-modeswitch data.
reboot system.

next open terminal
change directory to /usr/local/bin/ztemtApp/zteusbserial

ls to see all subdirectories organized by kernel version
do uname -a to check your kernel ver.
IF it is 10.04LTS then safely COPY 2.6.31 to NEW FOLDER 2.6.32.
(note these are the C files with headers and makefiles required for install script to function).

Now run your install package (search for the deb package on google, or u can get it from reliance (lousy people) web site itself to be safe. it is called "CrossPlatformUI-V1.0-38-RelianceHSD-i386-Ubuntu.deb"

double click/install that file. it will run through and compile the silly launch utility and we can all be happy. Ohter solutions on web do NOT realize that people will want to ACTIVATE the modem using ubuntu as well, therefore u need the correct modem AT codes that the silly dialer utility is providing. So my solution here is first that adresses using the original dialer utillity itself on ubuntu. others are using wvdial and network manager. HERE U MUST TURN OFF NETWORKING under "network manager"in ubuntu. it will conflict.

HOPEFULLY THIS WILL PUT AN END TO THE REPEAT WHINING about USB modem not working in Linux FROM INDIA all over google due to total neglect of indian customer by (trust me i've tried talking to adag) by ADAG Reliance.

.....now,if we were "phoren clients" then adag would polish our shoes for us!

---

### Post by raunhar on 2010-12-13
First Thing: India is not a poor country.
Second thing: Linux gets less support, because there are is not much awareness about it, so all companies prefer to provide support to Windows rather than LINUX .

Till Linux gets more acceptance, its users will be neglected.

---

### Post by Pritamsng on 2010-12-13
Dear Kiers,
                1st of all do u know... Reliance is an Indian Company. :) 
                2nd its working for me.. lol..

---

### Post by raviepic3 on 2011-01-09
I am on ubuntu 10.10 64 bit version.  

I got the card up and running just by using the network manager, i set up a new mobile braoadband connection and done.   

[COLOR=Red]But the issue is it takes around 1 to 2 mins sometimes for it to detect my plugged in reliance data card.  [/COLOR]
[COLOR=Red]
[/COLOR][INDENT][COLOR=Red]1. Is this normal ?   [/COLOR]
[/INDENT]

[COLOR=Red]The deb package accompanied with the reliance cd   CrossPlatformUI-V1.0-38-RelianceHSD-i386-Ubuntu.deb  aint supporting 64 bit OS,   [/COLOR]
[COLOR=Red]
[/COLOR][INDENT][COLOR=Red]2. Is there a way i can convert this deb into supporting my 64 bit os just to have the GUI part of reliance connect ? [/COLOR]
[/INDENT]

[COLOR=Red]Seems i can configure my connection type as 1X or HSD or Hybrid using my  reliance data connect GUI which i am not able to bring it up in my 64  bit system as said earlier. Now its using 1X by default[/COLOR]
[COLOR=Red]
[/COLOR][INDENT][COLOR=Red]3. , so howd i change it to HSD ?[/COLOR][/INDENT]

---

### Post by raunhar on 2011-01-10
The software that comes with Reliance device is for versions 9.04 only and does not support later versions.

The delay is normal with the device for Reliance devices only. If any other device, there is no delay

---

### Post by kiers on 2011-01-10
> **raviepic3 said:**
> ....   

[COLOR=Red]But the issue is it takes around 1 to 2 mins sometimes for it to detect my plugged in reliance data card.  [/COLOR]
[COLOR=Red]
[/COLOR][INDENT][COLOR=Red]1. Is this normal ?   [/COLOR]
[/INDENT][COLOR=Red]The deb package accompanied with the reliance cd   CrossPlatformUI-V1.0-38-RelianceHSD-i386-Ubuntu.deb  aint supporting 64 bit OS,   [/COLOR]


Yes, i had the same problem with time delay. But I am running the original intended shell driver provided by reliance and i was able to get rid of delay (instant recognition of device) by DISABLING ModemManager. (if you google you will find steps accordingly).

but as i mentioned above, i recompiled the given c code driver on my netbook (Ubuntu 10.04; YES I know zte says it's only upto earlier version 28 kernel, but i am up and running on my version 32 kernel! w/o hitch) and this allows me to set HSD vs 1X speeds etc. 

It's shame that IT company like ADAG reliance can't take UBuntu seriously enough. B/C their dialer DOES WORK on linux as is!

---

### Post by raviepic3 on 2011-01-11
Oh, thanks for replying.

Any idea on how i can change the connection mode from 1x to HSD or Hybrid ?

---

### Post by ramakrishna0265 on 2011-02-04
Hi 
i too have problem on zte ac 2736.unable to install even on 9.04.in the mobile broad band reliance name is not there .what to do i thought of format and installing 9.10 since it has reliance name but looking the woes of u guys i am confused what to do?

---

### Post by raunhar on 2011-02-05
The software (LINUX Vresion) that comes with ZTE AC2736, can be installed on 9.04 without any problems. The interface of the software is just like that of Windows interface.

---

### Post by shrijith1 on 2011-03-13
> **raviepic3 said:**
> Oh, thanks for replying.

Any idea on how i can change the connection mode from 1x to HSD or Hybrid ?
I have had the same issue. Delay of 2 mins before it detects the usb modem. One thing I have noticed is that if I connect to internet using gnome-ppp, I can see the mobile broadband option just after it connects. So, there should be some setting to overcome this delay. I tried putting the modprobe command in /etc/rc.local but that doesn't help. 

Any other idea?

---

### Post by alexfish on 2011-03-13
hi

can try disable modemmanager see what happens

alexfish

---

### Post by bichu93 on 2011-03-21
[http://anshumanpandey.net/2010/08/08/using-mts-mblaze-ubuntu/]("http://anshumanpandey.net/2010/08/08/using-mts-mblaze-ubuntu/")



ALL U NEED IS HERE CHECK THIS LINK

---

