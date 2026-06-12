---
title: "Pantech USB broadband modem and 11.10"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by mike.jones on 2011-11-17
I've got a Pantech 290 broadband modem with Verizon. It works fine (with the VZManager software) on my Windows laptop, but I can't seem to get it to work with my Kubuntu Onieric laptop. It seems to recognize the modem (as /tty/ACM0) when I plug it in. Network Manager seems to recognize that it's there, but can't make a connection with it. I've seen reports that this "just works" in 11.04, but apparently not in 11.10. Any suggestions? Is there any way to get network manager to spit out debugging info about what it's trying to do?

---

### Post by alexfish on 2011-11-17
the problem may lay with modem-manager

can download mm-test.py from here
```
wget http://cgit.freedesktop.org/ModemManager/ModemManager/plain/test/mm-test.py
```it should be in your home folder.

or paste in the browser```
http://cgit.freedesktop.org/ModemManager/ModemManager/plain/test/mm-test.py
```save the page to the home directory ensure named "mm-test.py".

run it as root
```
sudo su
python `pwd`/mm-test.py
```

can also try
```
killall modem-manager
``` if modem-manager hanging onto the device
wait a while for modem-manager to re init and prob the device , then do the test again

alexfish

---

### Post by mike.jones on 2011-11-17
OK, I downloaded the script and ran it. Got this:
```

CDMA modem
Driver: 'cdc_acm'
Modem device: '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3'
Data device: 'ttyACM0'
Vendor:  PCD
Model:   UML290VW
Version: L0290VWB522F.242  1  [May 12 2011 13:21:52]

ESN: <private>
1x State:   registered (roaming unknown)
EVDO State: registered (roaming unknown)
Signal quality: 48
Class: Unknown
Band:  Z
SID:   78

```

When I look at it in Network Manager,
it looks like this (Note - I did check "enable mobile broadband):
```

Type: Mobile Broadband
Connection State: not enabled
IP Address: no address
Connection Speed: unknown
System Name: ttyACM0
MAC Address: 
Driver: cdc_acm
Operator: 
Signal Quality: 0%
Access Technology: unknown/unknown

```

When I look at the configuration for the wireless connection in Network Manager, it's set to
```

Number: #777
Username: <mynumber>@vzw4g.com
Password: vzw

```

Any other suggestions?

---

### Post by alexfish on 2011-11-17
need to see if got net interface , may see from what drivers are loaded

can post the results of 

```
usb-devices
```

---

### Post by mike.jones on 2011-11-17
Output of "sudo usb-devices":

```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=106c ProdID=3718 Rev=00.00
S:  Manufacturer=Pantech, Incorporated
S:  Product=PANTECH UML290
C:  #Ifs= 6 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcaux
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=fd Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=fe Prot=ff Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=f0 Prot=ff Driver=(none)

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52b Rev=12.01
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=05 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=05a4 ProdID=9840 Rev=01.10
S:  Product=USB Compliant Keypad
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=48mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

Looks like it's right there at the top, but I don't know how to decode the I: lines. 

Also, I went into /etc/NetworkManager/NetworkManager.conf and added a logging stanza to log debug info about mobile broadband. When I tried to connect with the modem I got this in the log:
```

Nov 17 13:56:29 Ultor modem-manager[21432]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Nov 17 13:56:29 Ultor modem-manager[21432]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> registered)
Nov 17 13:56:29 Ultor NetworkManager[21434]: <warn> CDMA connection failed: (32) No carrier
Nov 17 13:56:29 Ultor NetworkManager[21434]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Nov 17 13:56:29 Ultor NetworkManager[21434]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed

```

---

### Post by alexfish on 2011-11-17
no sure if the  parts of the diver are binding to the device correctly
although the correct driver has loaded for the device
can be seen from

```
grep -i v106cp3718 /lib/modules/`uname -r`/modules.alias
```so need more info
```
grep  v106cp3718 /sys/bus/usb/devices/*/modalias
```

---

### Post by mike.jones on 2011-11-17
First, thanks for the help so far!

Here's what I get
```

mike@Ultor:~$ grep -i v106cp3718 /lib/modules/`uname -r`/modules.alias
alias usb:v106Cp3718d*dc*dsc*dp*icFFiscFFipFF* qcaux

```
and
```

mike@Ultor:~$ grep  v106cp3718 /sys/bus/usb/devices/*/modalias
mike@Ultor:~$ 

