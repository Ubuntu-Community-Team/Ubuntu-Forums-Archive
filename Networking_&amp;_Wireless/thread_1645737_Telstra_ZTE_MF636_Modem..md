---
title: "Telstra ZTE MF636 Modem."
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by Brodie337 on 2010-12-15
Hi there!

I've got a telstra MF 636 modem that I've been trying to make work in Ubuntu 10.10.

Telstra have the modem report itself as a CD when it is first plugged in, but I've found out how to get around that using the terminal in the telstra software.

Anyway, my problem is that the computer will not recognise that the modem is plugged in. lsusb reports it as there, but the access point does not appear under the network icon 99 percent of the time. On the rare occasion it does, I click it, and it tries to connect, with the little animation and all, but it just disconnects.

If you need any more info, just let me know!

Thanks,
Brodie.

---

### Post by alexfish on 2010-12-15
Hi

are you say it can connect using the Telstra software , but can't connect with Network Manager

or

 modem gets recognized  using Telstra software , but  neither methods will  connect

or can explain further


can also post details of this command from the terminal when not working

Code:

usb-devices

alexfish

---

### Post by Brodie337 on 2010-12-15
Sorry about the poor description. I was half asleep earlier. :D

What happens is that I can see the modem in the output of lsusb, and its recognised as a modem, not a CD drive as the Telstra USBs usually are, because I used the terminal in the Telstra software to change that.

The problem is that although I can see the modem in lsusb, I cannot use it. The access point that I have created is not shown under the newtwork manager in the panel. VERY occasionally the network will appear there, but I cannot connect.

Heres the output of usb-devices with the modem plugged in:
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0031 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Technologies MSM
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 5 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=058f ProdID=6335 Rev=01.05
S:  Manufacturer=Generic
S:  Product=Mass Storage Device
S:  SerialNumber=058F63356336
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=03 Dev#=  3 Spd=480 MxCh= 0
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
S:  Manufacturer=Linux 2.6.35-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-23-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

---

### Post by alexfish on 2010-12-15
Hi

the device is showing two possibilities for the modem

I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option 
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

not sure if the Telstra software or possible kernel patch is correct


From a fresh boot: then issue the commands for Telstra.

can post details of these commands from the terminal

Code:

[COLOR=Blue]grep ZTE /var/log/syslog[/COLOR]


Code:

