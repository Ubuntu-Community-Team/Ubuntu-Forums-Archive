---
title: "Vodafone Installation Software for Mobile Broadband - will not install."
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by zozza on 2010-10-03
I have a Vodafone mobile broadband dongle for the United Kingdom.  The installation software is for Windows and Macs only.  In Windows it works fine.  If I plug the dongle in the USB in Ubuntu then it is recognised but the installation does not start (quite understandably). 

So I tried using wine with the Windows executable.  It starts off promisingly, then hangs.  Some files are created along with desktop icons but the installation does not complete.  

I have seen here ([http://ubuntuforums.org/showthread.php?t=1466490&highlight=vodafone](http://ubuntuforums.org/showthread.php?t=1466490&highlight=vodafone)) the comment that Vodafone installation can be tricky.  

Please note that my issue is not the connection - it is the software installation that will enable any potential connection to be made.  

So, can any kind person tell me if it is possible to get Vodafone dongles working under 10.04? 

Also, are there any other UK broadband pay-as-you-go dongles that will work?  I have seen in a very recent post that "3" seems to be plug-and-play?

Thanks.

---

### Post by alexfish on 2010-10-03
hi

I am assuming you trying to run the software loaded on the device

there is a Linux version from Betavine but the 10.04 is still in development
so can't say if the recent version is bug free , so be prepared to un-install if there are
problems 

the actual sofware will install no problem if you disable the existing usb_modeswitch

[http://www.betavine.net/datacards/index.php/Main_Page](http://www.betavine.net/datacards/index.php/Main_Page)

---

### Post by zozza on 2010-10-04
> **alexfish said:**
> hi

I am assuming you trying to run the software loaded on the device

there is a Linux version from Betavine but the 10.04 is still in development
so can't say if the recent version is bug free , so be prepared to un-install if there are
problems 

the actual sofware will install no problem if you disable the existing usb_modeswitch

[http://www.betavine.net/datacards/index.php/Main_Page](http://www.betavine.net/datacards/index.php/Main_Page)

Yes, I am trying to use the software on the dongle.

Thanks for the link - I see their are dozens of packages for Ubuntu - is there a specific one you would suggest?

Finally, when I do sudo usb_modeswitch it says: "Error: Could not find file /etc/usb-modeswitch.conf"

Thanks again.

---

### Post by alexfish on 2010-10-04
Hi

Please read all( think twice)

on the link page where it says 

Development version: Beta 2.99 suitable for Ubuntu 10 ( click on the link )

the latest Development Version shows as 2.99.12

Reminder to all readers, this software is as it says (Beta) Beta means not a final release

there are several files to download (suggest downloading all)
installing in sequence ( now does not depend on usb_modeswitch )

python messaging
wader core
bcm

it suggests

Notes: Ideally you should load the bcm, wader-core and python-messaging packages in this section, 
as they've been tested together. Additionally if you have device that is not recognised when inserted, 
try installing the updated usb-modeswitch-data package too. 

I have Just done an installation of BCM .This a basic synop

Modem (not of Vodafone origin . ZTE device) . device not recognised Network Manager and BCM
used alternate method to get connection

Modem (Vodafone origin. Huawie K3565) . device recognised by Network Manager and BCM
BCM configured the device and reported status (No problems)

since I use a variety of devices and ISP's , it was necessary for me to remove BCM 

Code used

code:
sudo apt-get --purge remove bcm

Result : None Vodafone Devices, not recognised in Network Manager (no connection available)
used alternate method of connecting and :will have to debug later:

Added
update: it was necessary to reinstall Modem Manager (this will remove the wader-core), then cleaned up the system with Ubuntu Tweak


alexfish

---

### Post by zozza on 2010-10-08
Code from usb-devices:

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1007 Rev=00.00
S:  Manufacturer=Vodafone (ZTE)
S:  Product=Vodafone Mobile Broadband K3570-Z
S:  SerialNumber=P680A8VDFD000000
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=02 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b071 Rev=15.44
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=CNF7129
S:  SerialNumber=SN0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-25-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by alexfish on 2010-10-09
looking up this device in the usb_modeswitch

##############################################################################
# Vodafone (ZTE) K3570-Z

DefaultVendor= 0x19d2
DefaultProduct=0x1007

TargetVendor=  0x19d2
TargetProduct= 0x1008

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"
###############################################################################
the usb_modeswitch may work

but you could try the following first

**Assuming** the usb_modeswitch is not installed( if it has been installed then it may be resetting the device )
 so un-installing the  usb_modeswitch may may work

also try

from the terminal

code:
[COLOR=Blue]sudo gedit /etc/udev/rules.d/zte_eject.rules[/COLOR]

add the following line

[COLOR=Blue]SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="1007", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"[/COLOR]

save the file , exit and reboot see what happens

if it does not work, remove the above line ,then try usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

follow the debian link [COLOR=Blue]important[/COLOR] (you will need the [COLOR=Blue]usb_modeswitch[/COLOR] + the [COLOR=Blue]data package[/COLOR])
these will self install when in ubuntu

if ubuntu 10.04 use the sid(unstable) , this does not mean the programm is unstable

If you want to try the Betavine software: this is a suggestion

try sakis3g from here(download the package"embedded usb_modeswitch) this will allow independent modeswitching
IE:will only mode-switch a device if requested

**[*Sakis3G*  - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=BTqwTMqAMMuG4AbBiLSuBg&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

this is an alternate method of dialup and independant of network manager ( so as mentioned above , alternate method of dial up )
see if you can connect with sakis3g , if everything OK

download the Betvine Software  from here
**[*[I]Betavine*[/I]]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBoQFjAA&url=http%3A%2F%2Fwww.betavine.net%2F&rct=j&q=betavine&ei=PzqwTNKOGZOT4QbslPmuBg&usg=AFQjCNEG1TulnCThxfGqqMFNfiPLr4yw-Q&cad=rja")**

See what happens . 

alexfish

---

