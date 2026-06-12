---
title: "VMC K3806 not detected - Custom settings"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by mj519078 on 2011-08-19
I recently bought one K3806 Vodafone Mobile Broadband usb stick.

My pc is a Dell Latidude D620 notebook (Bios A08) running Ubuntu 11.04 (Natty Narwhal).

I downloaded (from Betavine) and installed without any error/warning the 3 packages ozerocdoff, usb-medeswitch and vodafone-mobile-connect.

Then I plug the K3806 in one usb slot.

The mount -v command produces following output :

/dev/sr1 on /media/10.1.108_RP154 type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)

The mount point directory contains following files :

-r-------- 1 mj519078 mj519078      128 2011-02-02 03:13 autorun.inf
-r-------- 1 mj519078 mj519078 48765870 2011-02-02 02:47 helper.exe
-r-------- 1 mj519078 mj519078   274432 2010-12-02 14:17 setup_vmb_lite.exe
-r-------- 1 mj519078 mj519078     5515 2010-12-02 14:17 version.ini

The lsusb command produces :

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12d1:14ae Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The usb-devices command produces :

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14ae Rev=01.02
S:  Manufacturer=Vodafone Group (Huawei)
S:  Product=Vodafone Mobile Broadband (Huawei)
S:  SerialNumber=0
C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

When I execute the vodafone-mobile-connect-card-driver-for-linux command, a popup windows appears saying :

 Select a device
  Known devices           No known devices found
  Custom device settings
     Device type          Serial is the only choice
     Data port device     Where can I find this value ?
     Control port device  Where can I find this value ?
     Speed connection     115200 (no other choice)

The LED indicator on the stick flashes green twice every 3 seconds, indicating a GPRS network has been detected.

In short, as the device is not known, I have to customize the settings.
I do not know what the data port is nor the control port.

Could anyone help or refer to some doc/faq ?

Thank you

---

### Post by sampont on 2011-08-24
I have the same hardware and the same problem. I have noticed that Ubuntu don't ask the PIN code but hardware is well reconized .

My solution is to remove the PIN code of the SIM card. After that the connection can be made easily.

---

### Post by Notuob on 2012-06-13
Thanks for the solution 
My  K3806 usb work fine

---