```

---

### Post by alexfish on 2011-11-17
hi
think made common typo in the above[FONT=monospace] notice the lower and upper case
the usb ids module(modalias) is different to whats logged in the files
[/FONT]```
grep  v106Cp3718 /sys/bus/usb/devices/*/modalias
```


 Network Manager is indicating fail at  " if0"  
> Nov 17 13:56:29 Ultor NetworkManager[21434]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed 
Nov 17 13:56:29 Ultor NetworkManager[21434]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failedbut mm indicates a dial up connection has been made
Nov 17 13:56:29 Ultor modem-manager<info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting) 
Nov 17 13:56:29 Ultor modem-manager[21432]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> registered)

so not sure where what the problem is [FONT=monospace]

the message from the device "[/FONT]No carrier"

is pppd failing to negotiated the connection or is the port closing before before the pppd is starting, can look further into the log files
have done a post about logging mm and nm at

[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490")

at the end of the thread there is a script which may shed some light about the device can use the script with arg "tty" the out put will show the status line of the device + responce to at command ; then will list all of what udev sees about the device

if trying some of the testing from 2 terminals then don't forget to use ATDT#777

although mm is seeing the device it is picking up the first port as indicated by mm ACM0
so can see if the device is in the dev
```
ls -al /dev/serial/by-id
``````
ls /dev/ttyACM*
```also try can try ppp directly or wvdial  see what happens

---

### Post by alexfish on 2011-11-18
had to some thinking about this mm-test.py , first time thought about taking it for a ride

to get this thing to work need' mm-test-pppd-plugin.so 

got it from
     [http://pkgs.org/download/ModemManager](http://pkgs.org/download/ModemManager)
 its and rpm package (openSUSE factory)
make sure its the latest source package and ensure it lists the mm-test-pppd-plugin.so and correct 586(32 bit) or amd64 bit

just upack and find the ' mm-test-pppd-plugin.so 
can use gksu nautilus on Ubuntu : don't know about kubuntu
or as root sudo su , cp it to
> /usr/lib/pppd/2.4.5/then from the terminal
```
sudo su
python /home/<user>/mm-test.py --no-scan  --connect --ip
```alexfish

---

### Post by mike.jones on 2011-11-20
OK, with the upper case issue sorted out, I get
```

/sys/bus/usb/devices/1-3:1.0/modalias:usb:v106Cp3718d0000dc02dsc00dp00ic02isc02ip01
/sys/bus/usb/devices/1-3:1.1/modalias:usb:v106Cp3718d0000dc02dsc00dp00ic0Aisc00ip00
/sys/bus/usb/devices/1-3:1.2/modalias:usb:v106Cp3718d0000dc02dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-3:1.3/modalias:usb:v106Cp3718d0000dc02dsc00dp00icFFiscFDipFF
/sys/bus/usb/devices/1-3:1.4/modalias:usb:v106Cp3718d0000dc02dsc00dp00icFFiscFEipFF
/sys/bus/usb/devices/1-3:1.5/modalias:usb:v106Cp3718d0000dc02dsc00dp00icFFiscF0ipFF

```

---

### Post by mike.jones on 2011-11-20
Haven't been able to build that library. I downloaded the source package and got a number of errors in the configure step about missing packages. Was able to find all of them except gudev-1.0. I've installed everything with "udev" in its name that looks like it could be related, but it's still not finding that.

---

### Post by mike.jones on 2011-11-21
OK, got the binary package and copied that .so into the pppd directory. Here's what I get:
```

root@Ultor:/home/mike# python mm-test.py --no-scan --connect --ip
CDMA modem
Driver: 'cdc_acm'
Modem device: '/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3'
Data device: 'ttyACM0'
Vendor:  PCD
Model:   UML290VW
Version: L0290VWB522F.242  1  [May 12 2011 13:21:52]

ESN: <private>
1x State:   unknown
EVDO State: unknown
Signal quality: 51
Class: Unknown
Band:  Z
SID:   275
Error connecting: org.freedesktop.ModemManager.Modem.Gsm.NoNetwork: No service

```

---

### Post by alexfish on 2011-11-21
hi

from the listing modem-manager is trying to dial gsm connection *99# it does not recognize the device as CDMA-EVDO as suggested , your details you have #777 , , seems modem-manager is returning the wrong
type of device whist it is been enumerated ,?, . IE 1 or 2  at the connecting stage   , yet indicates = 2 > " CDMA  modem"   ..can post details of modem-manager and network-manager versions, possible to install versions where the device worked'.. added will also  look at the script. to see if there
are any oop's.

can also suggest for now using pppconfig for the connection using /dev/ttyACM0 or try WVdial see what happens. remember NM and MM are only front end to the [COLOR=Blue]pppd[/COLOR] as is ppp and wvdial, [COLOR=Blue]pppd[/COLOR] does the work after a CONNECT message is received

in the How to
[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490")

there is how to connect from ,script , wvdial , ppp +  how to use 2 terminal as a serial port, can use the dial command ATDT#777 to see if a CONNECT message arrives on /dev/ttyACM0 .

ADDED: from the modalias . This device seems to have 2 types of connections available. But will take time to search which types of drivers will be suitable , will post later if found

alexfish

---

### Post by alexfish on 2011-11-21
looking at the modalias part of this device looks as if got 

firmware uploader for USB

indicating possible driver = i1480_dfu_usb

but don't change see if can get device working or possible to try in windows , see if the firmware needs updating

ADDED from part of the modalias (parts with no driver and indicates up-loader )   [FONT=monospace]"[/FONT]icFFiscFFipFF "  this usually indicates GSM type of device , not sure if modem-manager looks at this 

As requested need inf from this command[FONT=monospace]. Important
[/FONT]```
ls -al /dev/serial/by-id
```Need this to confirm the port orientation , IE to see if it lists the same as the usb-devices output,  it will list the "IF" have known of devices been incorrectly switched by ejecting the device after modeswitching.. AS said this is important to have this info
EG , if the device incorrectly switched the ttyACM**** , get reversed this this can make some connection managers connecting to the wrong port: this is mentioned at post #16 of the how to

ADDED see below[FONT=monospace] 
[/FONT]I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm  > CDMA  normaly ACM0
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm  > CDMA   normaly ACM1
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcaux   > this last part could look as if GSM  : but the first part of modalias from the actual device , indicates CDMA

Just found this
>  [1]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L1") ***/****   [2]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L2") *** * Qualcomm USB Auxiliary Serial Port driver***   [3]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L3") *** ****   [4]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L4") *** * Copyright (C) 2008 Greg Kroah-Hartman <greg@kroah.com>***   [5]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L5") *** * Copyright (C) 2010 Dan Williams <dcbw@redhat.com>***   [6]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L6") *** ****   [7]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L7") *** *  This program is free software; you can redistribute it and/or modify***   [8]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L8") *** *  it under the terms of the GNU General Public License version 2 as***   [9]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L9") *** *  published by the Free Software Foundation.***  [10]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L10") *** ****  [11]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L11") *** * Devices listed here usually provide a CDC ACM port on which normal modem***  [12]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L12") *** * AT commands and PPP can be used.  But when that port is in-use by PPP it***  [13]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L13") *** * cannot be used simultaneously for status or signal strength.  Instead, the***  [14]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L14") *** * ports here can be queried for that information using the Qualcomm DM***  [15]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L15") *** * protocol.***  [16]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L16") *** */***  [17]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L17")   [18]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L18") #include <linux/kernel.h>  [19]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L19") #include <linux/init.h>  [20]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L20") #include <linux/tty.h>  [21]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L21") #include <linux/module.h>  [22]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L22") #include <linux/usb.h>  [23]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L23") #include <linux/usb/serial.h>  [24]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L24")   [25]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L25") ***/* NOTE: for now, only use this driver for devices that provide a CDC-ACM port***  [26]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L26") *** * for normal AT commands, but also provide secondary USB interfaces for the***  [27]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L27") *** * QCDM-capable ports.  Devices that do not provide a CDC-ACM port should***  [28]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L28") *** * probably be driven by option.ko.***  [29]("http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c#L29") *** */***
[http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c](http://lxr.free-electrons.com/source/drivers/usb/serial/qcaux.c)

Seams to confirm  initial thoughts , hope read PM , 


****
alexfish

---

