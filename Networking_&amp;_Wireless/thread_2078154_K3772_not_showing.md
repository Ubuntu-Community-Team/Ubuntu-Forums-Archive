---
title: "K3772 not showing"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by juliancam on 2012-10-30
Hello. I am trying to set up a vodafone K3772 3G dongle in 12.04 but no device is listed when I try to add a mobile broadband connection. The K3772 device is listed under the usb-modprobe data file and when I do lsusb I get:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 12d1:1526 Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 13d3:5711 IMC Networks 

but when I try to set up a mobile connection the drop down list for devices is grey out with "any device". If try to go ahead and set it up anyway nothing shows under wireless connections. A search of google got me trying to echo the last two into /sys/bus/usb-serial/drivers/option1/new_id but I think that is for if a device is not recognized and other people talk of a new usb device window that should have popped up but didn't.  My only thoughts were if maybe the Windows setup files on the stick could be interferring with it, but I don't want to get rid of them unless I have to incase I need them for a windows machine.   Any suggestions? 

(this is my first attempt at setting up a 3g mobile connection. I know 
the device works because it set up ok in windozzzzzzzz)

Julian

---

### Post by ajgreeny on 2012-10-30
The connection will not show in wireless connections but in Mobile Broadband connections.  Open up network connections by right clicking on the network icon in the panel, then go to the Mobile Broadband tab and see if you can add or configure the dongle there.

If it is supported and enabled it should just work.

---

### Post by alexfish on 2012-10-30
Possible this is a new device , RE: the ID = 12d1:1526 , and not listed here
[http://www.draisberghof.de/usb_modeswitch/device_reference.txt](http://www.draisberghof.de/usb_modeswitch/device_reference.txt)
Huawei generally have Two switching codes,

in linux If the device has not switched , generally shown by this command from the terminal
```
usb-devices
```
If not switched it will show as a storage device , if swiched it will show the nodes + possible the driver

if shows only as storage the best to visit will be usb_modeswitch forum

[ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")


Regards

alexfish

---

### Post by juliancam on 2012-10-30
> **ajgreeny said:**
> The connection will not show in wireless connections but in Mobile Broadband connections.  Open up network connections by right clicking on the network icon in the panel, then go to the Mobile Broadband tab and see if you can add or configure the dongle there.

If it is supported and enabled it should just work.

Sorry, I don't think I made myself  very clear.  I _am_ trying to add it as a mobile broadband devices, but there are no devices listed in what would be the drop down menu of devices. The wireless reference was to look for the connection after I tried to configure the connection  against the grayed out "any device" in network manager .

Julian

---

### Post by juliancam on 2012-10-30
> **alexfish said:**
> Possible this is a new device , RE: the ID = 12d1:1526 , and not listed here
[http://www.draisberghof.de/usb_modeswitch/device_reference.txt](http://www.draisberghof.de/usb_modeswitch/device_reference.txt)
Huawei generally have Two switching codes,

in linux If the device has not switched , generally shown by this command from the terminal
```
usb-devices
```If not switched it will show as a storage device , if swiched it will show the nodes + possible the driver

if shows only as storage the best to visit will be usb_modeswitch forum

[ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")  

hmm, usb-devices reports this:

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-32-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1526 Rev=01.02
S:  Manufacturer=Vodafone (Huawei)
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=5711 Rev=12.04
S:  Manufacturer=Azurewave
S:  Product=USB 2.0 UVC VGA WebCam
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-32-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-32-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-32-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.02
S:  Manufacturer=Linux 3.2.0-32-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub




Regards

alexfish[/QUOTE]

The second paragraph suggests it is being picked up as a modem doesn't it?  (or maybe not on second reread ; maybe I better go to that modeswitch forum)  On the other hand it is definitely showing in the Places menu as a storage device and I have just noticed that line "I" has driver=usb-storage so does that mean it has not switched?

Julian

---

### Post by alexfish on 2012-10-30
@ Julian

```

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1526 Rev=01.02
S:  Manufacturer=Vodafone (Huawei)
S:  Product=Vodafone Mobile Broadband (Huawei)
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=[COLOR=Red]usb-storage[/COLOR] < [COLOR=Red]Not Switched[/COLOR]>
``` Go to the usb_modeswitch forum , sure Josh will be of assistance.

if the device ID is definite new, then if Solved , this will help others to get connected
what gets listed there will find it's way back in all linux distro's

also to highlight "Cls=08(stor.) " also  = storage
Regards

Alex

---