[COLOR=Blue]ls -al /dev/serial/by-id/*

[COLOR=Black]Added : does the device have other functions other than connecting to network and sms texting[/COLOR]
[/COLOR]

---

### Post by Brodie337 on 2010-12-15
Double post...

---

### Post by Brodie337 on 2010-12-15
I didnt know it could do anything other than internet, and I'm fairly certain that its got no SMS capability.

Would you like me to run those with the USB plugged in?

The two options might be because the device reports as a CD drive when it is first plugged into a Windows machine, so the user can install the Telstra software.

---

### Post by cascade9 on 2010-12-15
Oldish thread, but it might thelp- 

[http://forums.whirlpool.net.au/archive/1162175](http://forums.whirlpool.net.au/archive/1162175)

Whirlpool is the best source for any telstra/linux issues. ;)

---

### Post by alexfish on 2010-12-15
> **Brodie337 said:**
> I didnt know it could do anything other than internet, and I'm fairly certain that its got no SMS capability.

Would you like me to run those with the USB plugged in?

The two options might be because the device reports as a CD drive when it is first plugged into a Windows machine, so the user can install the Telstra software.


hi

Yes ; connect the device ; wait about 30 seconds then issue the commands

the commands are only to retrieve information about how the system is seeing the device

then if the correct port is found then : and if the " connection info is correct"  then the device should connect:

the above link to whirlpool is old : and there is no necessity to load a default serial driver for this device
as the option driver is already bound to the device. only exception is that , part of the device "maybe part of the storage facility for sd card has bound to the option driver "  this can lead to a connection manager failing to identify the correct port :

Please follow instructions as requested

alexfish

---

### Post by Brodie337 on 2010-12-15
grep ZTE /var/log/syslog returns:
```
Dec 14 21:45:57 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 14:19:02 Hydrogen kernel: [    2.619410] scsi 2:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 14:19:03 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 14:19:18 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 14:19:38 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 14:19:43 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 14:19:43 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 14:20:05 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 14:20:05 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB2
Dec 15 14:20:55 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB0
Dec 15 14:22:35 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 14:22:40 Hydrogen kernel: [  233.927751] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 14:22:50 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 14:22:55 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 14:23:10 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 14:23:37 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 14:23:37 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB2
Dec 15 14:24:27 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 14:24:27 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 14:24:32 Hydrogen kernel: [  345.932858] scsi 4:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 14:24:42 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 14:25:25 Hydrogen kernel: [    2.584408] scsi 2:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 14:25:25 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 14:25:41 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 14:26:01 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 14:26:06 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 14:26:06 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 14:26:28 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 14:26:28 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB2
Dec 15 14:26:53 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 14:26:53 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 14:26:58 Hydrogen kernel: [  108.472750] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 14:27:08 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 14:27:25 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 14:27:41 Hydrogen kernel: [  151.455749] scsi 4:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 14:27:51 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 14:28:11 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 14:28:16 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 14:28:16 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 14:28:38 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 14:28:38 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB2
Dec 15 14:28:40 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 14:28:53 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 14:28:58 Hydrogen kernel: [  228.468771] scsi 5:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 14:29:08 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 14:29:28 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 14:29:33 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 14:29:58 Hydrogen kernel: [  288.388731] scsi 6:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 14:30:08 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 14:30:28 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 14:30:51 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 15:10:17 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 15:11:43 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:11:48 Hydrogen kernel: [   65.374779] scsi 2:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:11:58 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:12:18 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:12:23 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:12:46 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 15:12:46 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB2
Dec 15 15:13:07 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 15:13:18 Hydrogen kernel: [  155.360776] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:13:28 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:13:45 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:13:45 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:13:45 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:17:39 Hydrogen kernel: [  195.883689] scsi 4:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:17:49 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:17:54 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:18:09 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:18:14 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:18:37 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 15:18:37 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB2
Dec 15 15:18:50 Hydrogen kernel: [  267.131708] scsi 5:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:19:00 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:19:20 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:19:25 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:19:25 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:19:47 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 15:19:47 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB2
Dec 15 15:20:37 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB0
Dec 15 15:24:48 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:24:48 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:24:53 Hydrogen kernel: [  629.712857] scsi 6:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:25:03 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:25:23 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:26:05 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:26:10 Hydrogen kernel: [  706.720835] scsi 7:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:26:20 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:27:28 Hydrogen modem-manager: do_grab_port: plugin 'ZTE' claimed to support tty/ttyUSB0 but couldn't: (-1) (unknown)
Dec 15 15:29:18 Hydrogen kernel: [  894.524495] scsi 8:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:30:11 Hydrogen kernel: [  947.529499] scsi 9:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:31:17 Hydrogen kernel: [    2.595364] scsi 2:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:31:17 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 15:31:32 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:31:52 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:31:57 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:31:57 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:32:19 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB1
Dec 15 15:32:19 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB2
Dec 15 15:33:08 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB0
Dec 15 15:44:51 Hydrogen kernel: [  141.436272] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:45:01 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:45:06 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:45:09 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:45:09 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:45:47 Hydrogen kernel: [  196.888876] scsi 4:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:45:57 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:46:02 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:46:10 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB2
Dec 15 15:47:03 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB0
Dec 15 15:49:37 Hydrogen kernel: [    2.596350] scsi 2:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:49:37 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 15:49:52 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:50:12 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:50:17 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:50:17 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 15:50:31 Hydrogen kernel: [   69.559455] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:50:41 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 15:51:01 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 15:51:24 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB1
Dec 15 15:52:17 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB0
Dec 15 15:52:39 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 15:52:44 Hydrogen kernel: [  202.597002] scsi 4:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 15:52:54 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 16:00:25 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 16:01:18 Hydrogen kernel: [   68.484763] scsi 2:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 16:01:28 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 16:01:33 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 16:01:33 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 16:01:48 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 16:02:14 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB1
Dec 15 16:02:14 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB2
Dec 15 16:02:58 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 16:03:03 Hydrogen kernel: [  174.241802] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 16:03:13 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 16:03:33 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 16:03:38 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 16:03:58 Hydrogen kernel: [  229.168748] scsi 4:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 16:04:08 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 16:04:28 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 16:04:51 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Dec 15 16:05:44 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB0
Dec 15 17:38:09 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 18:01:02 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 18:01:07 Hydrogen kernel: [ 1193.750817] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 18:01:17 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 15 18:01:22 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 18:01:37 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 18:02:06 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB2
Dec 15 18:02:06 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB1
Dec 15 18:02:56 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3 claimed port ttyUSB0
Dec 15 18:19:53 Hydrogen kernel: [ 1520.297344] scsi 4:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 18:20:03 Hydrogen modem-manager: (ttyUSB5): probe requested by plugin 'ZTE'
Dec 15 18:20:23 Hydrogen modem-manager: (ttyUSB4): probe requested by plugin 'ZTE'
Dec 15 18:20:28 Hydrogen modem-manager: (ttyUSB6): probe requested by plugin 'ZTE'
Dec 15 18:20:28 Hydrogen modem-manager: (ttyUSB7): probe requested by plugin 'ZTE'
Dec 15 18:20:51 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB5
Dec 15 18:20:51 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB6
Dec 15 18:21:41 Hydrogen modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB4
Dec 15 18:47:04 Hydrogen modem-manager: Loaded plugin ZTE
Dec 15 23:00:18 Hydrogen modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Dec 15 23:00:23 Hydrogen kernel: [  321.253077] scsi 3:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 15 23:00:33 Hydrogen modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Dec 15 23:00:38 Hydrogen modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Dec 15 23:00:47 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 16 09:30:17 Hydrogen kernel: [  533.583695] scsi 6:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 16 09:30:17 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Dec 16 09:30:23 Hydrogen kernel: [  539.539655] scsi 7:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Dec 16 09:30:33 Hydrogen modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
```
And ls -al /dev/serial/by-id/* returns:
```
lrwxrwxrwx 1 root root 13 2010-12-16 09:30 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-12-16 09:30 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-12-16 09:30 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if03-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-12-16 09:30 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if04-port0 -> ../../ttyUSB3
```

---

### Post by alexfish on 2010-12-15
Hi

the log file does not show the consistancy I have seen in past for this type of device
seems the device is taking a long time to settle; and note the ttyUSB3 ; inquire , and response  ::: MMC STORAGE . nor do I see any activity of the usb_modeswitch
in Ubuntu 10.10 this is now part of the distro , is it  installed

Can try these procedures:

plug the device in prior to boot:

after boot wait for the system to settle , possible wait for up to 5mins , see if the connection appears in Network Manager
if it appears in NM try the connection , at same time monitor the events in the Log file viewer messages , see which tty port
is connecting.

if not connecting or not seen try these from the terminal

Codes:

[COLOR=Blue]sudo su[/COLOR]

[COLOR=Blue]killall modem-manager[/COLOR]

[COLOR=Blue]modprobe -r option[/COLOR]

;;;;;;;;;wait about 5 seconds then

[COLOR=Blue]modprobe option[/COLOR]

[COLOR=Blue]exit[/COLOR]

then close the terminal

wait and see if the connection appears in the Network Manager; if so try the connection

also if your connection is 3g can also try this software called Sakis3g

details of how to install sakis3g: see post #10

 [How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")
 
look at the menu options of sakis3g in regards to preparation and registering

can you confirm this device works and is stable on a widows system

alexfish

---

