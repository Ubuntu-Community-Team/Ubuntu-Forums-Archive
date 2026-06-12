---
title: "Vodafone USB (K 3805-z)"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by buteobuteo on 2011-01-17
With Lynx I plugged in the Vodafone USB dongle and it just asked "What network" and "Acount or payasyougo" and then connected.  However Meerkat seems to ignore the dongle except to show the windows loader files on the desktop.  How do you connect with Meerkat please?

---

### Post by alexfish on 2011-01-17
Hi

can see if this helps

[**How to check for the option drive****r and modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

**Updated to Notify:**

[B]Unless your device looks like the results of the usb-devices at Post #3 , and if your device of Vodafone origin , assume there will be a no fix , following this thread
[/B] 
regards
alexfish

---

### Post by buteobuteo on 2011-01-18
Tried that, this is the output.  Problem may be it doesn't appear to be a HUAWEI device.  Just remembered that I lost the original one and this is a replacement.  If this is the case I presume I have to wait for drivers to be written.  Thank you for your time.
 
 ```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-27-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1002 Rev=00.01
S:  Manufacturer=Vodafone
S:  Product=K3805-z
S:  SerialNumber=1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E
C:  #Ifs= 9 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 5 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 7 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=058f ProdID=6335 Rev=01.05
S:  Manufacturer=Generic
S:  Product=Mass Storage Device
S:  SerialNumber=058F63356336
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=507b Rev=12.22
S:  Manufacturer=GenesysLogic Technology Co., Ltd.
S:  Product=USB2.0 UVC PC Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-27-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0b05 ProdID=b700 Rev=02.41
S:  Manufacturer=Broadcom Corp
S:  Product=BT-253
S:  SerialNumber=002243E19B1E
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)
[EMAIL="vic@UbuntuBabyAsus:~$"]vic@UbuntuBabyAsus:~$[/EMAIL] ^C
[EMAIL="vic@UbuntuBabyAsus:~$"]vic@UbuntuBabyAsus:~$[/EMAIL] 

```

---

### Post by alexfish on 2011-01-18
oowee, 

looks like a 4g device , verizon have similar device

example of verizon device which can connect/ but only 3g at present

T: Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#= 6 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=02(commc) Sub=02 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=1004 ProdID=61aa Rev=01.00
S: Manufacturer=LG ELECTRONICSInc
S: Product=LG UDC-AHB Subsystem
C: #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=400mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I: If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I: If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I: If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

so should be able to connect if can extract details

but I do know the verizon device has to be configured in windows first,

what does the demesage show

[FONT=Verdana][SIZE=1]**Code:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]dmesg | grep -e "modem" -e "tty"

can also have a prowl around the usb-devices files and see which  directories in "some times the port name is listed as a directory" IE tty*

exomple of where the directories are

/sys/bus/usb/devices/1-3/1-3:1.0

although your system search all [/SIZE][/FONT][FONT=Verdana][SIZE=2]/sys/bus/usb/devices/*-*/*:*[/SIZE][/FONT]

as quick guide can try : edit the usb* to suite

code:
ls -al /sys/bus/usb/devices/usb1/*/*/*

and pick the important bits like 
drwxr-xr-x 4 root root    0 2011-01-18 13:18 tty*

Added can also try this command

Code:

ls -al /dev/serial/by-id


[FONT=Verdana][SIZE=2] 
alexfish
[/SIZE][/FONT]

---

### Post by buteobuteo on 2011-01-19
Is the following of any use?  I'm am not a complete beginner but am not very familiar with Linux

```
vic@UbuntuBabyAsus:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
vic@UbuntuBabyAsus:~$ ls -al /dev/serial/by-id
ls: cannot access /dev/serial/by-id: No such file or directory
vic@UbuntuBabyAsus:~$ 
vic@UbuntuBabyAsus:~$ /sys/bus/usb/devices/*-*/*:*
bash: /sys/bus/usb/devices/1-2/1-2:1.0: is a directory
The code      ls -al /sys/bus/usb/devices/usb1/*/*/*   produced so much this was all I could copy and paste

-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:50 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:50 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:50 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:50 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 18:50 serial
-r--r--r-- 1 root root  4096 2011-01-19 18:50 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:50 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:50 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb1/1-5:
total 0
drwxr-xr-x 5 root root     0 2011-01-19 18:38 .
drwxr-xr-x 8 root root     0 2011-01-19 18:50 ..
drwxr-xr-x 6 root root     0 2011-01-19 18:38 1-5:1.0
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 authorized
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bcdDevice
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 bConfigurationValue
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bDeviceProtocol
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceSubClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPower
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumConfigurations
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumInterfaces
-r--r--r-- 1 root root  4096 2011-01-19 20:25 busnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 configuration
-r--r--r-- 1 root root 65553 2011-01-19 18:38 descriptors
-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:38 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:38 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 18:38 serial
-r--r--r-- 1 root root  4096 2011-01-19 18:38 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:38 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb1/1-8:
total 0
drwxr-xr-x 6 root root     0 2011-01-19 18:38 .
drwxr-xr-x 8 root root     0 2011-01-19 18:50 ..
drwxr-xr-x 6 root root     0 2011-01-19 18:38 1-8:1.0
drwxr-xr-x 3 root root     0 2011-01-19 18:38 1-8:1.1
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 authorized
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bcdDevice
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 bConfigurationValue
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bDeviceProtocol
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bDeviceSubClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPower
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumConfigurations
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumInterfaces
-r--r--r-- 1 root root  4096 2011-01-19 20:25 busnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 configuration
-r--r--r-- 1 root root 65553 2011-01-19 18:38 descriptors
-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:38 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:38 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 20:25 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:38 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb1/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 8 root root    0 2011-01-19 18:50 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb1/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 8 root root    0 2011-01-19 18:50 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/driver/usb2/2-0:1.0:
total 0
drwxr-xr-x 4 root root    0 2011-01-19 18:38 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bAlternateSetting
-r--r--r-- 1 root root 4096 2011-01-19 18:38 bInterfaceClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceNumber
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bNumEndpoints
lrwxrwxrwx 1 root root    0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/hub
drwxr-xr-x 3 root root    0 2011-01-19 20:25 ep_81
-r--r--r-- 1 root root 4096 2011-01-19 20:25 modalias
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
lrwxrwxrwx 1 root root    0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-r--r--r-- 1 root root 4096 2011-01-19 20:25 supports_autosuspend
-rw-r--r-- 1 root root 4096 2011-01-19 18:38 uevent

/sys/bus/usb/devices/usb1/driver/usb2/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb2/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/driver/usb3/3-0:1.0:
total 0
drwxr-xr-x 4 root root    0 2011-01-19 18:38 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bAlternateSetting
-r--r--r-- 1 root root 4096 2011-01-19 18:38 bInterfaceClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceNumber
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bNumEndpoints
lrwxrwxrwx 1 root root    0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/hub
drwxr-xr-x 3 root root    0 2011-01-19 20:25 ep_81
-r--r--r-- 1 root root 4096 2011-01-19 20:25 modalias
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
lrwxrwxrwx 1 root root    0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-r--r--r-- 1 root root 4096 2011-01-19 20:25 supports_autosuspend
-rw-r--r-- 1 root root 4096 2011-01-19 18:38 uevent

/sys/bus/usb/devices/usb1/driver/usb3/3-1:
total 0
drwxr-xr-x 5 root root     0 2011-01-19 18:38 .
drwxr-xr-x 6 root root     0 2011-01-19 18:38 ..
drwxr-xr-x 6 root root     0 2011-01-19 18:38 3-1:1.0
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 authorized
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bcdDevice
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 bConfigurationValue
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bDeviceProtocol
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceSubClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPower
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumConfigurations
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumInterfaces
-r--r--r-- 1 root root  4096 2011-01-19 20:25 busnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 configuration
-r--r--r-- 1 root root 65553 2011-01-19 18:38 descriptors
-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:38 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:38 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 20:25 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:38 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb3/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb3/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/driver/usb4/4-0:1.0:
total 0
drwxr-xr-x 4 root root    0 2011-01-19 18:38 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bAlternateSetting
-r--r--r-- 1 root root 4096 2011-01-19 18:38 bInterfaceClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceNumber
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bNumEndpoints
lrwxrwxrwx 1 root root    0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/hub
drwxr-xr-x 3 root root    0 2011-01-19 20:25 ep_81
-r--r--r-- 1 root root 4096 2011-01-19 20:25 modalias
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
lrwxrwxrwx 1 root root    0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-r--r--r-- 1 root root 4096 2011-01-19 20:25 supports_autosuspend
-rw-r--r-- 1 root root 4096 2011-01-19 18:38 uevent

/sys/bus/usb/devices/usb1/driver/usb4/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb4/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/driver/usb5/5-0:1.0:
total 0
drwxr-xr-x 4 root root    0 2011-01-19 18:38 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bAlternateSetting
-r--r--r-- 1 root root 4096 2011-01-19 18:38 bInterfaceClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceNumber
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bNumEndpoints
lrwxrwxrwx 1 root root    0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/hub
drwxr-xr-x 3 root root    0 2011-01-19 20:25 ep_81
-r--r--r-- 1 root root 4096 2011-01-19 20:25 modalias
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
lrwxrwxrwx 1 root root    0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-r--r--r-- 1 root root 4096 2011-01-19 20:25 supports_autosuspend
-rw-r--r-- 1 root root 4096 2011-01-19 18:38 uevent

/sys/bus/usb/devices/usb1/driver/usb5/5-1:
total 0
drwxr-xr-x 8 root root     0 2011-01-19 18:38 .
drwxr-xr-x 6 root root     0 2011-01-19 18:38 ..
drwxr-xr-x 7 root root     0 2011-01-19 18:38 5-1:1.0
drwxr-xr-x 5 root root     0 2011-01-19 18:38 5-1:1.1
drwxr-xr-x 5 root root     0 2011-01-19 18:38 5-1:1.2
drwxr-xr-x 3 root root     0 2011-01-19 18:38 5-1:1.3
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 authorized
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bcdDevice
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 bConfigurationValue
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceClass
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceProtocol
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceSubClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPower
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumConfigurations
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumInterfaces
-r--r--r-- 1 root root  4096 2011-01-19 20:25 busnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 configuration
-r--r--r-- 1 root root 65553 2011-01-19 18:38 descriptors
-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:38 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:38 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 18:38 serial
-r--r--r-- 1 root root  4096 2011-01-19 20:25 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:38 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb5/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb5/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/subsystem/drivers/btusb:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 5-1:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 5-1:1.1 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/btusb
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/hiddev:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usbhid
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/hub:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 2-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 3-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 4-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 5-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usbcore
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/usb:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-2 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-2
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-5 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-5
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-8 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-8
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 3-1 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3/3-1
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 5-1 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-1
--w-------  1 root root 4096 2011-01-19 20:25 bind
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb1 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb2 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb3 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb4 -> ../../../../devices/pci0000:00/0000:00:1d.2/usb4
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb5 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5

/sys/bus/usb/devices/usb1/subsystem/drivers/usbfs:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usbcore
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/usbhid:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 3-1:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usbhid
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/usb-storage:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-2:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-5:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usb_storage
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/uvcvideo:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-8:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-8:1.1 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.1
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/uvcvideo
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind
vic@UbuntuBabyAsus:~$
```

---

### Post by buteobuteo on 2011-01-19
Is the following of any use?  I'm am not a complete beginner but am not very familiar with Linux

vic@UbuntuBabyAsus:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
vic@UbuntuBabyAsus:~$ ls -al /dev/serial/by-id
ls: cannot access /dev/serial/by-id: No such file or directory
vic@UbuntuBabyAsus:~$ 
vic@UbuntuBabyAsus:~$ /sys/bus/usb/devices/*-*/*:*
bash: /sys/bus/usb/devices/1-2/1-2:1.0: is a directory
The code      ls -al /sys/bus/usb/devices/usb1/*/*/*   produced so much this was all I could copy and paste

-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:50 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:50 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:50 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:50 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 18:50 serial
-r--r--r-- 1 root root  4096 2011-01-19 18:50 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:50 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:50 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb1/1-5:
total 0
drwxr-xr-x 5 root root     0 2011-01-19 18:38 .
drwxr-xr-x 8 root root     0 2011-01-19 18:50 ..
drwxr-xr-x 6 root root     0 2011-01-19 18:38 1-5:1.0
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 authorized
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bcdDevice
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 bConfigurationValue
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bDeviceProtocol
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceSubClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPower
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumConfigurations
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumInterfaces
-r--r--r-- 1 root root  4096 2011-01-19 20:25 busnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 configuration
-r--r--r-- 1 root root 65553 2011-01-19 18:38 descriptors
-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:38 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:38 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 18:38 serial
-r--r--r-- 1 root root  4096 2011-01-19 18:38 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:38 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb1/1-8:
total 0
drwxr-xr-x 6 root root     0 2011-01-19 18:38 .
drwxr-xr-x 8 root root     0 2011-01-19 18:50 ..
drwxr-xr-x 6 root root     0 2011-01-19 18:38 1-8:1.0
drwxr-xr-x 3 root root     0 2011-01-19 18:38 1-8:1.1
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 authorized
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bcdDevice
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 bConfigurationValue
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bDeviceProtocol
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bDeviceSubClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPower
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumConfigurations
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumInterfaces
-r--r--r-- 1 root root  4096 2011-01-19 20:25 busnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 configuration
-r--r--r-- 1 root root 65553 2011-01-19 18:38 descriptors
-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:38 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:38 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 20:25 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:38 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb1/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 8 root root    0 2011-01-19 18:50 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb1/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 8 root root    0 2011-01-19 18:50 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/driver/usb2/2-0:1.0:
total 0
drwxr-xr-x 4 root root    0 2011-01-19 18:38 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bAlternateSetting
-r--r--r-- 1 root root 4096 2011-01-19 18:38 bInterfaceClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceNumber
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bNumEndpoints
lrwxrwxrwx 1 root root    0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/hub
drwxr-xr-x 3 root root    0 2011-01-19 20:25 ep_81
-r--r--r-- 1 root root 4096 2011-01-19 20:25 modalias
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
lrwxrwxrwx 1 root root    0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-r--r--r-- 1 root root 4096 2011-01-19 20:25 supports_autosuspend
-rw-r--r-- 1 root root 4096 2011-01-19 18:38 uevent

/sys/bus/usb/devices/usb1/driver/usb2/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb2/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/driver/usb3/3-0:1.0:
total 0
drwxr-xr-x 4 root root    0 2011-01-19 18:38 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bAlternateSetting
-r--r--r-- 1 root root 4096 2011-01-19 18:38 bInterfaceClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceNumber
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bNumEndpoints
lrwxrwxrwx 1 root root    0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/hub
drwxr-xr-x 3 root root    0 2011-01-19 20:25 ep_81
-r--r--r-- 1 root root 4096 2011-01-19 20:25 modalias
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
lrwxrwxrwx 1 root root    0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-r--r--r-- 1 root root 4096 2011-01-19 20:25 supports_autosuspend
-rw-r--r-- 1 root root 4096 2011-01-19 18:38 uevent

/sys/bus/usb/devices/usb1/driver/usb3/3-1:
total 0
drwxr-xr-x 5 root root     0 2011-01-19 18:38 .
drwxr-xr-x 6 root root     0 2011-01-19 18:38 ..
drwxr-xr-x 6 root root     0 2011-01-19 18:38 3-1:1.0
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 authorized
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bcdDevice
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 bConfigurationValue
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bDeviceProtocol
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceSubClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPower
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumConfigurations
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumInterfaces
-r--r--r-- 1 root root  4096 2011-01-19 20:25 busnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 configuration
-r--r--r-- 1 root root 65553 2011-01-19 18:38 descriptors
-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:38 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:38 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 20:25 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:38 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb3/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb3/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/driver/usb4/4-0:1.0:
total 0
drwxr-xr-x 4 root root    0 2011-01-19 18:38 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bAlternateSetting
-r--r--r-- 1 root root 4096 2011-01-19 18:38 bInterfaceClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceNumber
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bNumEndpoints
lrwxrwxrwx 1 root root    0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/hub
drwxr-xr-x 3 root root    0 2011-01-19 20:25 ep_81
-r--r--r-- 1 root root 4096 2011-01-19 20:25 modalias
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
lrwxrwxrwx 1 root root    0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-r--r--r-- 1 root root 4096 2011-01-19 20:25 supports_autosuspend
-rw-r--r-- 1 root root 4096 2011-01-19 18:38 uevent

/sys/bus/usb/devices/usb1/driver/usb4/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb4/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 5 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/driver/usb5/5-0:1.0:
total 0
drwxr-xr-x 4 root root    0 2011-01-19 18:38 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bAlternateSetting
-r--r--r-- 1 root root 4096 2011-01-19 18:38 bInterfaceClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceNumber
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceProtocol
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterfaceSubClass
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bNumEndpoints
lrwxrwxrwx 1 root root    0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/hub
drwxr-xr-x 3 root root    0 2011-01-19 20:25 ep_81
-r--r--r-- 1 root root 4096 2011-01-19 20:25 modalias
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
lrwxrwxrwx 1 root root    0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-r--r--r-- 1 root root 4096 2011-01-19 20:25 supports_autosuspend
-rw-r--r-- 1 root root 4096 2011-01-19 18:38 uevent

/sys/bus/usb/devices/usb1/driver/usb5/5-1:
total 0
drwxr-xr-x 8 root root     0 2011-01-19 18:38 .
drwxr-xr-x 6 root root     0 2011-01-19 18:38 ..
drwxr-xr-x 7 root root     0 2011-01-19 18:38 5-1:1.0
drwxr-xr-x 5 root root     0 2011-01-19 18:38 5-1:1.1
drwxr-xr-x 5 root root     0 2011-01-19 18:38 5-1:1.2
drwxr-xr-x 3 root root     0 2011-01-19 18:38 5-1:1.3
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 authorized
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bcdDevice
-rw-r--r-- 1 root root  4096 2011-01-19 20:25 bConfigurationValue
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceClass
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceProtocol
-r--r--r-- 1 root root  4096 2011-01-19 18:38 bDeviceSubClass
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPacketSize0
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bMaxPower
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumConfigurations
-r--r--r-- 1 root root  4096 2011-01-19 20:25 bNumInterfaces
-r--r--r-- 1 root root  4096 2011-01-19 20:25 busnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 configuration
-r--r--r-- 1 root root 65553 2011-01-19 18:38 descriptors
-r--r--r-- 1 root root  4096 2011-01-19 20:25 dev
-r--r--r-- 1 root root  4096 2011-01-19 20:25 devnum
lrwxrwxrwx 1 root root     0 2011-01-19 20:25 driver -> ../../../../../bus/usb/drivers/usb
drwxr-xr-x 3 root root     0 2011-01-19 20:25 ep_00
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idProduct
-r--r--r-- 1 root root  4096 2011-01-19 18:38 idVendor
-r--r--r-- 1 root root  4096 2011-01-19 18:38 manufacturer
-r--r--r-- 1 root root  4096 2011-01-19 20:25 maxchild
drwxr-xr-x 2 root root     0 2011-01-19 20:25 power
-r--r--r-- 1 root root  4096 2011-01-19 18:38 product
-r--r--r-- 1 root root  4096 2011-01-19 20:25 quirks
-r--r--r-- 1 root root  4096 2011-01-19 18:38 serial
-r--r--r-- 1 root root  4096 2011-01-19 20:25 speed
lrwxrwxrwx 1 root root     0 2011-01-19 18:38 subsystem -> ../../../../../bus/usb
-rw-r--r-- 1 root root  4096 2011-01-19 18:38 uevent
-r--r--r-- 1 root root  4096 2011-01-19 20:25 urbnum
-r--r--r-- 1 root root  4096 2011-01-19 20:25 version

/sys/bus/usb/devices/usb1/driver/usb5/ep_00:
total 0
drwxr-xr-x 3 root root    0 2011-01-19 20:25 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bEndpointAddress
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bInterval
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bLength
-r--r--r-- 1 root root 4096 2011-01-19 20:25 bmAttributes
-r--r--r-- 1 root root 4096 2011-01-19 20:25 direction
-r--r--r-- 1 root root 4096 2011-01-19 20:25 interval
drwxr-xr-x 2 root root    0 2011-01-19 20:25 power
-r--r--r-- 1 root root 4096 2011-01-19 20:25 type
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 uevent
-r--r--r-- 1 root root 4096 2011-01-19 20:25 wMaxPacketSize

/sys/bus/usb/devices/usb1/driver/usb5/power:
total 0
drwxr-xr-x 2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 6 root root    0 2011-01-19 18:38 ..
-r--r--r-- 1 root root 4096 2011-01-19 20:25 active_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 autosuspend
-r--r--r-- 1 root root 4096 2011-01-19 20:25 connected_duration
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 level
-rw-r--r-- 1 root root 4096 2011-01-19 20:25 wakeup

/sys/bus/usb/devices/usb1/subsystem/drivers/btusb:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 5-1:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 5-1:1.1 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.1
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/btusb
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/hiddev:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usbhid
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/hub:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 2-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 3-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 4-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 5-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usbcore
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/usb:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-2 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-2
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-5 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-5
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-8 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-8
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 3-1 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3/3-1
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 5-1 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-1
--w-------  1 root root 4096 2011-01-19 20:25 bind
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb1 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb2 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb3 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb4 -> ../../../../devices/pci0000:00/0000:00:1d.2/usb4
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 usb5 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5

/sys/bus/usb/devices/usb1/subsystem/drivers/usbfs:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usbcore
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/usbhid:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 3-1:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usbhid
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/usb-storage:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-2:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-5:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/usb_storage
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind

/sys/bus/usb/devices/usb1/subsystem/drivers/uvcvideo:
total 0
drwxr-xr-x  2 root root    0 2011-01-19 20:25 .
drwxr-xr-x 10 root root    0 2011-01-19 18:38 ..
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-8:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 1-8:1.1 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.1
--w-------  1 root root 4096 2011-01-19 20:25 bind
lrwxrwxrwx  1 root root    0 2011-01-19 20:25 module -> ../../../../module/uvcvideo
--w-------  1 root root 4096 2011-01-19 20:25 new_id
--w-------  1 root root 4096 2011-01-19 20:25 uevent
--w-------  1 root root 4096 2011-01-19 20:25 unbind
vic@UbuntuBabyAsus:~$

---

### Post by buteobuteo on 2011-01-19
Is the following of any use?  I'm am not a complete beginner but am not very familiar with Linux

vic@UbuntuBabyAsus:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
vic@UbuntuBabyAsus:~$ ls -al /dev/serial/by-id
ls: cannot access /dev/serial/by-id: No such file or directory
vic@UbuntuBabyAsus:~$ 
vic@UbuntuBabyAsus:~$ /sys/bus/usb/devices/*-*/*:*
bash: /sys/bus/usb/devices/1-2/1-2:1.0: is a directory
The code      ls -al /sys/bus/usb/devices/usb1/*/*/*   produced so much that it wouldn't upload this reply.  Is it possible to redirect to file if the output would be useful?

---

### Post by buteobuteo on 2011-01-19
> **alexfish said:**
> oowee, 

looks like a 4g device , verizon have similar device

example of verizon device which can connect/ but only 3g at present

T: Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#= 6 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=02(commc) Sub=02 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=1004 ProdID=61aa Rev=01.00
S: Manufacturer=LG ELECTRONICSInc
S: Product=LG UDC-AHB Subsystem
C: #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=400mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I: If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I: If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I: If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

so should be able to connect if can extract details

but I do know the verizon device has to be configured in windows first,

what does the demesage show

[FONT=Verdana][SIZE=1]**Code:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]dmesg | grep -e "modem" -e "tty"

can also have a prowl around the usb-devices files and see which  directories in "some times the port name is listed as a directory" IE tty*

exomple of where the directories are

/sys/bus/usb/devices/1-3/1-3:1.0

although your system search all [/SIZE][/FONT][FONT=Verdana][SIZE=2]/sys/bus/usb/devices/*-*/*:*[/SIZE][/FONT]

as quick guide can try : edit the usb* to suite

code:
ls -al /sys/bus/usb/devices/usb1/*/*/*

and pick the important bits like 
drwxr-xr-x 4 root root    0 2011-01-18 13:18 tty*

Added can also try this command

Code:

ls -al /dev/serial/by-id


[FONT=Verdana][SIZE=2] 
alexfish
[/SIZE][/FONT]
Is the following of any use?  I'm am not a complete beginner but am not very familiar with Linux

vic@UbuntuBabyAsus:~$ dmesg | grep -e "modem" -e "tty"
[    0.000000] console [tty0] enabled
vic@UbuntuBabyAsus:~$ ls -al /dev/serial/by-id
ls: cannot access /dev/serial/by-id: No such file or directory
vic@UbuntuBabyAsus:~$ 
vic@UbuntuBabyAsus:~$ /sys/bus/usb/devices/*-*/*:*
bash: /sys/bus/usb/devices/1-2/1-2:1.0: is a directory
The  code      ls -al /sys/bus/usb/devices/usb1/*/*/*   produced so much  that it wouldn't upload this reply.  Is it possible to redirect to file  if the output would be useful?

---

### Post by alexfish on 2011-01-21
Hi

there is enough info posted , on the previous 
however

can try this command from the terminal (use copy and paste)

Code:

udevadm info --export-db > `pwd`/vodafoneinfo

the file should be in your home directory

have a look through the info ; locate the bits that relate to the modem / don't post the whole file
example might see something like /dev/ttyACM* or device dev

the file will be quite long , 

alexfish

---

### Post by buteobuteo on 2011-01-21
> **alexfish said:**
> Hi

there is enough info posted , on the previous 
however

can try this command from the terminal (use copy and paste)

Code:

udevadm info --export-db > `pwd`/vodafoneinfo

the file should be in your home directory

have a look through the info ; locate the bits that relate to the modem / don't post the whole file
example might see something like /dev/ttyACM* or device dev

the file will be quite long , 

alexfish

Not sure what you're looking for so have cut and pasted anything with tty in it.

```
P: /devices/platform/serial8250/tty/ttyS0
N: ttyS0
S: char/4:64
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS0
E: MAJOR=4
E: MINOR=64
E: DEVNAME=/dev/ttyS0
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:64

P: /devices/platform/serial8250/tty/ttyS1
N: ttyS1
S: char/4:65
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
E: MAJOR=4
E: MINOR=65
E: DEVNAME=/dev/ttyS1
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:65

P: /devices/platform/serial8250/tty/ttyS2
N: ttyS2
S: char/4:66
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
E: MAJOR=4
E: MINOR=66
E: DEVNAME=/dev/ttyS2
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:66

P: /devices/platform/serial8250/tty/ttyS3
N: ttyS3
S: char/4:67
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
E: MAJOR=4
E: MINOR=67
E: DEVNAME=/dev/ttyS3
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:67

```

```
P: /devices/virtual/tty/console
N: console
S: char/5:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/console
E: MAJOR=5
E: MINOR=1
E: DEVNAME=/dev/console
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/5:1

P: /devices/virtual/tty/ptmx
N: ptmx
S: char/5:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/ptmx
E: MAJOR=5
E: MINOR=2
E: DEVNAME=/dev/ptmx
E: DEVMODE=0666
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/5:2

P: /devices/virtual/tty/tty
N: tty
S: char/5:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty
E: MAJOR=5
E: MINOR=0
E: DEVNAME=/dev/tty
E: DEVMODE=0666
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/5:0

P: /devices/virtual/tty/tty0
N: tty0
S: char/4:0
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty0
E: MAJOR=4
E: MINOR=0
E: DEVNAME=/dev/tty0
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:0

P: /devices/virtual/tty/tty1
N: tty1
S: char/4:1
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty1
E: MAJOR=4
E: MINOR=1
E: DEVNAME=/dev/tty1
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:1

P: /devices/virtual/tty/tty10
N: tty10
S: char/4:10
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty10
E: MAJOR=4
E: MINOR=10
E: DEVNAME=/dev/tty10
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:10

P: /devices/virtual/tty/tty11
N: tty11
S: char/4:11
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty11
E: MAJOR=4
E: MINOR=11
E: DEVNAME=/dev/tty11
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:11

P: /devices/virtual/tty/tty12
N: tty12
S: char/4:12
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty12
E: MAJOR=4
E: MINOR=12
E: DEVNAME=/dev/tty12
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:12

P: /devices/virtual/tty/tty13
N: tty13
S: char/4:13
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty13
E: MAJOR=4
E: MINOR=13
E: DEVNAME=/dev/tty13
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:13

P: /devices/virtual/tty/tty14
N: tty14
S: char/4:14
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty14
E: MAJOR=4
E: MINOR=14
E: DEVNAME=/dev/tty14
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:14

P: /devices/virtual/tty/tty15
N: tty15
S: char/4:15
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty15
E: MAJOR=4
E: MINOR=15
E: DEVNAME=/dev/tty15
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:15

P: /devices/virtual/tty/tty16
N: tty16
S: char/4:16
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty16
E: MAJOR=4
E: MINOR=16
E: DEVNAME=/dev/tty16
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:16

P: /devices/virtual/tty/tty17
N: tty17
S: char/4:17
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty17
E: MAJOR=4
E: MINOR=17
E: DEVNAME=/dev/tty17
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:17

P: /devices/virtual/tty/tty18
N: tty18
S: char/4:18
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty18
E: MAJOR=4
E: MINOR=18
E: DEVNAME=/dev/tty18
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:18

P: /devices/virtual/tty/tty19
N: tty19
S: char/4:19
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty19
E: MAJOR=4
E: MINOR=19
E: DEVNAME=/dev/tty19
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:19

P: /devices/virtual/tty/tty2
N: tty2
S: char/4:2
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty2
E: MAJOR=4
E: MINOR=2
E: DEVNAME=/dev/tty2
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:2

P: /devices/virtual/tty/tty20
N: tty20
S: char/4:20
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty20
E: MAJOR=4
E: MINOR=20
E: DEVNAME=/dev/tty20
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:20

P: /devices/virtual/tty/tty21
N: tty21
S: char/4:21
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty21
E: MAJOR=4
E: MINOR=21
E: DEVNAME=/dev/tty21
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:21

P: /devices/virtual/tty/tty22
N: tty22
S: char/4:22
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty22
E: MAJOR=4
E: MINOR=22
E: DEVNAME=/dev/tty22
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:22

P: /devices/virtual/tty/tty23
N: tty23
S: char/4:23
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty23
E: MAJOR=4
E: MINOR=23
E: DEVNAME=/dev/tty23
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:23

P: /devices/virtual/tty/tty24
N: tty24
S: char/4:24
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty24
E: MAJOR=4
E: MINOR=24
E: DEVNAME=/dev/tty24
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:24

P: /devices/virtual/tty/tty25
N: tty25
S: char/4:25
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty25
E: MAJOR=4
E: MINOR=25
E: DEVNAME=/dev/tty25
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:25

P: /devices/virtual/tty/tty26
N: tty26
S: char/4:26
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty26
E: MAJOR=4
E: MINOR=26
E: DEVNAME=/dev/tty26
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:26

P: /devices/virtual/tty/tty27
N: tty27
S: char/4:27
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty27
E: MAJOR=4
E: MINOR=27
E: DEVNAME=/dev/tty27
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:27

P: /devices/virtual/tty/tty28
N: tty28
S: char/4:28
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty28
E: MAJOR=4
E: MINOR=28
E: DEVNAME=/dev/tty28
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:28

P: /devices/virtual/tty/tty29
N: tty29
S: char/4:29
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty29
E: MAJOR=4
E: MINOR=29
E: DEVNAME=/dev/tty29
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:29

P: /devices/virtual/tty/tty3
N: tty3
S: char/4:3
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty3
E: MAJOR=4
E: MINOR=3
E: DEVNAME=/dev/tty3
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:3

P: /devices/virtual/tty/tty30
N: tty30
S: char/4:30
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty30
E: MAJOR=4
E: MINOR=30
E: DEVNAME=/dev/tty30
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:30

P: /devices/virtual/tty/tty31
N: tty31
S: char/4:31
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty31
E: MAJOR=4
E: MINOR=31
E: DEVNAME=/dev/tty31
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:31

P: /devices/virtual/tty/tty32
N: tty32
S: char/4:32
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty32
E: MAJOR=4
E: MINOR=32
E: DEVNAME=/dev/tty32
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:32

P: /devices/virtual/tty/tty33
N: tty33
S: char/4:33
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty33
E: MAJOR=4
E: MINOR=33
E: DEVNAME=/dev/tty33
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:33

P: /devices/virtual/tty/tty34
N: tty34
S: char/4:34
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty34
E: MAJOR=4
E: MINOR=34
E: DEVNAME=/dev/tty34
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:34

P: /devices/virtual/tty/tty35
N: tty35
S: char/4:35
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty35
E: MAJOR=4
E: MINOR=35
E: DEVNAME=/dev/tty35
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:35

P: /devices/virtual/tty/tty36
N: tty36
S: char/4:36
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty36
E: MAJOR=4
E: MINOR=36
E: DEVNAME=/dev/tty36
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:36

P: /devices/virtual/tty/tty37
N: tty37
S: char/4:37
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty37
E: MAJOR=4
E: MINOR=37
E: DEVNAME=/dev/tty37
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:37

P: /devices/virtual/tty/tty38
N: tty38
S: char/4:38
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty38
E: MAJOR=4
E: MINOR=38
E: DEVNAME=/dev/tty38
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:38

P: /devices/virtual/tty/tty39
N: tty39
S: char/4:39
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty39
E: MAJOR=4
E: MINOR=39
E: DEVNAME=/dev/tty39
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:39

P: /devices/virtual/tty/tty4
N: tty4
S: char/4:4
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty4
E: MAJOR=4
E: MINOR=4
E: DEVNAME=/dev/tty4
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:4

P: /devices/virtual/tty/tty40
N: tty40
S: char/4:40
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty40
E: MAJOR=4
E: MINOR=40
E: DEVNAME=/dev/tty40
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:40

P: /devices/virtual/tty/tty41
N: tty41
S: char/4:41
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty41
E: MAJOR=4
E: MINOR=41
E: DEVNAME=/dev/tty41
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:41

P: /devices/virtual/tty/tty42
N: tty42
S: char/4:42
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty42
E: MAJOR=4
E: MINOR=42
E: DEVNAME=/dev/tty42
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:42

P: /devices/virtual/tty/tty43
N: tty43
S: char/4:43
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty43
E: MAJOR=4
E: MINOR=43
E: DEVNAME=/dev/tty43
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:43

P: /devices/virtual/tty/tty44
N: tty44
S: char/4:44
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty44
E: MAJOR=4
E: MINOR=44
E: DEVNAME=/dev/tty44
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:44

P: /devices/virtual/tty/tty45
N: tty45
S: char/4:45
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty45
E: MAJOR=4
E: MINOR=45
E: DEVNAME=/dev/tty45
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:45

P: /devices/virtual/tty/tty46
N: tty46
S: char/4:46
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty46
E: MAJOR=4
E: MINOR=46
E: DEVNAME=/dev/tty46
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:46

P: /devices/virtual/tty/tty47
N: tty47
S: char/4:47
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty47
E: MAJOR=4
E: MINOR=47
E: DEVNAME=/dev/tty47
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:47

P: /devices/virtual/tty/tty48
N: tty48
S: char/4:48
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty48
E: MAJOR=4
E: MINOR=48
E: DEVNAME=/dev/tty48
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:48

P: /devices/virtual/tty/tty49
N: tty49
S: char/4:49
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty49
E: MAJOR=4
E: MINOR=49
E: DEVNAME=/dev/tty49
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:49

P: /devices/virtual/tty/tty5
N: tty5
S: char/4:5
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty5
E: MAJOR=4
E: MINOR=5
E: DEVNAME=/dev/tty5
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:5

P: /devices/virtual/tty/tty50
N: tty50
S: char/4:50
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty50
E: MAJOR=4
E: MINOR=50
E: DEVNAME=/dev/tty50
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:50

P: /devices/virtual/tty/tty51
N: tty51
S: char/4:51
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty51
E: MAJOR=4
E: MINOR=51
E: DEVNAME=/dev/tty51
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:51

P: /devices/virtual/tty/tty52
N: tty52
S: char/4:52
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty52
E: MAJOR=4
E: MINOR=52
E: DEVNAME=/dev/tty52
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:52

P: /devices/virtual/tty/tty53
N: tty53
S: char/4:53
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty53
E: MAJOR=4
E: MINOR=53
E: DEVNAME=/dev/tty53
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:53

P: /devices/virtual/tty/tty54
N: tty54
S: char/4:54
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty54
E: MAJOR=4
E: MINOR=54
E: DEVNAME=/dev/tty54
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:54

P: /devices/virtual/tty/tty55
N: tty55
S: char/4:55
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty55
E: MAJOR=4
E: MINOR=55
E: DEVNAME=/dev/tty55
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:55

P: /devices/virtual/tty/tty56
N: tty56
S: char/4:56
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty56
E: MAJOR=4
E: MINOR=56
E: DEVNAME=/dev/tty56
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:56

P: /devices/virtual/tty/tty57
N: tty57
S: char/4:57
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty57
E: MAJOR=4
E: MINOR=57
E: DEVNAME=/dev/tty57
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:57

P: /devices/virtual/tty/tty58
N: tty58
S: char/4:58
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty58
E: MAJOR=4
E: MINOR=58
E: DEVNAME=/dev/tty58
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:58

P: /devices/virtual/tty/tty59
N: tty59
S: char/4:59
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty59
E: MAJOR=4
E: MINOR=59
E: DEVNAME=/dev/tty59
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:59

P: /devices/virtual/tty/tty6
N: tty6
S: char/4:6
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty6
E: MAJOR=4
E: MINOR=6
E: DEVNAME=/dev/tty6
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:6

P: /devices/virtual/tty/tty60
N: tty60
S: char/4:60
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty60
E: MAJOR=4
E: MINOR=60
E: DEVNAME=/dev/tty60
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:60

P: /devices/virtual/tty/tty61
N: tty61
S: char/4:61
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty61
E: MAJOR=4
E: MINOR=61
E: DEVNAME=/dev/tty61
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:61

P: /devices/virtual/tty/tty62
N: tty62
S: char/4:62
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty62
E: MAJOR=4
E: MINOR=62
E: DEVNAME=/dev/tty62
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:62

P: /devices/virtual/tty/tty63
N: tty63
S: char/4:63
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/tty/tty63
E: MAJOR=4
E: MINOR=63
E: DEVNAME=/dev/tty63
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:63

```

---

### Post by buteobuteo on 2011-01-22
Had a quick look at the Win drivers, it appears to be called a K 3805-z device

---

### Post by alexfish on 2011-01-23
Hi

looking for lines which look like

S: Manufacturer=LG ELECTRONICSInc

P: /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.0/[COLOR=Blue]ttyUSB0/tty/ttyUSB0[/COLOR]

your actual info will be different maybe ttyACM*


> P: /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.1/ttyUSB1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.1/ttyUSB1
E: SUBSYSTEM=usb-serial
E: DRIVER=option1

P: /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.1/ttyUSB1/tty/ttyUSB1
N: ttyUSB1
S: char/188:1
S: serial/by-path/pci-0000:00:02.1-usb-0:3:1.1-port0
S: serial/by-id/usb-ZTE_Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if01-port0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.1/ttyUSB1/tty/ttyUSB1
E: SUBSYSTEM=tty
E: DEVNAME=ttyUSB1
example of my devices 


also looking for info similar to screen shot : looking in the " /sys/bus/usb/devices "

As said your device will have different info

---

### Post by buteobuteo on 2011-01-23
Hi 
Looking in " /sys/bus/usb/devices " everything seems to be an EHCI Host Controller.  I have USB 1 to 5 and all seem similar, nothing about tty or a manufacturer other than Asus (Make of netbook in use) and Linux with core code.

---

### Post by alexfish on 2011-01-23
if it shows from the " usb-devices" command
from earlier post
> T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1002 Rev=00.01
S:  Manufacturer=Vodafone
S:  Product=K3805-z
S:  SerialNumber=1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E
C:  #Ifs= 9 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 5 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 7 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)then info has got to be in there somewhere

try this: ensure the device is connected

```
ls -al /sys/bus/usb/devices/usb*/*/*/* > `pwd`/vodfoneinfo
```this will list all the info

each section will be in bocks ,within the blocks of info, look for similar lines

> lrwxrwxrwx 1 root root    0 2011-01-23 09:34 driver -> ../../../../../../bus/usb/drivers/cdc-acm or cdc_acm
lrwxrwxrwx 1 root root    0 2011-01-23 09:34 driver -> ../../../../../../bus/usb/drivers/cdc_ether{ should be 6 or more blocks}

when located post the 6 blocks of info

or can try everything
```
ls -al /sys/bus/usb/devices/*/*/*/* > `pwd`/vodfoneinfo
```

---

### Post by buteobuteo on 2011-01-23
> **alexfish said:**
> if it shows from the " usb-devices" command
from earlier post
then info has got to be in there somewhere
 
try this: ensure the device is connected
 
```
ls -al /sys/bus/usb/devices/usb*/*/*/* > `pwd`/vodfoneinfo
```this will list all the info
 
each section will be in bocks ,within the blocks of info, look for similar lines
 
{ should be 6 or more blocks}
 
when located post the 6 blocks of info
 
or can try everything
```
ls -al /sys/bus/usb/devices/*/*/*/* > `pwd`/vodfoneinfo
```
 
I'm afraid I couldn't find it I tried serching on "cdc_ether" and "cdc_acm" with no result.  I also tried searching on "usb-storage", found about 20 instances but none associated with anything I could recognise.

---

### Post by alexfish on 2011-01-23
> **buteobuteo said:**
> I'm afraid I couldn't find it I tried serching on "cdc_ether" and "cdc_acm" with no result.  I also tried searching on "usb-storage", found about 20 instances but none associated with anything I could recognise.

Hi

can try this script / open up gedit

```
gedit `pwd`/Desktop/devices.tcl
```copy and paste this

```
#!/usr/bin/tclsh
    ################################
    #   Set  path
    set dir "/sys/bus/usb/devices/"
    set devices [ glob -nocomplain -directory $dir *]
    set dev [llength $devices]
    #set devices [lreplace $devices 0 0]
    foreach device $devices {
        puts $device
    }
```save and exit

ensure the device is not connected

enter this code

```
tclsh `pwd`/Desktop/devices.tcl
```now connect the device

give time for the device to settle
and repeat the code

```
tclsh `pwd`/Desktop/devices.tcl
```can post the results

hopefully ! from this it may be possible to see where the device is

also try this if you notice any changes

```
#!/usr/bin/tclsh
    ################################
    #   Set  path
    set dir "/sys/bus/usb/devices/"
    set devices [ glob -nocomplain -directory $dir *]
    set dev [llength $devices]
    #set devices [lreplace $devices 0 0]
    foreach device $devices {
        #puts $device
            set more [ glob -nocomplain -directory $device *]
            foreach mdevice $more {
            puts $mdevice
            }    
    }
```

---

### Post by buteobuteo on 2011-01-24
I can't see any difference between the 2 outputs.  Will try the last suggestion .
```
/sys/bus/usb/devices/usb1
/sys/bus/usb/devices/1-0:1.0
/sys/bus/usb/devices/usb2
/sys/bus/usb/devices/2-0:1.0
/sys/bus/usb/devices/usb3
/sys/bus/usb/devices/3-0:1.0
/sys/bus/usb/devices/usb4
/sys/bus/usb/devices/4-0:1.0
/sys/bus/usb/devices/usb5
/sys/bus/usb/devices/5-0:1.0
/sys/bus/usb/devices/1-5
/sys/bus/usb/devices/1-5:1.0
/sys/bus/usb/devices/1-8
/sys/bus/usb/devices/1-8:1.0
/sys/bus/usb/devices/1-8:1.1
/sys/bus/usb/devices/3-1
/sys/bus/usb/devices/3-1:1.0
/sys/bus/usb/devices/5-1
/sys/bus/usb/devices/5-1:1.0
/sys/bus/usb/devices/5-1:1.1
/sys/bus/usb/devices/5-1:1.2
/sys/bus/usb/devices/5-1:1.3


/sys/bus/usb/devices/usb1
/sys/bus/usb/devices/1-0:1.0
/sys/bus/usb/devices/usb2
/sys/bus/usb/devices/2-0:1.0
/sys/bus/usb/devices/usb3
/sys/bus/usb/devices/3-0:1.0
/sys/bus/usb/devices/usb4
/sys/bus/usb/devices/4-0:1.0
/sys/bus/usb/devices/usb5
/sys/bus/usb/devices/5-0:1.0
/sys/bus/usb/devices/1-5
/sys/bus/usb/devices/1-5:1.0
/sys/bus/usb/devices/1-8
/sys/bus/usb/devices/1-8:1.0
/sys/bus/usb/devices/1-8:1.1
/sys/bus/usb/devices/3-1
/sys/bus/usb/devices/3-1:1.0
/sys/bus/usb/devices/5-1
/sys/bus/usb/devices/5-1:1.0
/sys/bus/usb/devices/5-1:1.1
/sys/bus/usb/devices/5-1:1.2
/sys/bus/usb/devices/5-1:1.3
```

---

### Post by buteobuteo on 2011-01-24
This is the 2 outputs after running the second script, they're obviously different but I'm afraid I couldn't pick out the relevant bits so I posted the whole lot.  Sorry I put the outputs side by side in a spreadsheet for easy comparison and copy/pasted from there.  If it's no good I'll redo.
```
                            body, div, table, thead, tbody, tfoot, tr, th, td, p { font-family: "Liberation Sans"; font-size: x-small; }                                       /sys/bus/usb/devices/usb1/uevent                               /sys/bus/usb/devices/usb1/dev                               /sys/bus/usb/devices/usb1/configuration                               /sys/bus/usb/devices/usb1/bNumInterfaces                               /sys/bus/usb/devices/usb1/bConfigurationValue                               /sys/bus/usb/devices/usb1/bmAttributes                               /sys/bus/usb/devices/usb1/bMaxPower                               /sys/bus/usb/devices/usb1/urbnum                               /sys/bus/usb/devices/usb1/idVendor                               /sys/bus/usb/devices/usb1/idProduct                               /sys/bus/usb/devices/usb1/bcdDevice                               /sys/bus/usb/devices/usb1/bDeviceClass                               /sys/bus/usb/devices/usb1/bDeviceSubClass                               /sys/bus/usb/devices/usb1/bDeviceProtocol                               /sys/bus/usb/devices/usb1/bNumConfigurations                               /sys/bus/usb/devices/usb1/bMaxPacketSize0                               /sys/bus/usb/devices/usb1/speed                               /sys/bus/usb/devices/usb1/busnum                               /sys/bus/usb/devices/usb1/devnum                               /sys/bus/usb/devices/usb1/version                               /sys/bus/usb/devices/usb1/maxchild                               /sys/bus/usb/devices/usb1/quirks                               /sys/bus/usb/devices/usb1/authorized                               /sys/bus/usb/devices/usb1/manufacturer                               /sys/bus/usb/devices/usb1/product                               /sys/bus/usb/devices/usb1/serial                               /sys/bus/usb/devices/usb1/subsystem                               /sys/bus/usb/devices/usb1/power                               /sys/bus/usb/devices/usb1/descriptors                               /sys/bus/usb/devices/usb1/driver                               /sys/bus/usb/devices/usb1/1-0:1.0                               /sys/bus/usb/devices/usb1/ep_00                               /sys/bus/usb/devices/usb1/authorized_default                               /sys/bus/usb/devices/usb1/1-5                               /sys/bus/usb/devices/usb1/1-8                               /sys/bus/usb/devices/1-0:1.0/uevent                               /sys/bus/usb/devices/1-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/1-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/1-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/1-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/1-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/1-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/1-0:1.0/modalias                               /sys/bus/usb/devices/1-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/1-0:1.0/subsystem                               /sys/bus/usb/devices/1-0:1.0/power                               /sys/bus/usb/devices/1-0:1.0/driver                               /sys/bus/usb/devices/1-0:1.0/ep_81                               /sys/bus/usb/devices/usb2/uevent                               /sys/bus/usb/devices/usb2/dev                               /sys/bus/usb/devices/usb2/configuration                               /sys/bus/usb/devices/usb2/bNumInterfaces                               /sys/bus/usb/devices/usb2/bConfigurationValue                               /sys/bus/usb/devices/usb2/bmAttributes                               /sys/bus/usb/devices/usb2/bMaxPower                               /sys/bus/usb/devices/usb2/urbnum                               /sys/bus/usb/devices/usb2/idVendor                               /sys/bus/usb/devices/usb2/idProduct                               /sys/bus/usb/devices/usb2/bcdDevice                               /sys/bus/usb/devices/usb2/bDeviceClass                               /sys/bus/usb/devices/usb2/bDeviceSubClass                               /sys/bus/usb/devices/usb2/bDeviceProtocol                               /sys/bus/usb/devices/usb2/bNumConfigurations                               /sys/bus/usb/devices/usb2/bMaxPacketSize0                               /sys/bus/usb/devices/usb2/speed                               /sys/bus/usb/devices/usb2/busnum                               /sys/bus/usb/devices/usb2/devnum                               /sys/bus/usb/devices/usb2/version                               /sys/bus/usb/devices/usb2/maxchild                               /sys/bus/usb/devices/usb2/quirks                               /sys/bus/usb/devices/usb2/authorized                               /sys/bus/usb/devices/usb2/manufacturer                               /sys/bus/usb/devices/usb2/product                               /sys/bus/usb/devices/usb2/serial                               /sys/bus/usb/devices/usb2/subsystem                               /sys/bus/usb/devices/usb2/power                               /sys/bus/usb/devices/usb2/descriptors                               /sys/bus/usb/devices/usb2/driver                               /sys/bus/usb/devices/usb2/2-0:1.0                               /sys/bus/usb/devices/usb2/ep_00                               /sys/bus/usb/devices/usb2/authorized_default                               /sys/bus/usb/devices/2-0:1.0/uevent                               /sys/bus/usb/devices/2-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/2-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/2-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/2-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/2-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/2-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/2-0:1.0/modalias                               /sys/bus/usb/devices/2-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/2-0:1.0/subsystem                               /sys/bus/usb/devices/2-0:1.0/power                               /sys/bus/usb/devices/2-0:1.0/driver                               /sys/bus/usb/devices/2-0:1.0/ep_81                               /sys/bus/usb/devices/usb3/uevent                               /sys/bus/usb/devices/usb3/dev                               /sys/bus/usb/devices/usb3/configuration                               /sys/bus/usb/devices/usb3/bNumInterfaces                               /sys/bus/usb/devices/usb3/bConfigurationValue                               /sys/bus/usb/devices/usb3/bmAttributes                               /sys/bus/usb/devices/usb3/bMaxPower                               /sys/bus/usb/devices/usb3/urbnum                               /sys/bus/usb/devices/usb3/idVendor                               /sys/bus/usb/devices/usb3/idProduct                               /sys/bus/usb/devices/usb3/bcdDevice                               /sys/bus/usb/devices/usb3/bDeviceClass                               /sys/bus/usb/devices/usb3/bDeviceSubClass                               /sys/bus/usb/devices/usb3/bDeviceProtocol                               /sys/bus/usb/devices/usb3/bNumConfigurations                               /sys/bus/usb/devices/usb3/bMaxPacketSize0                               /sys/bus/usb/devices/usb3/speed                               /sys/bus/usb/devices/usb3/busnum                               /sys/bus/usb/devices/usb3/devnum                               /sys/bus/usb/devices/usb3/version                               /sys/bus/usb/devices/usb3/maxchild                               /sys/bus/usb/devices/usb3/quirks                               /sys/bus/usb/devices/usb3/authorized                               /sys/bus/usb/devices/usb3/manufacturer                               /sys/bus/usb/devices/usb3/product                               /sys/bus/usb/devices/usb3/serial                               /sys/bus/usb/devices/usb3/subsystem                               /sys/bus/usb/devices/usb3/power                               /sys/bus/usb/devices/usb3/descriptors                               /sys/bus/usb/devices/usb3/driver                               /sys/bus/usb/devices/usb3/3-0:1.0                               /sys/bus/usb/devices/usb3/ep_00                               /sys/bus/usb/devices/usb3/authorized_default                               /sys/bus/usb/devices/usb3/3-1                               /sys/bus/usb/devices/3-0:1.0/uevent                               /sys/bus/usb/devices/3-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/3-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/3-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/3-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/3-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/3-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/3-0:1.0/modalias                               /sys/bus/usb/devices/3-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/3-0:1.0/subsystem                               /sys/bus/usb/devices/3-0:1.0/power                               /sys/bus/usb/devices/3-0:1.0/driver                               /sys/bus/usb/devices/3-0:1.0/ep_81                               /sys/bus/usb/devices/usb4/uevent                               /sys/bus/usb/devices/usb4/dev                               /sys/bus/usb/devices/usb4/configuration                               /sys/bus/usb/devices/usb4/bNumInterfaces                               /sys/bus/usb/devices/usb4/bConfigurationValue                               /sys/bus/usb/devices/usb4/bmAttributes                               /sys/bus/usb/devices/usb4/bMaxPower                               /sys/bus/usb/devices/usb4/urbnum                               /sys/bus/usb/devices/usb4/idVendor                               /sys/bus/usb/devices/usb4/idProduct                               /sys/bus/usb/devices/usb4/bcdDevice                               /sys/bus/usb/devices/usb4/bDeviceClass                               /sys/bus/usb/devices/usb4/bDeviceSubClass                               /sys/bus/usb/devices/usb4/bDeviceProtocol                               /sys/bus/usb/devices/usb4/bNumConfigurations                               /sys/bus/usb/devices/usb4/bMaxPacketSize0                               /sys/bus/usb/devices/usb4/speed                               /sys/bus/usb/devices/usb4/busnum                               /sys/bus/usb/devices/usb4/devnum                               /sys/bus/usb/devices/usb4/version                               /sys/bus/usb/devices/usb4/maxchild                               /sys/bus/usb/devices/usb4/quirks                               /sys/bus/usb/devices/usb4/authorized                               /sys/bus/usb/devices/usb4/manufacturer                               /sys/bus/usb/devices/usb4/product                               /sys/bus/usb/devices/usb4/serial                               /sys/bus/usb/devices/usb4/subsystem                               /sys/bus/usb/devices/usb4/power                               /sys/bus/usb/devices/usb4/descriptors                               /sys/bus/usb/devices/usb4/driver                               /sys/bus/usb/devices/usb4/4-0:1.0                               /sys/bus/usb/devices/usb4/ep_00                               /sys/bus/usb/devices/usb4/authorized_default                               /sys/bus/usb/devices/4-0:1.0/uevent                               /sys/bus/usb/devices/4-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/4-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/4-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/4-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/4-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/4-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/4-0:1.0/modalias                               /sys/bus/usb/devices/4-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/4-0:1.0/subsystem                               /sys/bus/usb/devices/4-0:1.0/power                               /sys/bus/usb/devices/4-0:1.0/driver                               /sys/bus/usb/devices/4-0:1.0/ep_81                               /sys/bus/usb/devices/usb5/uevent                               /sys/bus/usb/devices/usb5/dev                               /sys/bus/usb/devices/usb5/configuration                               /sys/bus/usb/devices/usb5/bNumInterfaces                               /sys/bus/usb/devices/usb5/bConfigurationValue                               /sys/bus/usb/devices/usb5/bmAttributes                               /sys/bus/usb/devices/usb5/bMaxPower                               /sys/bus/usb/devices/usb5/urbnum                               /sys/bus/usb/devices/usb5/idVendor                               /sys/bus/usb/devices/usb5/idProduct                               /sys/bus/usb/devices/usb5/bcdDevice                               /sys/bus/usb/devices/usb5/bDeviceClass                               /sys/bus/usb/devices/usb5/bDeviceSubClass                               /sys/bus/usb/devices/usb5/bDeviceProtocol                               /sys/bus/usb/devices/usb5/bNumConfigurations                               /sys/bus/usb/devices/usb5/bMaxPacketSize0                               /sys/bus/usb/devices/usb5/speed                               /sys/bus/usb/devices/usb5/busnum                               /sys/bus/usb/devices/usb5/devnum                               /sys/bus/usb/devices/usb5/version                               /sys/bus/usb/devices/usb5/maxchild                               /sys/bus/usb/devices/usb5/quirks                               /sys/bus/usb/devices/usb5/authorized                               /sys/bus/usb/devices/usb5/manufacturer                               /sys/bus/usb/devices/usb5/product                               /sys/bus/usb/devices/usb5/serial                               /sys/bus/usb/devices/usb5/subsystem                               /sys/bus/usb/devices/usb5/power                               /sys/bus/usb/devices/usb5/descriptors                               /sys/bus/usb/devices/usb5/driver                               /sys/bus/usb/devices/usb5/5-0:1.0                               /sys/bus/usb/devices/usb5/ep_00                               /sys/bus/usb/devices/usb5/authorized_default                               /sys/bus/usb/devices/usb5/5-1                               /sys/bus/usb/devices/5-0:1.0/uevent                               /sys/bus/usb/devices/5-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/5-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/5-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/5-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/5-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/5-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/5-0:1.0/modalias                               /sys/bus/usb/devices/5-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/5-0:1.0/subsystem                               /sys/bus/usb/devices/5-0:1.0/power                               /sys/bus/usb/devices/5-0:1.0/driver                               /sys/bus/usb/devices/5-0:1.0/ep_81                               /sys/bus/usb/devices/1-5/uevent                               /sys/bus/usb/devices/1-5/dev                               /sys/bus/usb/devices/1-5/configuration                               /sys/bus/usb/devices/1-5/bNumInterfaces                               /sys/bus/usb/devices/1-5/bConfigurationValue                               /sys/bus/usb/devices/1-5/bmAttributes                               /sys/bus/usb/devices/1-5/bMaxPower                               /sys/bus/usb/devices/1-5/urbnum                               /sys/bus/usb/devices/1-5/idVendor                               /sys/bus/usb/devices/1-5/idProduct                               /sys/bus/usb/devices/1-5/bcdDevice                               /sys/bus/usb/devices/1-5/bDeviceClass                               /sys/bus/usb/devices/1-5/bDeviceSubClass                               /sys/bus/usb/devices/1-5/bDeviceProtocol                               /sys/bus/usb/devices/1-5/bNumConfigurations                               /sys/bus/usb/devices/1-5/bMaxPacketSize0                               /sys/bus/usb/devices/1-5/speed                               /sys/bus/usb/devices/1-5/busnum                               /sys/bus/usb/devices/1-5/devnum                               /sys/bus/usb/devices/1-5/version                               /sys/bus/usb/devices/1-5/maxchild                               /sys/bus/usb/devices/1-5/quirks                               /sys/bus/usb/devices/1-5/authorized                               /sys/bus/usb/devices/1-5/manufacturer                               /sys/bus/usb/devices/1-5/product                               /sys/bus/usb/devices/1-5/serial                               /sys/bus/usb/devices/1-5/subsystem                               /sys/bus/usb/devices/1-5/power                               /sys/bus/usb/devices/1-5/descriptors                               /sys/bus/usb/devices/1-5/driver                               /sys/bus/usb/devices/1-5/1-5:1.0                               /sys/bus/usb/devices/1-5/ep_00                               /sys/bus/usb/devices/1-5:1.0/uevent                               /sys/bus/usb/devices/1-5:1.0/bInterfaceNumber                               /sys/bus/usb/devices/1-5:1.0/bAlternateSetting                               /sys/bus/usb/devices/1-5:1.0/bNumEndpoints                               /sys/bus/usb/devices/1-5:1.0/bInterfaceClass                               /sys/bus/usb/devices/1-5:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/1-5:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/1-5:1.0/modalias                               /sys/bus/usb/devices/1-5:1.0/supports_autosuspend                               /sys/bus/usb/devices/1-5:1.0/subsystem                               /sys/bus/usb/devices/1-5:1.0/power                               /sys/bus/usb/devices/1-5:1.0/ep_01                               /sys/bus/usb/devices/1-5:1.0/ep_82                               /sys/bus/usb/devices/1-5:1.0/driver                               /sys/bus/usb/devices/1-5:1.0/host2                               /sys/bus/usb/devices/1-8/uevent                               /sys/bus/usb/devices/1-8/dev                               /sys/bus/usb/devices/1-8/configuration                               /sys/bus/usb/devices/1-8/bNumInterfaces                               /sys/bus/usb/devices/1-8/bConfigurationValue                               /sys/bus/usb/devices/1-8/bmAttributes                               /sys/bus/usb/devices/1-8/bMaxPower                               /sys/bus/usb/devices/1-8/urbnum                               /sys/bus/usb/devices/1-8/idVendor                               /sys/bus/usb/devices/1-8/idProduct                               /sys/bus/usb/devices/1-8/bcdDevice                               /sys/bus/usb/devices/1-8/bDeviceClass                               /sys/bus/usb/devices/1-8/bDeviceSubClass                               /sys/bus/usb/devices/1-8/bDeviceProtocol                               /sys/bus/usb/devices/1-8/bNumConfigurations                               /sys/bus/usb/devices/1-8/bMaxPacketSize0                               /sys/bus/usb/devices/1-8/speed                               /sys/bus/usb/devices/1-8/busnum                               /sys/bus/usb/devices/1-8/devnum                               /sys/bus/usb/devices/1-8/version                               /sys/bus/usb/devices/1-8/maxchild                               /sys/bus/usb/devices/1-8/quirks                               /sys/bus/usb/devices/1-8/authorized                               /sys/bus/usb/devices/1-8/manufacturer                               /sys/bus/usb/devices/1-8/product                               /sys/bus/usb/devices/1-8/subsystem                               /sys/bus/usb/devices/1-8/power                               /sys/bus/usb/devices/1-8/descriptors                               /sys/bus/usb/devices/1-8/driver                               /sys/bus/usb/devices/1-8/1-8:1.0                               /sys/bus/usb/devices/1-8/1-8:1.1                               /sys/bus/usb/devices/1-8/ep_00                               /sys/bus/usb/devices/1-8:1.0/uevent                               /sys/bus/usb/devices/1-8:1.0/bInterfaceNumber                               /sys/bus/usb/devices/1-8:1.0/bAlternateSetting                               /sys/bus/usb/devices/1-8:1.0/bNumEndpoints                               /sys/bus/usb/devices/1-8:1.0/bInterfaceClass                               /sys/bus/usb/devices/1-8:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/1-8:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/1-8:1.0/modalias                               /sys/bus/usb/devices/1-8:1.0/supports_autosuspend                               /sys/bus/usb/devices/1-8:1.0/iad_bFirstInterface                               /sys/bus/usb/devices/1-8:1.0/iad_bInterfaceCount                               /sys/bus/usb/devices/1-8:1.0/iad_bFunctionClass                               /sys/bus/usb/devices/1-8:1.0/iad_bFunctionSubClass                               /sys/bus/usb/devices/1-8:1.0/iad_bFunctionProtocol                               /sys/bus/usb/devices/1-8:1.0/subsystem                               /sys/bus/usb/devices/1-8:1.0/power                               /sys/bus/usb/devices/1-8:1.0/interface                               /sys/bus/usb/devices/1-8:1.0/ep_83                               /sys/bus/usb/devices/1-8:1.0/driver                               /sys/bus/usb/devices/1-8:1.0/video4linux                               /sys/bus/usb/devices/1-8:1.0/input                               /sys/bus/usb/devices/1-8:1.1/uevent                               /sys/bus/usb/devices/1-8:1.1/bInterfaceNumber                               /sys/bus/usb/devices/1-8:1.1/bAlternateSetting                               /sys/bus/usb/devices/1-8:1.1/bNumEndpoints                               /sys/bus/usb/devices/1-8:1.1/bInterfaceClass                               /sys/bus/usb/devices/1-8:1.1/bInterfaceSubClass                               /sys/bus/usb/devices/1-8:1.1/bInterfaceProtocol                               /sys/bus/usb/devices/1-8:1.1/modalias                               /sys/bus/usb/devices/1-8:1.1/supports_autosuspend                               /sys/bus/usb/devices/1-8:1.1/iad_bFirstInterface                               /sys/bus/usb/devices/1-8:1.1/iad_bInterfaceCount                               /sys/bus/usb/devices/1-8:1.1/iad_bFunctionClass                               /sys/bus/usb/devices/1-8:1.1/iad_bFunctionSubClass                               /sys/bus/usb/devices/1-8:1.1/iad_bFunctionProtocol                               /sys/bus/usb/devices/1-8:1.1/subsystem                               /sys/bus/usb/devices/1-8:1.1/power                               /sys/bus/usb/devices/1-8:1.1/driver                               /sys/bus/usb/devices/3-1/uevent                               /sys/bus/usb/devices/3-1/dev                               /sys/bus/usb/devices/3-1/configuration                               /sys/bus/usb/devices/3-1/bNumInterfaces                               /sys/bus/usb/devices/3-1/bConfigurationValue                               /sys/bus/usb/devices/3-1/bmAttributes                               /sys/bus/usb/devices/3-1/bMaxPower                               /sys/bus/usb/devices/3-1/urbnum                               /sys/bus/usb/devices/3-1/idVendor                               /sys/bus/usb/devices/3-1/idProduct                               /sys/bus/usb/devices/3-1/bcdDevice                               /sys/bus/usb/devices/3-1/bDeviceClass                               /sys/bus/usb/devices/3-1/bDeviceSubClass                               /sys/bus/usb/devices/3-1/bDeviceProtocol                               /sys/bus/usb/devices/3-1/bNumConfigurations                               /sys/bus/usb/devices/3-1/bMaxPacketSize0                               /sys/bus/usb/devices/3-1/speed                               /sys/bus/usb/devices/3-1/busnum                               /sys/bus/usb/devices/3-1/devnum                               /sys/bus/usb/devices/3-1/version                               /sys/bus/usb/devices/3-1/maxchild                               /sys/bus/usb/devices/3-1/quirks                               /sys/bus/usb/devices/3-1/authorized                               /sys/bus/usb/devices/3-1/manufacturer                               /sys/bus/usb/devices/3-1/product                               /sys/bus/usb/devices/3-1/subsystem                               /sys/bus/usb/devices/3-1/power                               /sys/bus/usb/devices/3-1/descriptors                               /sys/bus/usb/devices/3-1/driver                               /sys/bus/usb/devices/3-1/3-1:1.0                               /sys/bus/usb/devices/3-1/ep_00                               /sys/bus/usb/devices/3-1:1.0/uevent                               /sys/bus/usb/devices/3-1:1.0/bInterfaceNumber                               /sys/bus/usb/devices/3-1:1.0/bAlternateSetting                               /sys/bus/usb/devices/3-1:1.0/bNumEndpoints                               /sys/bus/usb/devices/3-1:1.0/bInterfaceClass                               /sys/bus/usb/devices/3-1:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/3-1:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/3-1:1.0/modalias                               /sys/bus/usb/devices/3-1:1.0/supports_autosuspend                               /sys/bus/usb/devices/3-1:1.0/subsystem                               /sys/bus/usb/devices/3-1:1.0/power                               /sys/bus/usb/devices/3-1:1.0/ep_81                               /sys/bus/usb/devices/3-1:1.0/driver                               /sys/bus/usb/devices/3-1:1.0/0003:046D:C016.0001                               /sys/bus/usb/devices/3-1:1.0/input                               /sys/bus/usb/devices/5-1/uevent                               /sys/bus/usb/devices/5-1/dev                               /sys/bus/usb/devices/5-1/configuration                               /sys/bus/usb/devices/5-1/bNumInterfaces                               /sys/bus/usb/devices/5-1/bConfigurationValue                               /sys/bus/usb/devices/5-1/bmAttributes                               /sys/bus/usb/devices/5-1/bMaxPower                               /sys/bus/usb/devices/5-1/urbnum                               /sys/bus/usb/devices/5-1/idVendor                               /sys/bus/usb/devices/5-1/idProduct                               /sys/bus/usb/devices/5-1/bcdDevice                               /sys/bus/usb/devices/5-1/bDeviceClass                               /sys/bus/usb/devices/5-1/bDeviceSubClass                               /sys/bus/usb/devices/5-1/bDeviceProtocol                               /sys/bus/usb/devices/5-1/bNumConfigurations                               /sys/bus/usb/devices/5-1/bMaxPacketSize0                               /sys/bus/usb/devices/5-1/speed                               /sys/bus/usb/devices/5-1/busnum                               /sys/bus/usb/devices/5-1/devnum                               /sys/bus/usb/devices/5-1/version                               /sys/bus/usb/devices/5-1/maxchild                               /sys/bus/usb/devices/5-1/quirks                               /sys/bus/usb/devices/5-1/authorized                               /sys/bus/usb/devices/5-1/manufacturer                               /sys/bus/usb/devices/5-1/product                               /sys/bus/usb/devices/5-1/serial                               /sys/bus/usb/devices/5-1/subsystem                               /sys/bus/usb/devices/5-1/power                               /sys/bus/usb/devices/5-1/descriptors                               /sys/bus/usb/devices/5-1/driver                               /sys/bus/usb/devices/5-1/5-1:1.0                               /sys/bus/usb/devices/5-1/5-1:1.1                               /sys/bus/usb/devices/5-1/5-1:1.2                               /sys/bus/usb/devices/5-1/5-1:1.3                               /sys/bus/usb/devices/5-1/ep_00                               /sys/bus/usb/devices/5-1:1.0/uevent                               /sys/bus/usb/devices/5-1:1.0/bInterfaceNumber                               /sys/bus/usb/devices/5-1:1.0/bAlternateSetting                               /sys/bus/usb/devices/5-1:1.0/bNumEndpoints                               /sys/bus/usb/devices/5-1:1.0/bInterfaceClass                               /sys/bus/usb/devices/5-1:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/5-1:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/5-1:1.0/modalias                               /sys/bus/usb/devices/5-1:1.0/supports_autosuspend                               /sys/bus/usb/devices/5-1:1.0/subsystem                               /sys/bus/usb/devices/5-1:1.0/power                               /sys/bus/usb/devices/5-1:1.0/ep_81                               /sys/bus/usb/devices/5-1:1.0/ep_82                               /sys/bus/usb/devices/5-1:1.0/ep_02                               /sys/bus/usb/devices/5-1:1.0/driver                               /sys/bus/usb/devices/5-1:1.0/bluetooth                               /sys/bus/usb/devices/5-1:1.1/uevent                               /sys/bus/usb/devices/5-1:1.1/bInterfaceNumber                               /sys/bus/usb/devices/5-1:1.1/bAlternateSetting                               /sys/bus/usb/devices/5-1:1.1/bNumEndpoints                               /sys/bus/usb/devices/5-1:1.1/bInterfaceClass                               /sys/bus/usb/devices/5-1:1.1/bInterfaceSubClass                               /sys/bus/usb/devices/5-1:1.1/bInterfaceProtocol                               /sys/bus/usb/devices/5-1:1.1/modalias                               /sys/bus/usb/devices/5-1:1.1/supports_autosuspend                               /sys/bus/usb/devices/5-1:1.1/subsystem                               /sys/bus/usb/devices/5-1:1.1/power                               /sys/bus/usb/devices/5-1:1.1/ep_83                               /sys/bus/usb/devices/5-1:1.1/ep_03                               /sys/bus/usb/devices/5-1:1.1/driver                               /sys/bus/usb/devices/5-1:1.2/uevent                               /sys/bus/usb/devices/5-1:1.2/bInterfaceNumber                               /sys/bus/usb/devices/5-1:1.2/bAlternateSetting                               /sys/bus/usb/devices/5-1:1.2/bNumEndpoints                               /sys/bus/usb/devices/5-1:1.2/bInterfaceClass                               /sys/bus/usb/devices/5-1:1.2/bInterfaceSubClass                               /sys/bus/usb/devices/5-1:1.2/bInterfaceProtocol                               /sys/bus/usb/devices/5-1:1.2/modalias                               /sys/bus/usb/devices/5-1:1.2/supports_autosuspend                               /sys/bus/usb/devices/5-1:1.2/subsystem                               /sys/bus/usb/devices/5-1:1.2/power                               /sys/bus/usb/devices/5-1:1.2/ep_84                               /sys/bus/usb/devices/5-1:1.2/ep_04                               /sys/bus/usb/devices/5-1:1.3/uevent                               /sys/bus/usb/devices/5-1:1.3/bInterfaceNumber                               /sys/bus/usb/devices/5-1:1.3/bAlternateSetting                               /sys/bus/usb/devices/5-1:1.3/bNumEndpoints                               /sys/bus/usb/devices/5-1:1.3/bInterfaceClass                               /sys/bus/usb/devices/5-1:1.3/bInterfaceSubClass                               /sys/bus/usb/devices/5-1:1.3/bInterfaceProtocol                               /sys/bus/usb/devices/5-1:1.3/modalias                               /sys/bus/usb/devices/5-1:1.3/supports_autosuspend                               /sys/bus/usb/devices/5-1:1.3/subsystem                               /sys/bus/usb/devices/5-1:1.3/power                               vic@UbuntuBabyAsus:~$                 
``````
                            body, div, table, thead, tbody, tfoot, tr, th, td, p { font-family: "Liberation Sans"; font-size: x-small; }                                       /sys/bus/usb/devices/usb1/manufacturer                               /sys/bus/usb/devices/usb1/product                               /sys/bus/usb/devices/usb1/serial                               /sys/bus/usb/devices/usb1/subsystem                               /sys/bus/usb/devices/usb1/power                               /sys/bus/usb/devices/usb1/descriptors                               /sys/bus/usb/devices/usb1/driver                               /sys/bus/usb/devices/usb1/1-0:1.0                               /sys/bus/usb/devices/usb1/ep_00                               /sys/bus/usb/devices/usb1/authorized_default                               /sys/bus/usb/devices/usb1/1-5                               /sys/bus/usb/devices/usb1/1-8                               /sys/bus/usb/devices/usb1/1-2                               /sys/bus/usb/devices/1-0:1.0/uevent                               /sys/bus/usb/devices/1-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/1-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/1-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/1-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/1-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/1-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/1-0:1.0/modalias                               /sys/bus/usb/devices/1-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/1-0:1.0/subsystem                               /sys/bus/usb/devices/1-0:1.0/power                               /sys/bus/usb/devices/1-0:1.0/driver                               /sys/bus/usb/devices/1-0:1.0/ep_81                               /sys/bus/usb/devices/usb2/uevent                               /sys/bus/usb/devices/usb2/dev                               /sys/bus/usb/devices/usb2/configuration                               /sys/bus/usb/devices/usb2/bNumInterfaces                               /sys/bus/usb/devices/usb2/bConfigurationValue                               /sys/bus/usb/devices/usb2/bmAttributes                               /sys/bus/usb/devices/usb2/bMaxPower                               /sys/bus/usb/devices/usb2/urbnum                               /sys/bus/usb/devices/usb2/idVendor                               /sys/bus/usb/devices/usb2/idProduct                               /sys/bus/usb/devices/usb2/bcdDevice                               /sys/bus/usb/devices/usb2/bDeviceClass                               /sys/bus/usb/devices/usb2/bDeviceSubClass                               /sys/bus/usb/devices/usb2/bDeviceProtocol                               /sys/bus/usb/devices/usb2/bNumConfigurations                               /sys/bus/usb/devices/usb2/bMaxPacketSize0                               /sys/bus/usb/devices/usb2/speed                               /sys/bus/usb/devices/usb2/busnum                               /sys/bus/usb/devices/usb2/devnum                               /sys/bus/usb/devices/usb2/version                               /sys/bus/usb/devices/usb2/maxchild                               /sys/bus/usb/devices/usb2/quirks                               /sys/bus/usb/devices/usb2/authorized                               /sys/bus/usb/devices/usb2/manufacturer                               /sys/bus/usb/devices/usb2/product                               /sys/bus/usb/devices/usb2/serial                               /sys/bus/usb/devices/usb2/subsystem                               /sys/bus/usb/devices/usb2/power                               /sys/bus/usb/devices/usb2/descriptors                               /sys/bus/usb/devices/usb2/driver                               /sys/bus/usb/devices/usb2/2-0:1.0                               /sys/bus/usb/devices/usb2/ep_00                               /sys/bus/usb/devices/usb2/authorized_default                               /sys/bus/usb/devices/2-0:1.0/uevent                               /sys/bus/usb/devices/2-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/2-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/2-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/2-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/2-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/2-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/2-0:1.0/modalias                               /sys/bus/usb/devices/2-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/2-0:1.0/subsystem                               /sys/bus/usb/devices/2-0:1.0/power                               /sys/bus/usb/devices/2-0:1.0/driver                               /sys/bus/usb/devices/2-0:1.0/ep_81                               /sys/bus/usb/devices/usb3/uevent                               /sys/bus/usb/devices/usb3/dev                               /sys/bus/usb/devices/usb3/configuration                               /sys/bus/usb/devices/usb3/bNumInterfaces                               /sys/bus/usb/devices/usb3/bConfigurationValue                               /sys/bus/usb/devices/usb3/bmAttributes                               /sys/bus/usb/devices/usb3/bMaxPower                               /sys/bus/usb/devices/usb3/urbnum                               /sys/bus/usb/devices/usb3/idVendor                               /sys/bus/usb/devices/usb3/idProduct                               /sys/bus/usb/devices/usb3/bcdDevice                               /sys/bus/usb/devices/usb3/bDeviceClass                               /sys/bus/usb/devices/usb3/bDeviceSubClass                               /sys/bus/usb/devices/usb3/bDeviceProtocol                               /sys/bus/usb/devices/usb3/bNumConfigurations                               /sys/bus/usb/devices/usb3/bMaxPacketSize0                               /sys/bus/usb/devices/usb3/speed                               /sys/bus/usb/devices/usb3/busnum                               /sys/bus/usb/devices/usb3/devnum                               /sys/bus/usb/devices/usb3/version                               /sys/bus/usb/devices/usb3/maxchild                               /sys/bus/usb/devices/usb3/quirks                               /sys/bus/usb/devices/usb3/authorized                               /sys/bus/usb/devices/usb3/manufacturer                               /sys/bus/usb/devices/usb3/product                               /sys/bus/usb/devices/usb3/serial                               /sys/bus/usb/devices/usb3/subsystem                               /sys/bus/usb/devices/usb3/power                               /sys/bus/usb/devices/usb3/descriptors                               /sys/bus/usb/devices/usb3/driver                               /sys/bus/usb/devices/usb3/3-0:1.0                               /sys/bus/usb/devices/usb3/ep_00                               /sys/bus/usb/devices/usb3/authorized_default                               /sys/bus/usb/devices/usb3/3-1                               /sys/bus/usb/devices/3-0:1.0/uevent                               /sys/bus/usb/devices/3-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/3-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/3-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/3-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/3-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/3-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/3-0:1.0/modalias                               /sys/bus/usb/devices/3-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/3-0:1.0/subsystem                               /sys/bus/usb/devices/3-0:1.0/power                               /sys/bus/usb/devices/3-0:1.0/driver                               /sys/bus/usb/devices/3-0:1.0/ep_81                               /sys/bus/usb/devices/usb4/uevent                               /sys/bus/usb/devices/usb4/dev                               /sys/bus/usb/devices/usb4/configuration                               /sys/bus/usb/devices/usb4/bNumInterfaces                               /sys/bus/usb/devices/usb4/bConfigurationValue                               /sys/bus/usb/devices/usb4/bmAttributes                               /sys/bus/usb/devices/usb4/bMaxPower                               /sys/bus/usb/devices/usb4/urbnum                               /sys/bus/usb/devices/usb4/idVendor                               /sys/bus/usb/devices/usb4/idProduct                               /sys/bus/usb/devices/usb4/bcdDevice                               /sys/bus/usb/devices/usb4/bDeviceClass                               /sys/bus/usb/devices/usb4/bDeviceSubClass                               /sys/bus/usb/devices/usb4/bDeviceProtocol                               /sys/bus/usb/devices/usb4/bNumConfigurations                               /sys/bus/usb/devices/usb4/bMaxPacketSize0                               /sys/bus/usb/devices/usb4/speed                               /sys/bus/usb/devices/usb4/busnum                               /sys/bus/usb/devices/usb4/devnum                               /sys/bus/usb/devices/usb4/version                               /sys/bus/usb/devices/usb4/maxchild                               /sys/bus/usb/devices/usb4/quirks                               /sys/bus/usb/devices/usb4/authorized                               /sys/bus/usb/devices/usb4/manufacturer                               /sys/bus/usb/devices/usb4/product                               /sys/bus/usb/devices/usb4/serial                               /sys/bus/usb/devices/usb4/subsystem                               /sys/bus/usb/devices/usb4/power                               /sys/bus/usb/devices/usb4/descriptors                               /sys/bus/usb/devices/usb4/driver                               /sys/bus/usb/devices/usb4/4-0:1.0                               /sys/bus/usb/devices/usb4/ep_00                               /sys/bus/usb/devices/usb4/authorized_default                               /sys/bus/usb/devices/4-0:1.0/uevent                               /sys/bus/usb/devices/4-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/4-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/4-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/4-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/4-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/4-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/4-0:1.0/modalias                               /sys/bus/usb/devices/4-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/4-0:1.0/subsystem                               /sys/bus/usb/devices/4-0:1.0/power                               /sys/bus/usb/devices/4-0:1.0/driver                               /sys/bus/usb/devices/4-0:1.0/ep_81                               /sys/bus/usb/devices/usb5/uevent                               /sys/bus/usb/devices/usb5/dev                               /sys/bus/usb/devices/usb5/configuration                               /sys/bus/usb/devices/usb5/bNumInterfaces                               /sys/bus/usb/devices/usb5/bConfigurationValue                               /sys/bus/usb/devices/usb5/bmAttributes                               /sys/bus/usb/devices/usb5/bMaxPower                               /sys/bus/usb/devices/usb5/urbnum                               /sys/bus/usb/devices/usb5/idVendor                               /sys/bus/usb/devices/usb5/idProduct                               /sys/bus/usb/devices/usb5/bcdDevice                               /sys/bus/usb/devices/usb5/bDeviceClass                               /sys/bus/usb/devices/usb5/bDeviceSubClass                               /sys/bus/usb/devices/usb5/bDeviceProtocol                               /sys/bus/usb/devices/usb5/bNumConfigurations                               /sys/bus/usb/devices/usb5/bMaxPacketSize0                               /sys/bus/usb/devices/usb5/speed                               /sys/bus/usb/devices/usb5/busnum                               /sys/bus/usb/devices/usb5/devnum                               /sys/bus/usb/devices/usb5/version                               /sys/bus/usb/devices/usb5/maxchild                               /sys/bus/usb/devices/usb5/quirks                               /sys/bus/usb/devices/usb5/authorized                               /sys/bus/usb/devices/usb5/manufacturer                               /sys/bus/usb/devices/usb5/product                               /sys/bus/usb/devices/usb5/serial                               /sys/bus/usb/devices/usb5/subsystem                               /sys/bus/usb/devices/usb5/power                               /sys/bus/usb/devices/usb5/descriptors                               /sys/bus/usb/devices/usb5/driver                               /sys/bus/usb/devices/usb5/5-0:1.0                               /sys/bus/usb/devices/usb5/ep_00                               /sys/bus/usb/devices/usb5/authorized_default                               /sys/bus/usb/devices/usb5/5-1                               /sys/bus/usb/devices/5-0:1.0/uevent                               /sys/bus/usb/devices/5-0:1.0/bInterfaceNumber                               /sys/bus/usb/devices/5-0:1.0/bAlternateSetting                               /sys/bus/usb/devices/5-0:1.0/bNumEndpoints                               /sys/bus/usb/devices/5-0:1.0/bInterfaceClass                               /sys/bus/usb/devices/5-0:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/5-0:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/5-0:1.0/modalias                               /sys/bus/usb/devices/5-0:1.0/supports_autosuspend                               /sys/bus/usb/devices/5-0:1.0/subsystem                               /sys/bus/usb/devices/5-0:1.0/power                               /sys/bus/usb/devices/5-0:1.0/driver                               /sys/bus/usb/devices/5-0:1.0/ep_81                               /sys/bus/usb/devices/1-5/uevent                               /sys/bus/usb/devices/1-5/dev                               /sys/bus/usb/devices/1-5/configuration                               /sys/bus/usb/devices/1-5/bNumInterfaces                               /sys/bus/usb/devices/1-5/bConfigurationValue                               /sys/bus/usb/devices/1-5/bmAttributes                               /sys/bus/usb/devices/1-5/bMaxPower                               /sys/bus/usb/devices/1-5/urbnum                               /sys/bus/usb/devices/1-5/idVendor                               /sys/bus/usb/devices/1-5/idProduct                               /sys/bus/usb/devices/1-5/bcdDevice                               /sys/bus/usb/devices/1-5/bDeviceClass                               /sys/bus/usb/devices/1-5/bDeviceSubClass                               /sys/bus/usb/devices/1-5/bDeviceProtocol                               /sys/bus/usb/devices/1-5/bNumConfigurations                               /sys/bus/usb/devices/1-5/bMaxPacketSize0                               /sys/bus/usb/devices/1-5/speed                               /sys/bus/usb/devices/1-5/busnum                               /sys/bus/usb/devices/1-5/devnum                               /sys/bus/usb/devices/1-5/version                               /sys/bus/usb/devices/1-5/maxchild                               /sys/bus/usb/devices/1-5/quirks                               /sys/bus/usb/devices/1-5/authorized                               /sys/bus/usb/devices/1-5/manufacturer                               /sys/bus/usb/devices/1-5/product                               /sys/bus/usb/devices/1-5/serial                               /sys/bus/usb/devices/1-5/subsystem                               /sys/bus/usb/devices/1-5/power                               /sys/bus/usb/devices/1-5/descriptors                               /sys/bus/usb/devices/1-5/driver                               /sys/bus/usb/devices/1-5/1-5:1.0                               /sys/bus/usb/devices/1-5/ep_00                               /sys/bus/usb/devices/1-5:1.0/uevent                               /sys/bus/usb/devices/1-5:1.0/bInterfaceNumber                               /sys/bus/usb/devices/1-5:1.0/bAlternateSetting                               /sys/bus/usb/devices/1-5:1.0/bNumEndpoints                               /sys/bus/usb/devices/1-5:1.0/bInterfaceClass                               /sys/bus/usb/devices/1-5:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/1-5:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/1-5:1.0/modalias                               /sys/bus/usb/devices/1-5:1.0/supports_autosuspend                               /sys/bus/usb/devices/1-5:1.0/subsystem                               /sys/bus/usb/devices/1-5:1.0/power                               /sys/bus/usb/devices/1-5:1.0/ep_01                               /sys/bus/usb/devices/1-5:1.0/ep_82                               /sys/bus/usb/devices/1-5:1.0/driver                               /sys/bus/usb/devices/1-5:1.0/host2                               /sys/bus/usb/devices/1-8/uevent                               /sys/bus/usb/devices/1-8/dev                               /sys/bus/usb/devices/1-8/configuration                               /sys/bus/usb/devices/1-8/bNumInterfaces                               /sys/bus/usb/devices/1-8/bConfigurationValue                               /sys/bus/usb/devices/1-8/bmAttributes                               /sys/bus/usb/devices/1-8/bMaxPower                               /sys/bus/usb/devices/1-8/urbnum                               /sys/bus/usb/devices/1-8/idVendor                               /sys/bus/usb/devices/1-8/idProduct                               /sys/bus/usb/devices/1-8/bcdDevice                               /sys/bus/usb/devices/1-8/bDeviceClass                               /sys/bus/usb/devices/1-8/bDeviceSubClass                               /sys/bus/usb/devices/1-8/bDeviceProtocol                               /sys/bus/usb/devices/1-8/bNumConfigurations                               /sys/bus/usb/devices/1-8/bMaxPacketSize0                               /sys/bus/usb/devices/1-8/speed                               /sys/bus/usb/devices/1-8/busnum                               /sys/bus/usb/devices/1-8/devnum                               /sys/bus/usb/devices/1-8/version                               /sys/bus/usb/devices/1-8/maxchild                               /sys/bus/usb/devices/1-8/quirks                               /sys/bus/usb/devices/1-8/authorized                               /sys/bus/usb/devices/1-8/manufacturer                               /sys/bus/usb/devices/1-8/product                               /sys/bus/usb/devices/1-8/subsystem                               /sys/bus/usb/devices/1-8/power                               /sys/bus/usb/devices/1-8/descriptors                               /sys/bus/usb/devices/1-8/driver                               /sys/bus/usb/devices/1-8/1-8:1.0                               /sys/bus/usb/devices/1-8/1-8:1.1                               /sys/bus/usb/devices/1-8/ep_00                               /sys/bus/usb/devices/1-8:1.0/uevent                               /sys/bus/usb/devices/1-8:1.0/bInterfaceNumber                               /sys/bus/usb/devices/1-8:1.0/bAlternateSetting                               /sys/bus/usb/devices/1-8:1.0/bNumEndpoints                               /sys/bus/usb/devices/1-8:1.0/bInterfaceClass                               /sys/bus/usb/devices/1-8:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/1-8:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/1-8:1.0/modalias                               /sys/bus/usb/devices/1-8:1.0/supports_autosuspend                               /sys/bus/usb/devices/1-8:1.0/iad_bFirstInterface                               /sys/bus/usb/devices/1-8:1.0/iad_bInterfaceCount                               /sys/bus/usb/devices/1-8:1.0/iad_bFunctionClass                               /sys/bus/usb/devices/1-8:1.0/iad_bFunctionSubClass                               /sys/bus/usb/devices/1-8:1.0/iad_bFunctionProtocol                               /sys/bus/usb/devices/1-8:1.0/subsystem                               /sys/bus/usb/devices/1-8:1.0/power                               /sys/bus/usb/devices/1-8:1.0/interface                               /sys/bus/usb/devices/1-8:1.0/ep_83                               /sys/bus/usb/devices/1-8:1.0/driver                               /sys/bus/usb/devices/1-8:1.0/video4linux                               /sys/bus/usb/devices/1-8:1.0/input                               /sys/bus/usb/devices/1-8:1.1/uevent                               /sys/bus/usb/devices/1-8:1.1/bInterfaceNumber                               /sys/bus/usb/devices/1-8:1.1/bAlternateSetting                               /sys/bus/usb/devices/1-8:1.1/bNumEndpoints                               /sys/bus/usb/devices/1-8:1.1/bInterfaceClass                               /sys/bus/usb/devices/1-8:1.1/bInterfaceSubClass                               /sys/bus/usb/devices/1-8:1.1/bInterfaceProtocol                               /sys/bus/usb/devices/1-8:1.1/modalias                               /sys/bus/usb/devices/1-8:1.1/supports_autosuspend                               /sys/bus/usb/devices/1-8:1.1/iad_bFirstInterface                               /sys/bus/usb/devices/1-8:1.1/iad_bInterfaceCount                               /sys/bus/usb/devices/1-8:1.1/iad_bFunctionClass                               /sys/bus/usb/devices/1-8:1.1/iad_bFunctionSubClass                               /sys/bus/usb/devices/1-8:1.1/iad_bFunctionProtocol                               /sys/bus/usb/devices/1-8:1.1/subsystem                               /sys/bus/usb/devices/1-8:1.1/power                               /sys/bus/usb/devices/1-8:1.1/driver                               /sys/bus/usb/devices/3-1/uevent                               /sys/bus/usb/devices/3-1/dev                               /sys/bus/usb/devices/3-1/configuration                               /sys/bus/usb/devices/3-1/bNumInterfaces                               /sys/bus/usb/devices/3-1/bConfigurationValue                               /sys/bus/usb/devices/3-1/bmAttributes                               /sys/bus/usb/devices/3-1/bMaxPower                               /sys/bus/usb/devices/3-1/urbnum                               /sys/bus/usb/devices/3-1/idVendor                               /sys/bus/usb/devices/3-1/idProduct                               /sys/bus/usb/devices/3-1/bcdDevice                               /sys/bus/usb/devices/3-1/bDeviceClass                               /sys/bus/usb/devices/3-1/bDeviceSubClass                               /sys/bus/usb/devices/3-1/bDeviceProtocol                               /sys/bus/usb/devices/3-1/bNumConfigurations                               /sys/bus/usb/devices/3-1/bMaxPacketSize0                               /sys/bus/usb/devices/3-1/speed                               /sys/bus/usb/devices/3-1/busnum                               /sys/bus/usb/devices/3-1/devnum                               /sys/bus/usb/devices/3-1/version                               /sys/bus/usb/devices/3-1/maxchild                               /sys/bus/usb/devices/3-1/quirks                               /sys/bus/usb/devices/3-1/authorized                               /sys/bus/usb/devices/3-1/manufacturer                               /sys/bus/usb/devices/3-1/product                               /sys/bus/usb/devices/3-1/subsystem                               /sys/bus/usb/devices/3-1/power                               /sys/bus/usb/devices/3-1/descriptors                               /sys/bus/usb/devices/3-1/driver                               /sys/bus/usb/devices/3-1/3-1:1.0                               /sys/bus/usb/devices/3-1/ep_00                               /sys/bus/usb/devices/3-1:1.0/uevent                               /sys/bus/usb/devices/3-1:1.0/bInterfaceNumber                               /sys/bus/usb/devices/3-1:1.0/bAlternateSetting                               /sys/bus/usb/devices/3-1:1.0/bNumEndpoints                               /sys/bus/usb/devices/3-1:1.0/bInterfaceClass                               /sys/bus/usb/devices/3-1:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/3-1:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/3-1:1.0/modalias                               /sys/bus/usb/devices/3-1:1.0/supports_autosuspend                               /sys/bus/usb/devices/3-1:1.0/subsystem                               /sys/bus/usb/devices/3-1:1.0/power                               /sys/bus/usb/devices/3-1:1.0/ep_81                               /sys/bus/usb/devices/3-1:1.0/driver                               /sys/bus/usb/devices/3-1:1.0/0003:046D:C016.0001                               /sys/bus/usb/devices/3-1:1.0/input                               /sys/bus/usb/devices/5-1/uevent                               /sys/bus/usb/devices/5-1/dev                               /sys/bus/usb/devices/5-1/configuration                               /sys/bus/usb/devices/5-1/bNumInterfaces                               /sys/bus/usb/devices/5-1/bConfigurationValue                               /sys/bus/usb/devices/5-1/bmAttributes                               /sys/bus/usb/devices/5-1/bMaxPower                               /sys/bus/usb/devices/5-1/urbnum                               /sys/bus/usb/devices/5-1/idVendor                               /sys/bus/usb/devices/5-1/idProduct                               /sys/bus/usb/devices/5-1/bcdDevice                               /sys/bus/usb/devices/5-1/bDeviceClass                               /sys/bus/usb/devices/5-1/bDeviceSubClass                               /sys/bus/usb/devices/5-1/bDeviceProtocol                               /sys/bus/usb/devices/5-1/bNumConfigurations                               /sys/bus/usb/devices/5-1/bMaxPacketSize0                               /sys/bus/usb/devices/5-1/speed                               /sys/bus/usb/devices/5-1/busnum                               /sys/bus/usb/devices/5-1/devnum                               /sys/bus/usb/devices/5-1/version                               /sys/bus/usb/devices/5-1/maxchild                               /sys/bus/usb/devices/5-1/quirks                               /sys/bus/usb/devices/5-1/authorized                               /sys/bus/usb/devices/5-1/manufacturer                               /sys/bus/usb/devices/5-1/product                               /sys/bus/usb/devices/5-1/serial                               /sys/bus/usb/devices/5-1/subsystem                               /sys/bus/usb/devices/5-1/power                               /sys/bus/usb/devices/5-1/descriptors                               /sys/bus/usb/devices/5-1/driver                               /sys/bus/usb/devices/5-1/5-1:1.0                               /sys/bus/usb/devices/5-1/5-1:1.1                               /sys/bus/usb/devices/5-1/5-1:1.2                               /sys/bus/usb/devices/5-1/5-1:1.3                               /sys/bus/usb/devices/5-1/ep_00                               /sys/bus/usb/devices/5-1:1.0/uevent                               /sys/bus/usb/devices/5-1:1.0/bInterfaceNumber                               /sys/bus/usb/devices/5-1:1.0/bAlternateSetting                               /sys/bus/usb/devices/5-1:1.0/bNumEndpoints                               /sys/bus/usb/devices/5-1:1.0/bInterfaceClass                               /sys/bus/usb/devices/5-1:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/5-1:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/5-1:1.0/modalias                               /sys/bus/usb/devices/5-1:1.0/supports_autosuspend                               /sys/bus/usb/devices/5-1:1.0/subsystem                               /sys/bus/usb/devices/5-1:1.0/power                               /sys/bus/usb/devices/5-1:1.0/ep_81                               /sys/bus/usb/devices/5-1:1.0/ep_82                               /sys/bus/usb/devices/5-1:1.0/ep_02                               /sys/bus/usb/devices/5-1:1.0/driver                               /sys/bus/usb/devices/5-1:1.0/bluetooth                               /sys/bus/usb/devices/5-1:1.1/uevent                               /sys/bus/usb/devices/5-1:1.1/bInterfaceNumber                               /sys/bus/usb/devices/5-1:1.1/bAlternateSetting                               /sys/bus/usb/devices/5-1:1.1/bNumEndpoints                               /sys/bus/usb/devices/5-1:1.1/bInterfaceClass                               /sys/bus/usb/devices/5-1:1.1/bInterfaceSubClass                               /sys/bus/usb/devices/5-1:1.1/bInterfaceProtocol                               /sys/bus/usb/devices/5-1:1.1/modalias                               /sys/bus/usb/devices/5-1:1.1/supports_autosuspend                               /sys/bus/usb/devices/5-1:1.1/subsystem                               /sys/bus/usb/devices/5-1:1.1/power                               /sys/bus/usb/devices/5-1:1.1/ep_83                               /sys/bus/usb/devices/5-1:1.1/ep_03                               /sys/bus/usb/devices/5-1:1.1/driver                               /sys/bus/usb/devices/5-1:1.2/uevent                               /sys/bus/usb/devices/5-1:1.2/bInterfaceNumber                               /sys/bus/usb/devices/5-1:1.2/bAlternateSetting                               /sys/bus/usb/devices/5-1:1.2/bNumEndpoints                               /sys/bus/usb/devices/5-1:1.2/bInterfaceClass                               /sys/bus/usb/devices/5-1:1.2/bInterfaceSubClass                               /sys/bus/usb/devices/5-1:1.2/bInterfaceProtocol                               /sys/bus/usb/devices/5-1:1.2/modalias                               /sys/bus/usb/devices/5-1:1.2/supports_autosuspend                               /sys/bus/usb/devices/5-1:1.2/subsystem                               /sys/bus/usb/devices/5-1:1.2/power                               /sys/bus/usb/devices/5-1:1.2/ep_84                               /sys/bus/usb/devices/5-1:1.2/ep_04                               /sys/bus/usb/devices/5-1:1.3/uevent                               /sys/bus/usb/devices/5-1:1.3/bInterfaceNumber                               /sys/bus/usb/devices/5-1:1.3/bAlternateSetting                               /sys/bus/usb/devices/5-1:1.3/bNumEndpoints                               /sys/bus/usb/devices/5-1:1.3/bInterfaceClass                               /sys/bus/usb/devices/5-1:1.3/bInterfaceSubClass                               /sys/bus/usb/devices/5-1:1.3/bInterfaceProtocol                               /sys/bus/usb/devices/5-1:1.3/modalias                               /sys/bus/usb/devices/5-1:1.3/supports_autosuspend                               /sys/bus/usb/devices/5-1:1.3/subsystem                               /sys/bus/usb/devices/5-1:1.3/power                               /sys/bus/usb/devices/1-2/uevent                               /sys/bus/usb/devices/1-2/dev                               /sys/bus/usb/devices/1-2/configuration                               /sys/bus/usb/devices/1-2/bNumInterfaces                               /sys/bus/usb/devices/1-2/bConfigurationValue                               /sys/bus/usb/devices/1-2/bmAttributes                               /sys/bus/usb/devices/1-2/bMaxPower                               /sys/bus/usb/devices/1-2/urbnum                               /sys/bus/usb/devices/1-2/idVendor                               /sys/bus/usb/devices/1-2/idProduct                               /sys/bus/usb/devices/1-2/bcdDevice                               /sys/bus/usb/devices/1-2/bDeviceClass                               /sys/bus/usb/devices/1-2/bDeviceSubClass                               /sys/bus/usb/devices/1-2/bDeviceProtocol                               /sys/bus/usb/devices/1-2/bNumConfigurations                               /sys/bus/usb/devices/1-2/bMaxPacketSize0                               /sys/bus/usb/devices/1-2/speed                               /sys/bus/usb/devices/1-2/busnum                               /sys/bus/usb/devices/1-2/devnum                               /sys/bus/usb/devices/1-2/version                               /sys/bus/usb/devices/1-2/maxchild                               /sys/bus/usb/devices/1-2/quirks                               /sys/bus/usb/devices/1-2/authorized                               /sys/bus/usb/devices/1-2/manufacturer                               /sys/bus/usb/devices/1-2/product                               /sys/bus/usb/devices/1-2/serial                               /sys/bus/usb/devices/1-2/subsystem                               /sys/bus/usb/devices/1-2/power                               /sys/bus/usb/devices/1-2/descriptors                               /sys/bus/usb/devices/1-2/driver                               /sys/bus/usb/devices/1-2/1-2:1.0                               /sys/bus/usb/devices/1-2/ep_00                               /sys/bus/usb/devices/1-2:1.0/uevent                               /sys/bus/usb/devices/1-2:1.0/bInterfaceNumber                               /sys/bus/usb/devices/1-2:1.0/bAlternateSetting                               /sys/bus/usb/devices/1-2:1.0/bNumEndpoints                               /sys/bus/usb/devices/1-2:1.0/bInterfaceClass                               /sys/bus/usb/devices/1-2:1.0/bInterfaceSubClass                               /sys/bus/usb/devices/1-2:1.0/bInterfaceProtocol                               /sys/bus/usb/devices/1-2:1.0/modalias                               /sys/bus/usb/devices/1-2:1.0/supports_autosuspend                               /sys/bus/usb/devices/1-2:1.0/subsystem                               /sys/bus/usb/devices/1-2:1.0/power                               /sys/bus/usb/devices/1-2:1.0/driver                               /sys/bus/usb/devices/1-2:1.0/host4                               /sys/bus/usb/devices/1-2:1.0/ep_01                               /sys/bus/usb/devices/1-2:1.0/ep_81                               vic@UbuntuBabyAsus:~$                 
```

---

### Post by alexfish on 2011-01-24
hi

from the original post

> T: Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 2 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=19d2 ProdID=1002 Rev=00.01
S: Manufacturer=Vodafone
S: Product=K3805-z
S: SerialNumber=1B04BBA38D69AC7ABFCA71D3F47B4307FDE05 14E
C: #Ifs= 9 Cfg#= 1 Atr=80 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I: If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I: If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I: If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I: If#= 4 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I: If#= 5 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I: If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 7 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)
[FONT=monospace]/usr/bin/usb-devices: line 79: printf: 08: invalid octal number[/FONT]
and the two parts at post   #[**16**]("http://ubuntuforums.org/showpost.php?p=10392406&postcount=16")

From what I am seeing the device is no longer recognized 

you could try the "usb-devices" command again , No need two post the outputs,
but can confirm you can get the same as in the above

Can suggest trying the device in Windows see what happens, if it works in windows, try in Ubuntu again , see if the device
is seen with the " lsusb" command

if when tried: or have dongle that is recognized : ie from the first bit of tcl script  I have posted
then can show where to look in the system , to see if any device nodes been registered.

alexfish

---

### Post by buteobuteo on 2011-01-24
Hi
Tried your original and got 2 extra lines, I'm afraid the significance of that escapes me.  The device has always (and still does) work in windows.  However it does seem to take longer to connect than the original but still connects if the signal is strong enough.

```
/sys/bus/usb/devices/1-2
/sys/bus/usb/devices/1-2:1.0

```

---

### Post by buteobuteo on 2011-01-24
Results of lsusb command
```
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 19d2:1001 ONDA Communication S.p.A. 
Bus 001 Device 005: ID 13d3:507b IMC Networks 
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I can find sys/bus/usb/devices/1-2:1.0 but there are multiple directories and sub directories all with seemingly the same name. I have no idea what I am looking for in the labyrinth.
 
Just rebooted (without dongle) lsusb command and 
Bus 001 Device 009: ID 19d2:1001 ONDA Communication S.p.A. 
is not there.  ONDA are an Italian company but seem to say that their devices are only for the Italian market.

---

### Post by alexfish on 2011-01-24
hi

need to go step by step

when the device is recocnized with the lsusb command, highlighted in blue

> Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Blue]Bus 001 Device 009: ID 19d2:1001 ONDA Communication S.p.A. [/COLOR]
Bus 001 Device 005: ID 13d3:507b IMC Networks 
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


then use the first bit of script, this will show which directory the device is in

```
#!/usr/bin/tclsh
    ################################
    #   Set  path
    set dir "/sys/bus/usb/devices/"
    set devices [ glob -nocomplain -directory $dir *]
    set dev [llength $devices]
    #set devices [lreplace $devices 0 0]
    foreach device $devices {
        puts $device
    }

```
then use the second script / this will list some of the details required, then may be possible as what to do next (also check it has been copied and pasted correctly).

Please do check the device is been recognized with the lsusb command prior to running the script

---

### Post by buteobuteo on 2011-01-24
I am sorry to be dense but I cannot see what information you want.  The path to required files seems to be
 
/sys/bus/usb/devices/1-2
/sys/bus/usb/devices/1-2:1.0

but I do not understand what it is in here that you need.  Is there a way of listing files here and sub directories to a text file that I can post?  Then you may be able to see what is needed.  Or is that what the second (missing) script is meant to do?

---

### Post by alexfish on 2011-01-24
Phew!

Maybe this will work

```
gedit `pwd`/Desktop/vodafone.tcl
```copy and paste this

```
#!/usr/bin/tclsh
    ################################
    # NO PROCS
    #   Set ids and paths
    global voda
    set voda            0
    set Vendor "19d2"
    set Product "[FONT=monospace]1002[/FONT]"
    set vodafone_ID "$Vendor:$Product"     
    set dir "/sys/bus/usb/devices/"
    puts "Searching Dir $dir"
    set devices [ glob -nocomplain -directory $dir *]
    #set dev [llength $devices]
    #set devices [lreplace $devices 0 0]
    ###############################
    # check vendor exist infile + check ids
    #-*
    foreach device $devices {
        puts $device
        set count 0
        set more [ glob -nocomplain -directory $device *]
        #--*
        foreach mdevice $more {
            incr count
            set checkvendor [string first {idVendor} $mdevice]
            #---*
            if {$checkvendor > -1 } {
                set vend [open $mdevice r]
                set idVendor [read $vend]
                set idVendor [string trim $idVendor]
                close $vend
                #----*                                
                if {$idVendor == $Vendor } {
                    set prodpath "$device/idProduct"
                    set prod [open $prodpath r]
                    set idProduct [read $prod]
                    set idProduct [string trim $idProduct]
                    set deviceVend "$idVendor:$idProduct"
                    close $prod
                    #-----*
                    if {$vodafone_ID == $deviceVend} {
                        set voda             1
                        puts "Directory of Vodafone Device $vodafone_ID $device"
                        #set fre "/sys/bus/usb/devices/1-3"
                        set wild [string trim $device $dir]
                        puts $wild
                        #set spliter [split $device "/"]
                        #set last [llength $devices]
                        #puts "Count $last"
                            #foreach splits $spliter {puts $splits}
                        set dirs_inf [ glob -nocomplain -directory $dir $wild*]
                        puts "Start Stats"
                        foreach inf $dirs_inf {
                            #puts $inf
                            set dirs_inf [ glob -nocomplain -directory $inf *]
                            foreach infos $dirs_inf {puts $infos}
                        }
                        
                    }
                }
            }
        }
    }
#-----*
############################################
# if exist then get the bits
############################################
if {$voda} {
    puts "DONE"
    } else {
    puts "Device $vodafone_ID does not exist"
    }
#############################################
```save and exit

ensure the device is recognized with the "lsusb" command

enter this code

```
tclsh `pwd`/Desktop/vodafone.tcl
```see what happens

alexfish

---

### Post by buteobuteo on 2011-01-25
Tried that with following results.

```
vic@UbuntuBabyAsus:~$ lsusb
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 19d2:1001 ONDA Communication S.p.A. 
Bus 001 Device 005: ID 13d3:507b IMC Networks 
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vic@UbuntuBabyAsus:~$ tclsh `pwd`/Desktop/vodafone.tcl
Searching Dir /sys/bus/usb/devices/
/sys/bus/usb/devices/usb1
/sys/bus/usb/devices/1-0:1.0
/sys/bus/usb/devices/usb2
/sys/bus/usb/devices/2-0:1.0
/sys/bus/usb/devices/usb3
/sys/bus/usb/devices/3-0:1.0
/sys/bus/usb/devices/usb4
/sys/bus/usb/devices/4-0:1.0
/sys/bus/usb/devices/usb5
/sys/bus/usb/devices/5-0:1.0
/sys/bus/usb/devices/1-5
/sys/bus/usb/devices/1-5:1.0
/sys/bus/usb/devices/1-8
/sys/bus/usb/devices/1-8:1.0
/sys/bus/usb/devices/1-8:1.1
/sys/bus/usb/devices/3-1
/sys/bus/usb/devices/3-1:1.0
/sys/bus/usb/devices/5-1
/sys/bus/usb/devices/5-1:1.0
/sys/bus/usb/devices/5-1:1.1
/sys/bus/usb/devices/5-1:1.2
/sys/bus/usb/devices/5-1:1.3
/sys/bus/usb/devices/1-2
/sys/bus/usb/devices/1-2:1.0
Device 19d2:1002 does not exist
vic@UbuntuBabyAsus:~$ 

```

---

### Post by alexfish on 2011-01-25
hi

from the lsusb command the device id shows 19d2:1001 (indicating not switched )
a earlier listing where it was recognized it shows 19d2:1002 (switched)

from usb_modeswitch.d files there is this entry
> ########################################################
# Vodafone (ZTE) K3805-Z
#
# Note:
#      This device has multiple USB profiles. Depending upon how it is flipped
#      from storage mode to modem mode determines its final PID and the packages
#      shown on its ISO CD image.

DefaultVendor= 0x[COLOR=Blue]19d2[/COLOR]
DefaultProduct=0x[COLOR=Blue]1001[/COLOR]

[COLOR=Red]TargetVendor=  0x19d2[/COLOR]
[COLOR=Red]TargetProduct= 0x1003[/COLOR]

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

NeedResponse=1

CheckSuccess=20
so now know the device is not in the usb_modeswitch data highlighted in [COLOR=Red]red[/COLOR]
although the ID's highlighted in [COLOR=Blue]blue[/COLOR] (do exist) ,

note the comments
> #      This device has multiple USB profiles. Depending upon how it is flipped
#      from storage mode to modem mode determines its final PID and the packages
#      shown on its ISO CD ima
from here it may be possible to switch the device directly using the above info
 
next time lsusb shows
> Bus 001 Device 006: ID 19d2:1001 ONDA Communication S.p.A.
try using usb_modeswitch
```
sudo usb_modeswitch -v 0x19d2 -p 0x1001 -P 0x19d2 -V 0x1002 -M "5553424312345678000000000000061b000000020000000000000000000000" -n
```
then check the ID's with the "lsusb" command
```
lsusb
```
if switched it will show
> Bus 001 Device 006: ID 19d2:1002 ONDA Communication S.p.A
run the script
```
tclsh `pwd`/Desktop/vodafone.tcl
```
if failed it will still show
> Bus 001 Device 006: ID 19d2:1001 ONDA Communication S.p.A.
 it will be pointless running the script

the next actions will depend on the results

alexfish

---

### Post by buteobuteo on 2011-01-25
Tried that results below.  Where, how do I get usb_modeswitch command?

```
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 19d2:1001 ONDA Communication S.p.A. 
Bus 001 Device 005: ID 13d3:507b IMC Networks 
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
vic@UbuntuBabyAsus:~$ sudo usb_modeswitch -v 0x19d2 -p 0x1001 -P 0x19d2 -V 0x1002 -M "5553424312345678000000000000061b000000020000000000000000000000" -n
[sudo] password for vic: 
Sorry, try again.
[sudo] password for vic: 
sudo: usb_modeswitch: command not found
vic@UbuntuBabyAsus:~$ 

```

---

### Post by alexfish on 2011-01-25
hi

must check if usb_modeswitch installed : normally installed on meerkat

try
```
which usb_modeswitch
```if the directory is not listed then usb_modeswitch is not installed
so need to install

```
sudo apt-get install usb-modeswitch
```

---

### Post by buteobuteo on 2011-01-26
At work so can't connect via Meerkat using windows to check your post, have saved relevant commands and will reboot into Meerkat.  I used the alternate instal rather than normal CD, probably why the command is missing.  The normal CD always worries me when it says it's going to use the whole disk to instal, I cannot take the risk of all my win terminal programs being wiped, it takes a long time to get them all back and running correctly.  Will let you know ASAP.

---

### Post by buteobuteo on 2011-01-26
Very strange, I left the dongle in whilst re-booting into Meerkat and the lsusb showed Bus 001 Device 006: ID 19d2:1002 ONDA Communication S.p.A. which means connected?  The device was showing a blue LED (blue - 3G, red - not connected, green - GPRS).  When lsusb shows 2001 the device has a red LED.    I cannot sudo apt-get install usb-modeswitch until I'm home and connected in Meerkat.
 
Although the device was showing it was not actually connecting, where do we go from here?

---

### Post by craigbrandt on 2011-01-26
Hi There,

I have been following the post and my situation is exactly the same. Ubuntu 10.10 x86_64 and Vodafone K3805-z. I have been reading the forum and can provide the info you are looking for:

The output of the [ udevadm info --export-db > `pwd`/vodafoneinfo ] is as follows:

> P: /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.1/tty/ttyACM0
N: ttyACM0
S: char/166:0
S: serial/by-path/pci-0000:00:1d.7-usb-0:1:1.1
S: serial/by-id/usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if01
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.1/tty/ttyACM0
E: SUBSYSTEM=tty
E: DEVNAME=ttyACM0
E: ID_PATH=pci-0000:00:1d.7-usb-0:1:1.1
E: ID_VENDOR=Vodafone
E: ID_VENDOR_ENC=Vodafone
E: ID_VENDOR_ID=19d2
E: ID_MODEL=K3805-z
E: ID_MODEL_ENC=K3805-z
E: ID_MODEL_ID=1003
E: ID_REVISION=0001
E: ID_SERIAL=Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F
E: ID_SERIAL_SHORT=7D746B50785D1515EA0ED68FBD6A1F435806096F
E: ID_TYPE=generic
E: ID_BUS=usb
E: ID_USB_INTERFACES=:020800:020201:0a0000:020600:080650:020b00:
E: ID_USB_INTERFACE_NUM=01
E: ID_USB_DRIVER=cdc_acm
E: ID_IFACE=01
E: ID_VENDOR_FROM_DATABASE=ONDA Communication S.p.A.
E: MAJOR=166
E: MINOR=0
E: DEVLINKS=/dev/char/166:0 /dev/serial/by-path/pci-0000:00:1d.7-usb-0:1:1.1 /dev/serial/by-id/usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if01


Any help on this would be appreciated

---

### Post by alexfish on 2011-01-26
zte are different to some other devices / 
can guess

constant blue /ready to connect
blinking blue/ connected
red device switch and ready to receive , initiating commands

I can only assume that issuing the correct commands to a certain port, will the activate the device

Reason :the device could have commands for

3g only
4g or (as some call LTE , using cdc_ether)
NMEA (usually GPS)

Maybe time to look at the drivers on the device

can make a copy then post these in attachments (and hope to make sense of some of the details)

alexfish

---

### Post by alexfish on 2011-01-26
Hi craigbrandt , welcome to the forums

need to confirm the /dev/* from

> P: /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.1/tty/ttyACM0> E: DEVLINKS=/dev/char/166:0 /dev/serial/by-path/pci-0000:00:1d.7-usb-0:1:1.1 /dev/serial/by-id/usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if01this may show the path /dev/tty* but can't confirm .

need to look at lshal as there is normaly a prefix node to the "tty/ttyACM0" in the path of "/devices/pci"
may be something like ttyACM* or /dev/ttyACM*

```
lshal > `pwd`/vodalshal
```the file should be in home directory
possible find the  ID's of the device

in the blocks with device ID . also look for lines

> linux.sysfs_path =

serial.device =
post all the info with ttyACM*

from this it may be possible to get the device connected,
also remind that I am looking for more info about the device
hence the scripts I am posting; as need to know the interfaces etc/ 

can also try

```
ls -al /dev/serial/by-id
```regards

alexfish

---

### Post by buteobuteo on 2011-01-26
Re lights. when plugged in in windows it first shows red flashing light and then shows blue (3G) or green flashing (GPRS) when connected. If I leave the device in whilst re-booting to Merkat it shows a flashing blue light once Meerkat is running and returns 1002. The same as in windows when connected but there is no actual connection to the net.
 
If Meerkat is fresh booted with the device inserted it shows a flashing blue light and 1002 as above.
 
If it is inserted after Meerkat is running it only shows a flashing red light and 1001.
 
Where are the drivers hidden?  I followed sys/bus/usb/drivers/cdc_acm/1-2:10/driver down 16 levels with no sign of an end, why so many repeat levels?
 
I tried Craig's [ udevadm info --export-db > `pwd`/vodafoneinfo ] 
```
P: /devices/pci0000:00/0000:00:1d.7/usb1/1-2
N: bus/usb/001/002
S: char/189:1
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-2
E: MAJOR=189
E: MINOR=1
E: DEVNAME=/dev/bus/usb/001/002
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=19d2/1002/1
E: TYPE=239/2/1
E: BUSNUM=001
E: DEVNUM=002
E: SUBSYSTEM=usb
E: ID_VENDOR=Vodafone
E: ID_VENDOR_ENC=Vodafone
E: ID_VENDOR_ID=19d2
E: ID_MODEL=K3805-z
E: ID_MODEL_ENC=K3805-z
E: ID_MODEL_ID=1002
E: ID_REVISION=0001
E: ID_SERIAL=Vodafone_K3805-z_1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E
E: ID_SERIAL_SHORT=1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E
E: ID_BUS=usb
E: ID_USB_INTERFACES=:020201:0a0000:020600:080650:020b00:
E: DEVLINKS=/dev/char/189:1
```

---

### Post by alexfish on 2011-01-26
hi

this indicates in unswitched state

> [FONT=monospace]E: ID_VENDOR_ID=19d2
E: ID_MODEL=K3805-z
E: ID_MODEL_ENC=K3805-z
[COLOR=Blue]E: ID_MODEL_ID=1002[/COLOR]
E: ID_REVISION=0001[/FONT]does a device or file show on the Desktop, if so then double click on it , it should reveal the files

if no device showing on the desktop can have a look disk utility / from System / Administration/Disk Utility

if the device shows in the disk utility then try using the options / like mount/eject/safely-remove

also if the device shows on the Desktop Try right click with the mouse , and select eject from the mouse menu

note any changes , from the lsub command

other than that ; need to use usb_modeswitch

try these sequences

boot with device connected
connect device after boot

also sometimes devices can be left in switched state when swapping between windows and linux


see what happens / play around with the sequences / don't be in a hurry / at least for now it works in windows

as you can see these events can make the user confused and untrusting towards Linux

usb_modeswitch relieves the pain  (most of the time)


alexfish

**Heck : someone drank four cups of my froffy ubuntu**

---

### Post by craigbrandt on 2011-01-27
Hi,

Thanks again for the help.

The output is as follows:

> udi = '/org/freedesktop/Hal/devices/usb_device_19d2_1003_7D746B50785D1515EA0ED68FBD6A1F435806096F_if1_serial_unknown_0'
  info.capabilities = {'serial', 'modem'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_19d2_1003_7D746B50785D1515EA0ED68FBD6A1F435806096F_if1'  (string)
  info.product = 'Serial Port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_19d2_1003_7D746B50785D1515EA0ED68FBD6A1F435806096F_if1_serial_unknown_0'  (string)
  linux.device_file = '/dev/ttyACM0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  [COLOR=SeaGreen]linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.1/tty/ttyACM0'  (string)[/COLOR]
  modem.command_sets = {'V.250'} (string list)
  [COLOR=SeaGreen]serial.device = '/dev/ttyACM0'  (string)[/COLOR]
  serial.originating_device = '/org/freedesktop/Hal/devices/usb_device_19d2_1003_7D746B50785D1515EA0ED68FBD6A1F435806096F_if1'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'unknown'  (string)
I would love to know how to solve these types of issues in the future! What is actually the problem? I wont learn without trying...

---

### Post by alexfish on 2011-01-27
> **craigbrandt said:**
> Hi,

Thanks again for the help.

The output is as follows:

I would love to know how to solve these types of issues in the future! What is actually the problem? I wont learn without trying...
Hi

the info shows there is /dev/ttyACM0 : however the system shows only two endpoints / normally
some managers will be looking for a device with EPs=3
however from the info

> info.capabilities = {'serial', 'modem'} (string list)shows ttyACM0 to be the modem

and the command set V.250 , which = Hayes AT commands

from this it looks like this part of the device accepts AT commands

can try this to see if the modem responds to the AT commands and hopefully get some info from the
device. then from this info see if it will connect

first going to check which /dev/tty* exit on the system , can explain once response is  posted

```
ls -al /dev/serial/by-id
```from previous info , know  that the was a device /dev/ttyACM0 : this indicates the path to read and write on a linux system,
and that it is AT capabale / AT commands are used to communicate with the modem

see if it will accept AT commands
open up first terminal to monitor the out puts

```
tr -s "\n" < /dev/ttyACM0
```open up second terminal and enter this command

```
echo -e "AT\r" > /dev/ttyACM0
```does OK show in the first terminal

test to see if PIN required

```
echo -e "AT+CPIN?\r" > /dev/ttyACM0
```if shows CPIN: SIM PIN then will have to enter PIN "echo -e "AT+CPIN=<youpin>\r" > /dev/ttyACM0
eg echo -e "AT+CPIN=1234\r" > /dev/ttyACM0

if PIN required : to enter pin code
```
echo -e "AT+CPIN=<youpin>\r" > /dev/ttyACM0
```If reply = CPIN:READY then assume ok to proceed

if so try this command : to reset device
```
echo -e "ATZ\r" > /dev/ttyACM0
```if OK try this command : for general info
```
echo -e "ATI\r" > /dev/ttyACM0
```to see if APN's are listed on the device
```
echo -e "AT+COPS?\r" > /dev/ttyACM0
```if the device is listing more than 1 /dev/ttyACM* then could try both

from this info  decides what to do next / if you have hand book for device it may indicate APN and Phone number,
user name and password , check

ADDED:

could post rest of info from the voda "lshal"file / but zip the file and upload to attachments 

Thanks in advance
alexfish

---

### Post by buteobuteo on 2011-01-27
> **alexfish said:**
> hi

as you can see these events can make the user confused and untrusting towards Linux

usb_modeswitch relieves the pain  (most of the time)


alexfish

**Heck : someone drank four cups of my froffy ubuntu**

I'm not worried about Linux, at least people try to help.  With windows nobody bothers unless 2 million people or a multinational are screaming.

Was trying to find out more about usb_modeswitch  and typed "usb_modeswitch ?" in a terminal and got the reply "Error: Could not find file /etc/usb_modeswitch.conf".  Also tried using Disk Utility, which tells me all about  my hard disk and Single Flash Reader but shows nothing when I click on Peripheral Devices, any idea why?

Retried Disk Utility after booting with the device inserted, it does show but only as an 74MB file system with Model: Vodafone USB SCSI CD-ROM

---

### Post by buteobuteo on 2011-01-27
Been poking around and found that Meerkat is setup to dial "*99#" whereas the working windows dials "*99***16#", unfortunately changing this doesn't seem to have any effect.  
Is there any way of directly requesting a connection?  When Meerkat is connected via WiFi or Lan I can right click and disconnect OK but how do you request a connection?

---

### Post by alexfish on 2011-01-27
hi

just edit the details

but leave the APN blank

---

### Post by craigbrandt on 2011-01-28
Hi alexfish,

There were 2 /dev/tty/ACM*. I had to first umount the Vodafone storage before the AT commands worked. Once done though, all the commands succeeded on both: Here is the output

> ls -al /dev/serial/by-id/total 0
drwxr-xr-x 2 root root 80 2011-01-28 16:51 .
drwxr-xr-x 4 root root 80 2011-01-28 16:51 ..
lrwxrwxrwx 1 root root 13 2011-01-28 16:51 usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-01-28 16:51 usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if03 -> ../../ttyACM1

> echo -e "AT\r" > /dev/ttyACM0OK

> echo -e "AT+CPIN?\r" > /dev/ttyACM0I used the network manager to put the PIN in

+CPIN: READY

> echo -e "ATZ\r" > /dev/ttyACM0OK

> echo -e "ATI\r" > /dev/ttyACM0ATI
P680A5.0.03

> echo -e "AT+COPS?\r" > /dev/ttyACM0AT+COPS?
+COPS: 0,0,"VodaCom-SA",2

I have also attached the file for you.

Thank again!

---

### Post by buteobuteo on 2011-01-28
Hi Craig
I gather that your device is working, I tried the commands (after demounting vodafone storage) but nothing works.  You seem to have a much better grasp of how Linux works.  I'll just have to boot into XP to connect when I'm out and about.

---

### Post by buteobuteo on 2011-01-28
> **alexfish said:**
> hi
 
just edit the details
 
but leave the APN blank
 
Doesn't make any difference if the APN is blank or not.  I'd already tried changing dial number.

---

### Post by alexfish on 2011-01-29
> **buteobuteo said:**
> Doesn't make any difference if the APN is blank or not.  I'd already tried changing dial number.

Hi

have had time to read and digest your posts

can refer back to post #3
> T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1002 Rev=00.01
S:  Manufacturer=Vodafone
S:  Product=K3805-z
S:  SerialNumber=1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E
C:  #Ifs= 9 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 5 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 7 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)the part of post #9

```
E: DEVPATH=/devices/platform/serial8250/tty/ttyS0
E: MAJOR=4
E: MINOR=64
E: DEVNAME=/dev/ttyS0
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:64

P: /devices/platform/serial8250/tty/ttyS1
N: ttyS1
S: char/4:65
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
E: MAJOR=4
E: MINOR=65
E: DEVNAME=/dev/ttyS1
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:65

P: /devices/platform/serial8250/tty/ttyS2
N: ttyS2
S: char/4:66
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
E: MAJOR=4
E: MINOR=66
E: DEVNAME=/dev/ttyS2
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:66

P: /devices/platform/serial8250/tty/ttyS3
N: ttyS3
S: char/4:67
E: UDEV_LOG=3
E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
E: MAJOR=4
E: MINOR=67
E: DEVNAME=/dev/ttyS3
E: SUBSYSTEM=tty
E: DEVLINKS=/dev/char/4:67
```it look as if the device is been seen on ttyS0 to ttyS3

ensure the device is recognized from the "lsusb" command and the "usb-devices

so from these need more info to see if any part of the device is listing as a modem

make this file

```
gedit `pwd`/Desktop/lshal-modem.tcl
```copy and paste this code
```
#!/usr/bin/tclsh
    ################################
    set lshal [exec lshal]
    set lshal [split $lshal "\n"]
    set modem aux:
    foreach lin $lshal {
            set ldfp [string first {'serial', 'modem'} $lin]
            if {$ldfp > -1} {
            puts $lin
            set modem "modem:"
            }
        set ldfp [string first {modem.command_sets} $lin]
            if {$ldfp > -1} {puts $lin}
        set ldfp [string first {serial.device} $lin]
            if {$ldfp > -1} {
            puts "$lin: $modem"
            puts ""
            puts ""
            set modem aux:
            }
    }
```save and exit

to run the code

```
tclsh `pwd`/Desktop/lshal-modem.tcl
```post the results

also when the device is recognized post the results of

```
ls -al /dev/serial/by-id
```also from other post the device appears switch and the sometimes unswitched

can confirm if usb_modeswitch installed

---

### Post by alexfish on 2011-01-29
> **craigbrandt said:**
> Hi alexfish,

There were 2 /dev/tty/ACM*. I had to first umount the Vodafone storage before the AT commands worked. Once done though, all the commands succeeded on both: Here is the output

total 0
drwxr-xr-x 2 root root 80 2011-01-28 16:51 .
drwxr-xr-x 4 root root 80 2011-01-28 16:51 ..
lrwxrwxrwx 1 root root 13 2011-01-28 16:51 usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-01-28 16:51 usb-Vodafone_K3805-z_7D746B50785D1515EA0ED68FBD6A1F435806096F-if03 -> ../../ttyACM1

OK

I used the network manager to put the PIN in

+CPIN: READY

OK

ATI
P680A5.0.03

AT+COPS?
+COPS: 0,0,"VodaCom-SA",2

I have also attached the file for you.

Thank again!

 To avoid confusion have :set up NEW THREAD here for craigbrandt

 [**vodafone "VodaCom-SA"**]("http://ubuntuforums.org/showthread.php?t=1677325")

Reason : Device listing **ID's** different to OP and** tyy***  listing are different

alexfish

---

### Post by Zimmer on 2011-01-29
Skipped quickly through thread so excuse if this is old hat..

Have you tried the Betavine application for these devices?? I used them before 10.04 (in 8.04) when support was not good for all USB modems...

[http://www.betavine.net/bvportal/community/linux](http://www.betavine.net/bvportal/community/linux)

---

### Post by buteobuteo on 2011-01-29
Hi Alexfish
You're very patient.
```
vic@UbuntuBabyAsus:~$ lsusb
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13d3:507b IMC Networks 
Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 002: ID 19d2:1002 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
vic@UbuntuBabyAsus:~$ usb-devices

relavent entry only shown

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1002 Rev=00.01
S:  Manufacturer=Vodafone
S:  Product=K3805-z
S:  SerialNumber=1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E
C:  #Ifs= 9 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 5 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
I:  If#= 7 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)

```

I presume this means there is an error in a file and some drivers are missing.

```
vic@UbuntuBabyAsus:~$ tclsh `pwd`/Desktop/lshal-modem.tcl
  info.capabilities = {'serial', 'modem'} (string list)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM1'  (string): modem:


  info.capabilities = {'serial', 'modem'} (string list)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM0'  (string): modem:
```
```
vic@UbuntuBabyAsus:~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-01-29 13:26 .
drwxr-xr-x 4 root root 80 2011-01-29 13:26 ..
lrwxrwxrwx 1 root root 13 2011-01-29 13:26 usb-Vodafone_K3805-z_1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E-if00 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 2011-01-29 13:26 usb-Vodafone_K3805-z_1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E-if02 -> ../../ttyACM1
```

Hope this means something to you.

---

### Post by alexfish on 2011-01-29
> **Zimmer said:**
> Skipped quickly through thread so excuse if this is old hat..

Have you tried the Betavine application for these devices?? I used them before 10.04 (in 8.04) when support was not good for all USB modems...

[http://www.betavine.net/bvportal/community/linux](http://www.betavine.net/bvportal/community/linux)


If you a  **Novice** I strongly advise against **installing** this software until alternate method of connection is established other than** Network Manager**

**Reason:** Betavine connection manager conflicts with modem-manager IE: it will **uninstall **Modem-Manager
and** Renders** **Network Manager unable to connect**

I will not dwell on the subject: 

alexfish

---

### Post by buteobuteo on 2011-01-29
> **alexfish said:**
> If you a  **Novice** I strongly advise against **installing** this software until alternate method of connection is established other than** Network Manager**

**Reason:** Betavine connection manager conflicts with modem-manager IE: it will **uninstall **Modem-Manager
and** Renders** **Network Manager unable to connect**

I will not dwell on the subject: 

alexfish
Thanks, you answered my next question!  I thought that might be the answer.

---

### Post by alexfish on 2011-01-30
Hi
 downloaded both win and apple drivers / they do the job where appropriated / almost impossible tasks to sort on Linux , so no confusion there.

have been looking for short term means of connecting, and looking further into what have
read on several posts and threads, similar devices,

there are several areas to look, and analyze, so will be posting further , although think sakis3g may provided a short term solution , to getting a connection. it does most of what has been requested on this thread.


Have put in attachments , un-compiled version of Sakis3g, (only the script part )
and renamed sakis3g-src

Can try if you wish . (nothing lost nothing gained)

If downloaded place the script on the desktop and unzip  , check the permission by right click/properties,:Permissions ,ensure the Execute box is ticked.  and rename to sakis3g-src.exe
this should the execute buy double clicking on the file

hopefully a menu will appear with a list of options, 
see what happens , it may give choices , IE interfaces , Apns Etc

May be helpful to post screen shots of your progress or if stuck at any stage

Note for users , this striped out version behaves in a different manor than some installed version of sakis3g
version: hence the rename to -src

[http://www.sakis3g.org/](http://www.sakis3g.org/)
 
Sakis3g Forum

  [http://forum.sakis3g.org/smf/index.php](http://forum.sakis3g.org/smf/index.php)
 
Point of interest
 [http://forum.sakis3g.org/smf/Vodafone]("http://forum.sakis3g.org/smf/index.php?PHPSESSID=452a05a82b9c8c1c63fc8be16c58679e&topic=272.msg1100#new")
 

 Alexfish

---

### Post by buteobuteo on 2011-01-30
Changed name to add .exe and got error
Archive:  /home/vic/Downloads/sakis3g-src.exe
[/home/vic/Downloads/sakis3g-src.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/vic/Downloads/sakis3g-src.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/vic/Downloads/sakis3g-src.exe or
          /home/vic/Downloads/sakis3g-src.exe.zip, and cannot find /home/vic/Downloads/sakis3g-src.exe.ZIP, period.

Tried dropping sakis3g-src (no .exe) in terminal window.
Small window with menu options appeared.
Highlighted connect with 3g and clicked OK
Select modem category that best fits your device.
Highlighted USB device, clicked OK
Failed to connect
tried again
Select modem device that provides modem capabilities.
Selected K3805z and clicked OK
Went back to select modem category
tried again and got to asking for password to run package
Failed to connect
 
It was plugged in after starting Meerkat and had red flashing light all the time.  Will now reboot into XP, connect and then reboot into Meerkat and try the script again.

---

### Post by alexfish on 2011-01-30
hi

can also try this 

make a new folder in the home directory named sakis

ensure the sakis3g-src script is on the desktop

```
exec `pwd`/Desktop/sakis3g-src --debug 2> `pwd`/sakis/sakis3g.txt
```

from the menus select
> only prepare modem (Setup+PINunlock+RegisterNetwork+UdateHAL)

once done the file will be in the sakis folder

if gedit does not recognize the encoding , try with Open Office WP

also can zip the file and upload to attachments

will then drop back to terminal commands, to determine which part of the
device hopefully can reveals the necessary info,or if the missing driver is
relevant.

alexfish

---

### Post by buteobuteo on 2011-01-30
Device is now showing blue flashing LED
run Sakis in terminal and after highlighring USB device it asked interface #0 #2 or #4
From lsusb it looks as though it should be #2 so OK'd #2
Please select APN 
internet
internet
Custom APN
selected first internet
Asked for APN_USER variable
tried "web"
didn't work
tried "vod"
tried twice to connect and failed
went back to beginning of menu
Tried twice more but failed at the connecting point.

Looked hopeful but didn't actually connect.

---

### Post by alexfish on 2011-01-31
> **buteobuteo said:**
> Device is now showing blue flashing LED
> run Sakis in terminal and after highlighring USB device it asked interface #0 #2 or #4From lsusb it looks as though it should be #2 so OK'd #2
Please select APN 
internet
internet
Custom APN
selected first internet
Asked for APN_USER variable
tried "web"
didn't work
tried "vod"
tried twice to connect and failed
went back to beginning of menu
Tried twice more but failed at the connecting point.

Looked hopeful but didn't actually connect.


hi

from last post

> run Sakis in terminal and after highlighring USB device it asked interface #0 #2 or #4, shows 3interfaces

so think it is important of how the device is see by the system when in this state

as request did you manage to get the log file

on previous posts there is enough info and script-lets

to see the necessary bits of the device (in this case more so , as it looks as if the device could be seen as a default ZTE : 
some 3g ZTE devices show three ttty*)

Please remember this , you are the one with the dongle, I am the one at the other end of wherever , if the postman does not arrive , I get no post to read

no post = no reply

remember run sakis3g in debug by post fixing : --debug
as posted

(The next option , could be to remove the cdc_ether module and then modprobe the device with the appropriate driver or module, but need the info)

alexfish

---

### Post by buteobuteo on 2011-01-31
> **alexfish said:**
> hi
 
as request did you manage to get the log file
 
 
Sorry missed a reference to a log file, where and what name would it be?

---

### Post by craigbrandt on 2011-01-31
Hi buteobuteo,

I have tried betavine before. It was on a previous Fedora install though. It did more harm than good! I am quite weary of installing additional 3G software on a box. If possible, I would like to try and get it working via the default network manager. If we can get it working properly, I am sure it will help a lot of people

---

### Post by buteobuteo on 2011-01-31
Sorry, understand what you mean, have attached file.

File was created after device inserted in Meerkat, will now boot XP and run again, if there is a difference it may be helpful.

---

### Post by buteobuteo on 2011-01-31
> **craigbrandt said:**
> Hi buteobuteo,
 
I have tried betavine before. It was on a previous Fedora install though. It did more harm than good! I am quite weary of installing additional 3G software on a box. If possible, I would like to try and get it working via the default network manager. If we can get it working properly, I am sure it will help a lot of people
 From the number of views I think you are right.
Regards
Vic

---

### Post by alexfish on 2011-01-31
> **buteobuteo said:**
> Sorry missed a reference to a log file, where and what name would it be?

hi

follow post
post #51

then when done click on Places / Home Folder / > should see folder "sakis"

the sakis3g file as posted will not harm to the Linux system , Least of all , not install
so can easily deleted from where you sit

the only difference to What I have posted (script-lets) is tcl and the sakis3g is bash script 

using the sakis script  will save a great deal of time and lengthy posting

[COLOR=Blue]1:::the important bit at this stage , is to catch info from the device [/COLOR],[COLOR=Blue] when the Three interfaces are showing[/COLOR] , but  since the connection failed , try to avoid the final connection,

assuming we can get all of the info , and the device working , Then maybe a bit of scripting or use of tcl will , save other users from having to use the terminal
and also hopefully seen by NM

Just noticed Your post

ADDED:
file shows no modem detected .. need to try  as highlighted in blue

Thanks

alexfish

---

### Post by buteobuteo on 2011-01-31
Blue LED file as promised.

---

### Post by alexfish on 2011-01-31
> **buteobuteo said:**
> Blue LED file as promised.

Hi

file  shows

046d:c016:Optical USB Mouse
058f:6335:Mass Storage Device
0b05:b700:BT-253
13d3:507b:USB2.0 UVC PC Camera
19d2:1002:K3805-z
[01657] [20:09:30][COLOR=Blue] No plugged modems found.[/COLOR]
[01657] [20:09:30] Asking user to select: OTHER Please select modem type Select modem category that best fits your 3G modem. Select Cancel USBMODEM USB device BLUETOOTH Bluetooth modem CUSTOM_TTY Custom tty...
[01657] [20:09:30] Asking user to select: OTHER Please select modem type Select modem category that best fits your 3G modem. Select Cancel USBMODEM USB device BLUETOOTH Bluetooth modem CUSTOM_TTY Custom tty...
[01657] [20:09:30] Variable OTHER is not set already.
/-------------------------------------------------------------------------------
[01657] [20:09:30] Will now run command: \'/bin/rm -f /tmp/sakis3g.zenity.pipe\'
/-------------------------------------------------------------------------------
\-------------------------------------------------------------------------------
[01657] [20:09:30] Command returned 0.
\-------------------------------------------------------------------------------
[01657] [20:09:30] PID 3846 is still running.
[01657] [20:09:31] PID 3846 is still running.
[01657] [20:09:31] Prompting user to select variable OTHER.

I am curious how at some stage  sakis was requesting to choose an interfaface

> #0 #1 #2Hoping you can replicate 

Posts #50 and post #52

alexfish

---

### Post by buteobuteo on 2011-01-31
> **alexfish said:**
> Hi

file  shows

046d:c016:Optical USB Mouse
058f:6335:Mass Storage Device
0b05:b700:BT-253
13d3:507b:USB2.0 UVC PC Camera
19d2:1002:K3805-z
[01657] [20:09:30][COLOR=Blue] No plugged modems found.[/COLOR]
[01657] [20:09:30] Asking user to select: OTHER Please select modem type Select modem category that best fits your 3G modem. Select Cancel USBMODEM USB device BLUETOOTH Bluetooth modem CUSTOM_TTY Custom tty...
[01657] [20:09:30] Asking user to select: OTHER Please select modem type Select modem category that best fits your 3G modem. Select Cancel USBMODEM USB device BLUETOOTH Bluetooth modem CUSTOM_TTY Custom tty...
[01657] [20:09:30] Variable OTHER is not set already.
/-------------------------------------------------------------------------------
[01657] [20:09:30] Will now run command: \'/bin/rm -f /tmp/sakis3g.zenity.pipe\'
/-------------------------------------------------------------------------------
\-------------------------------------------------------------------------------
[01657] [20:09:30] Command returned 0.
\-------------------------------------------------------------------------------
[01657] [20:09:30] PID 3846 is still running.
[01657] [20:09:31] PID 3846 is still running.
[01657] [20:09:31] Prompting user to select variable OTHER.

I am curious how at some stage  sakis was requesting to choose an interfaface

Hoping you can replicate 

Posts #50 and post #52

alexfish
Cannot replicate, sakis only asked to choose an interface the first time it was run.  It asked if I wanted  #0 #2 or #4, I checked with "lsub" and the K3805-z showed on #2 so I chose #2.

Added

The device had been primed and working in XP the second time and was showing blue flashing LED.

ADDED

It will re-ask if started again, on #0 and #2 it tries to connect twice and fails, on #4 it says "locating tty" but fails.

---

### Post by alexfish on 2011-01-31
> **buteobuteo said:**
> Cannot replicate, sakis only asked to choose an interface the first time it was run.  It asked if I wanted  #0 #2 or #4, I checked with "lsub" and the K3805-z showed on #2 so I chose #2.

Added

The device had been primed and working in XP the second time and was showing blue flashing LED.

ADDED

It will re-ask if started again, on #0 and #2 it tries to connect twice and fails, on #4 it says "locating tty" but fails.

need to cross reference with the tcl lshal-modem script . hope it is still on the Desktop RE: post #43

```
tclsh `pwd`/Desktop/lshal-modem.tcl
```also check the lsusb command for the ID's

ADDED:  RE post #51
requested menu option from sakis3g
> only prepare modem (Setup+PINunlock+RegisterNetwork+UdateHAL)and from post #43 where the lshal script showed
>  info.capabilities = {'serial', 'modem'} (string list)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM1'  (string): modem:


  info.capabilities = {'serial', 'modem'} (string list)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM0'  (string): modem:

---

### Post by buteobuteo on 2011-01-31
This was on the desktop, have to log off until tomorrow.

---

### Post by alexfish on 2011-01-31
RECAP:

and take the following steps

post #1

With Lynx I plugged in the Vodafone USB dongle and it just asked "What network" and "Acount or payasyougo" and then connected. However Meerkat seems to ignore the dongle [COLOR=Blue]except to show the windows loader files on the desktop[/COLOR]. How do you connect with Meerkat please?

can try right click and eject the device or file see if the device ID = [COLOR=Blue]19d2:1002[/COLOR]
with the lsub command

```
lsusb
```also
my reply post#2 is

> How to check for the option driver and modprobe option driver module**STEP 1:**
in the link there is a reference to ZTE devices not switching

then the how to write the rule

```
sudo gedit /etc/udev/rules.d/zte_eject.rules
```add this line edit the device ID's according to the device : in this case the rule would be

```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="1001", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

```save exit and reboot (with the device connect)

to ensure device is seen on the system

the lsusb command

and note the ID's
 
should show
 
> ID 19d2:1002 ONDA Communication S.p.A. 

if confirmed the device is seen in this state : assume reasonably stable
but test connect on boot with device connected ; then connect device after boot

see which is most stable

if the device is not stable and still getting device ID ID 19d2:1001

then need to look at usb_modeswitch

had requested if the usb_modswitch was installed on the system (need reply)

IF OK go to step 2

**STEP 2:**
from 

```
lsusb
```> if recognized as 19d2:1002 . see if drivers are loading```
usb-devices
```should show
> T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1002 Rev=00.01
S:  Manufacturer=Vodafone
S:  Product=K3805-z
S:  SerialNumber=1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E
C:  #Ifs= 9 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 5 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 7 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)from this it confirms the device has switched and the drivers are loading ( but at present not sure if the config is correct)
IF the output looks like the above go to step 3

**Step 3:**

the tcl script

to execute the script 

```
tclsh `pwd`/Desktop/lshal-modem.tcl
```in the terminal it should show 
> 
info.capabilities = {'serial', 'modem'} (string list)
modem.command_sets = {'V.250'} (string list)
serial.device = '/dev/ttyACM1' (string): modem:

info.capabilities = {'serial', 'modem'} (string list)
modem.command_sets = {'V.250'} (string list)
serial.device = '/dev/ttyACM0' (string): modem:if everything checks out the can proceed to run the sakis3g script at Step 4

**STEP 4:**
> ensure the sakis3g-src script is on the desktop```
exec `pwd`/Desktop/sakis3g-src --debug 2> `pwd`/sakis/sakis3g.txt
```from the menus select
> only prepare modem (Setup+PINunlock+RegisterNetwork+UdateHAL)once done the file will be in the sakis folder

**IF** the file shows
> no modemdo not post the file ,just reply " modem not detected"

**If** the file indicates a modem exits 
 zip the file and upload to attachments

---

### Post by buteobuteo on 2011-02-01
Step 1.  After this rebooted and then plugged device in, after short while it changed from red flashing to blue flashing.  First time it's ever done that, lsusb returned 
Bus 001 Device 007: ID 19d2:1003 ONDA Communication S.p.A. 
Why now showing 1003?
Did try to instal usb_modswitch but failed.
ls-usb returned
```
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1003 Rev=00.01
S:  Manufacturer=Vodafone
S:  Product=K3805-z
S:  SerialNumber=1B04BBA38D69AC7ABFCA71D3F47B4307FDE0514E
C:  #Ifs=10 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 6 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 7 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)
/usr/bin/usb-devices: line 79: printf: 09: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)

```
Ran step 3 script
```
vic@UbuntuBabyAsus:~$ tclsh `pwd`/Desktop/lshal-modem.tcl
  info.capabilities = {'serial', 'modem'} (string list)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM1'  (string): modem:


  info.capabilities = {'serial', 'modem'} (string list)
  modem.command_sets = {'V.250'} (string list)
  serial.device = '/dev/ttyACM0'  (string): modem:


vic@UbuntuBabyAsus:~$ 

```
Step 4
```
[01625] [20:23:59] No plugged modems found.
```

Doesn't make much sense to me.  Will try reloading usb-modeswitch.

---

### Post by buteobuteo on 2011-02-01
Reloaded usb-modeswitch and tried
```
sudo usb_modeswitch -v 0x19d2 -p 0x1001 -P 0x19d2 -V 0x1002 -M "5553424312345678000000000000061b000000020000000000000000000000" -n
```
Result
```
vic@UbuntuBabyAsus:~$ sudo usb_modeswitch -v 0x19d2 -p 0x1001 -P 0x19d2 -V 0x1002 -M "5553424312345678000000000000061b000000020000000000000000000000" -n
[sudo] password for vic: 

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 No default device found. Is it connected? Bye.

```

---

### Post by alexfish on 2011-02-02
Seem OK till Sakis

Repeat the Steps as mention in previous post , no need to post results
if everything OK till you get to the sakis stage

everything OK
```
exec `pwd`/Desktop/sakis3g-src --debug 2> `pwd`/sakis/sakis3g.txt
```When using sakis should ensure to follow these menus sequences
> more optionsselect
> select only prepare modem (setup+PIN unlock+Register network+UpdateHAL)select
> USB deviceselect
 > <your device>see what happens

post the the results in attachments
ADDED

OOP's
just noticed when running sakis in debug as above
that the contents of debug file disappears / maybe catch some of it from the terminal

---

### Post by buteobuteo on 2011-02-02
OK up to Sakis
When got to interface, it asked  #1  #3   or  #5  chose #1 as device showing 001 on lsusb.  Still failed to connect, file attached.

---

### Post by alexfish on 2011-02-02
> **buteobuteo said:**
> OK up to Sakis
When got to interface, it asked  #1  #3   or  #5  chose #1 as device showing 001 on lsusb.  Still failed to connect, file attached.
sakis log shows some interesting bits
> USBMODEM='19d2:1003'previous ID,s show 
> USBMODEM='19d2:1002'when the device is recognized as 19d2:1003 and ran the sakis script ,actually connects

except for a [COLOR=Blue]LCP failure[/COLOR] : possible things to look at : 

also of note from the info there appears to be APN "[COLOR=Blue]internetinternet[/COLOR]" , this does not look correct
and sakis3g was dialing on this info

according to the sim provider info 

network-id mcc="234" mnc="15"

and looking up the data base

there are three options for this simcard {mainly to with the pay plans and APN's and passwords}

Options
> Contract:
APN = internet
Username = web
Password = web
DNS1 = 10.206.65.68
DNS2 = 10.203.65.68

Prepaid:
APN = pp.vodafone.co.uk
Username = wap
Password = wap
DNS1 = 172.29.1.11
DNS2 = 172.29.1.11

TopUp and Go:
APN = pp.internet
Username none
Password none
it is possible to use these option in sakis3g by using [COLOR=Blue]custom APN[/COLOR]
if using Custom APN and Username & Password not required , just enter " pass " or any word of your choice { the servers don't ask for them}

maybe worth a try

although you will have to monitor the device ID's before trying the connection
and monitor what happens , keep using the logging options

from the log : parts of the connection details
Note the first line and the also the LCP failure with NCP
> AT+CGDCONT=1,"IP","[COLOR=Blue]internetinternetinternet[/COLOR]"
pppd options in effect:
Serial connection established.
[04721] [20:58:36] Waiting for interface to go up (1 seconds passed).
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
Remote message: Icera PPP - Password Verified OK
PAP authentication succeeded
[04721] [20:58:37] PID 11209 is still running.
[04721] [20:58:37] Interface ppp0 is up.
[04721] [20:58:37] Waiting for interface to go up (2 seconds passed).
[04721] [20:58:38] PID 11209 is still running.
[04721] [20:58:38] Interface ppp0 is up.
[04721] [20:58:38] Waiting for interface to go up (3 seconds passed).
[COLOR=Blue]LCP terminated by peer (0021: Normal Termination by NCP)[/COLOR]
Hangup (SIGHUP)
Modem hangup
Connection terminated.ADDED:
when the device shows the ID 19d2:1003 , does Network Manager recognize the device

also of note from the log is the[COLOR=Blue] AT+CGDCONT=1,"IP"

[COLOR=Black]it seems to be accumulating "[/COLOR][/COLOR][COLOR=Blue]internet[/COLOR][COLOR=Blue]" i[COLOR=Black]n the same area of the sim : IE first shows " internetinetnet" then "intenetinternetinternet"
MONITOR THIS , 
from the log
+CGDCONT: 1,"IP","internetinternet","",0,1
+CGDCONT: 2,"IP","internet","",0,1
[/COLOR][/COLOR]

---

### Post by buteobuteo on 2011-02-02
I did ask about 1002 changing to 1003 in previous post, is it significant?  I did choose internet (not internetinternet) as this is in the XP setup.  The device is contract and I entered exactly as you show except sakis does not ask for DNS 1 &2.

Not sure where Network Manager is, there is network connections in System/Preferences or network tools in System/Administration.  I did have a look in software sources but there seems to be several Network managers, didn't want to try loading the wrong one and make things worse.

---

### Post by alexfish on 2011-02-02
> **buteobuteo said:**
> I did ask about 1002 changing to 1003 in previous post, is it significant?  I did choose internet (not internetinternet) as this is in the XP setup.  The device is contract and I entered exactly as you show except sakis does not ask for DNS 1 &2.

Had missed that thanks
from usb_info the device has different ID's depending
how configured,

but as to the reason "still trying to figure out"
still looking at the info : ie blinking lights and swapping between win and Linux
ZTE rules EJECT, or use usb_mode switch , or eject from the desktop

as said your the one with the device: so will have to monitor

at the end of the day need to get the device as stable as possible:


can also try the TWO TERMINALS
here we are assuming the device is recognized as 1003 and all the checking is OK
and try the <cid> at 
> +CGDCONT: 2,"IP","internet","",0,1, 
dial command for this would be "ATDT*99***2#"

open up the first terminal and enter this code
```
tr -s "\n" < /dev/ttyACMO
```open up second terminal and enter this dial command code
```
echo -e "ATDT*99***2#\r" > /dev/ttyACM0
```if it shows 
CONNECT or CONNECT <NUMBER> ,in the first terminal 
or can try the dial command 3 or 4 times if connect does not show

enter this code in the second terminal
```
sudo pppd ttyACM0 115200 debug nodetach defaultroute noipdefault noauth lock usepeerdns user web password web
```if primary and secondary addresses show then your connected
see what happens post the results

Also curious : was the replacement complete with sim card , or just the device and use existing sim

---

### Post by buteobuteo on 2011-02-03
Please excuse my ignorance but what is```
and try the <cid> at 
```Didn't like 
tr -s "\n" < /dev/ttyACMO

vic@UbuntuBabyAsus:~$ tr -s "\n" < /dev/ttyACMO
bash: /dev/ttyACMO: No such file or directory

Lost original device in rush to catch plane, replacement was device + sim

Device is recognised (by lsusb and flashing blue light) when plugged in after a cold start with Meerkat, don't need to prime it in XP first.

Had a look in /dev  it shows tty0 to tty63 with todays date.  Is this normal?

---

### Post by alexfish on 2011-02-03
can do check with

ls -al /dev/serial/by-id ... the file does not exist usually stems from 2 events

the  main one it is not recognized , the other is the removal of the device , and the reconnection  before the system had time to settle , so the /dev/acm0, may have changed to something like /dev/ttyACM1 or 2 or other number 

also did you check the routines step by step as previously posted

ie lsusb etc

as can see from previous post these steps are necessary  , 

the device behaves in a strange manor and has multiple ID's

as your post: and a subsequent, attempt to connect ( almost succeeded ) the un-switched ID is 19d2:1001
> Re: Vodafone USB
Very strange, I left the dongle in whilst re-booting into Meerkat and the lsusb showed Bus 001 Device 006: ID 19d2:1002 ONDA Communication S.p.A. which means connected? The device was showing a blue LED (blue - 3G, red - not connected, green - GPRS). When lsusb shows 2001 the device has a red LED. I cannot sudo apt-get install usb-modeswitch until I'm home and connected in Meerkat.

Although the device was showing it was not actually connecting, where do we go from here?
Step 1. After this rebooted and then plugged device in, after short while it changed from red flashing to blue flashing. First time it's ever done that, lsusb returned
Bus 001 Device 007: ID 19d2:1003 ONDA Communication S.p.A.
Why now showing 1003?The constant blue light , seems good to me , Looks like behavior of a ZTE ready to go . was it a reboot from windows or a reboot
Ubuntu back into Ubuntu
what happens if boot Ubuntu from scratch with the device connected

Don't want this thread stretching all the way to Sidney Harbour , almost half way there now .................;)

---

### Post by buteobuteo on 2011-02-03
Looked in /dev and saw ttyACM0 and ttyACM1
Tried changing command to ttyACM1 and saw 

CONNECT 14400000

in first window, then realised that I,d copied ACM(oscar) not ACM(zero)

Tried ttyACM0 (without rebooting) but returned error.

Does that make any sense?

Device shows as 1003 with blue flashing when inserted after boot into Meerkat or if booted with device plugged in.

---

### Post by alexfish on 2011-02-03
> **buteobuteo said:**
> Looked in /dev and saw ttyACM0 and ttyACM1
Tried changing command to ttyACM1 and saw 

CONNECT 14400000

in first window, then realised that I,d copied ACM(oscar) not ACM(zero)

Tried ttyACM0 (without rebooting) but returned error.

Does that make any sense?

The CONNECT 14400000 

means your connected to a cell , from here issue the pppd command in the second terminal as previously posted'


the meaning of <cid> in sim card can be looked up here

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

Added/ 
from
> Tried ttyACM0 (without rebooting) but returned error.
Does that make any sense?
the device ports ttyACM* , yes it does make sense, but not logical sense, as in should
this device should always connect to ACM0

may be assuming ,had time reading through the How to  link ,that detecting and resourcing new devices can be an arduous task , not only in Linux , but also in windows 
I have read through the Vodafone forum concerning this device,
possible if the VB script was available , and in the right hands then perhaps they could make some headway,

From the info you have posted , it is necessary , to test each port to see which one will connect, but also check the device ID's to which the ports have been allocated by the linux system , 

with some of the above in mind, Had pre posted below.

---

### Post by alexfish on 2011-02-04
as previosly mentioned , the device will be recognized as 1003
from reboot from windows to Ubuntu

here is a suggestion . 

catch the device when in the 1003 mode , with constant blue LED

READ THROUGH THE POST AND DIGEST. actions and sequences prior to committing , read three or four times , to get the picture in the mind

open the first terminal to monitor / edit the ttyACM* to suit the modem /
you should know how to identify this from previous posts
```
tr -s "\n" < /dev/ttyACMO
```open the second terminal
```
echo -e "AT+ZCDRUN=8\r" > /dev/ttyACM0
```this may turn the cd part of the device off

command for stay connected
```
echo -e "AT+ZOPRT=5\r" > /dev/ttyACM0
```find  the device function status
```
echo -e "AT+CFUN?\r" > /dev/ttyACM0
```post the results

can also try connection , as mention post #71

unplug the device , reboot , see what the device ID shows

if shows as 1003 repeat the above ,try the connection again 

can also get the results of these two commands from the terminal . [COLOR=Blue]Prior to Reboot[/COLOR] and have constant blue light , ID = 192d:1003
```
echo -e "AT+CLAC\r" > /dev/ttyACM0
``````
echo -e "AT&V\r" > /dev/ttyACM0
```zip the two files and post in attachments, via Sidney Harbour...:sad:

if problem when in windows

CD   back on by AT+ZCDRUN=9

---

### Post by buteobuteo on 2011-02-06
When device is in 1003 mode the blue LED is flashing, exactly the same as when working in XP.

The device is now always in this mode in Meerkat, it doesn't matter if it is in when booted or if inserted after booting.

Have attached file with results of all five commands given.

---

### Post by alexfish on 2011-02-06
look at the file only AT+CLAC listed
some new commands in there . as to meaning of these , got no Idea as yet, tried to google the meanings , to no avail

did you try the connection as mentioned at post #71

remember you have to find the port which will give the "CONNECT 14400000" message 

as your
> Looked in /dev and saw ttyACM0 and ttyACM1
Tried changing command to ttyACM1 and saw

CONNECT 14400000

in first window, then realised that I,d copied ACM(oscar) not ACM(zero)

Tried ttyACM0 (without rebooting) but returned error.

Does that make any sense?
yes try ttyACM1 if this is the port it connects to
also edit the tty* to suit in the pppd connection script : this bit "sudo pppd ttyACM0" to sudo pppd ttyACM1
```
tr -s "\n" < /dev/ttyACM1
```
```
echo -e "ATDT*99***2#\r" > /dev/ttyACM1
```
```
sudo pppd ttyACM1 115200 debug nodetach defaultroute noipdefault noauth lock usepeerdns user web password web
```

---

### Post by buteobuteo on 2011-02-07
tty/ACM1 definitely returns the connect 1400000 but device is still flashing blue.  My apologies for poor observation, I was using device in XP today and it is solid blue when connected.
 The sudo pppd command returned
```
Couldn't set tty to PPP discipline: Device or resource busy

```Will reboot and try pppd command before doing anything else.

After re-boot
vic@UbuntuBabyAsus:~$ sudo pppd ttyACM1 115200 debug nodetach defaultroute noipdefault noauth lock usepeerdns user web password web
[sudo] password for vic: 
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe5ff2980> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
vic@UbuntuBabyAsus:~$ 
What does that lot mean?  Blue flashing throughout.

---

### Post by alexfish on 2011-02-10
Hi
weird , result , but sakis3g does connect and then gets a disconnect message.
have been trolling , and thinking , Ref to this cdc_ether ,
had noticed from some log files posted on other forums ,  NM attempting to auto connect to usb0(net)
can have the device attached and post results of these commands from the terminal
```
grep NetworkManager /var/log/syslog
```and this one
```
grep modem-manager /var/log/syslog
```

---

### Post by buteobuteo on 2011-02-12
> **alexfish said:**
> Hi
weird , result , but sakis3g does connect and then gets a disconnect message.
have been trolling , and thinking , Ref to this cdc_ether ,
had noticed from some log files posted on other forums ,  NM attempting to auto connect to usb0(net)
can have the device attached and post results of these commands from the terminal
```
grep NetworkManager /var/log/syslog
```and this one
```
grep modem-manager /var/log/syslog
```

Sorry for delay, extremely hectic week at work.  Hope the attached provide some illumination.

---

### Post by alexfish on 2011-02-12
from the Network Manager info
> [COLOR=Blue]<info>  (usb0): carrier is OFF[/COLOR]
<info>  (usb0): new Ethernet device (driver: 'cdc_ether')
<info>  (usb0): exported as /org/freedesktop/NetworkManager/Devices/2
[COLOR=Blue]<info>  (usb0): now managed[/COLOR]
<info>  (usb0): device state change: 1 -> 2 (reason 2)
<info>  (usb0): bringing up device.
<info>  (usb0): preparing device.
<info>  (usb0): deactivating device (reason: 2).

Added default wired connection[COLOR=Blue] 'Auto usb0' for /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.5/net/usb0
[/COLOR]
[COLOR=Blue]<info>  (usb0): carrier now ON (device state 2)[/COLOR]
(usb0): device state change: 2 -> 3 (reason 40)
[COLOR=Blue]<info>  (usb0): carrier now OFF (device state 3[/COLOR])

<info>  (usb0): device state change: 3 -> 2 (reason 40)
<info>  (usb0): deactivating device (reason: 40).

[COLOR=Blue]<info>  Policy set 'Auto BTHomeHub-****' (wlan0) as default for routing and DNS.[/COLOR] <<< try to disable this connection when trying the device

<WARN>  [COLOR=Blue]auto_activate_device(): Connection 'Auto usb0' auto-activation failed: (2) Device not managed by NetworkManager[/COLOR]

<info> [COLOR=Blue] (ttyACM1): new GSM device (driver: 'cdc_acm')[/COLOR]
<info>  (ttyACM1): exported as /org/freedesktop/NetworkManager/Devices/3
<info>  [COLOR=Blue](ttyACM1): now managed[/COLOR]
<info>  (ttyACM1): device state change: 1 -> 2 (reason 2)
<info>  (ttyACM1): deactivating device (reason: 2).
<info>  (ttyACM1): device state change: 2 -> 3 (reason 0)as far as the device is concerned looks as if everything is ready  but:

<info> [COLOR=Blue] Policy set 'Auto BTHomeHub-****' (wlan0) as default for routing and DNS.[/COLOR] <<< try to disable this connection when trying the device

Boot up the computer without the device

disable the [COLOR=Blue]BThomeHub[/COLOR] , and monitor the Network connections with nm-tool
```
nm-tool
```connect the device 
wait a couple of minutes ([COLOR=Blue]do nothing[/COLOR])
open up a second terminal 
```
nm-tool
``` or repeat until more info appears or different to first terminal ,post the results of both terminals

also have have a look in the NM Connections , see if the interface shows up

---

### Post by buteobuteo on 2011-02-12
Seems to be recognising but not connecting.

---

### Post by buteobuteo on 2011-02-12
Tried nm after reconnecting Home Hub out of curiosity and got different response.

---

### Post by alexfish on 2011-02-12
Hi

only after after info at present, then will look through , to see if makes sense

can connect the device after boot , again

wait for the device to settle , post results of ifconfig

```
ifconfig
```

alexfish

---

### Post by buteobuteo on 2011-02-12
Requested file attached.

---

### Post by alexfish on 2011-02-24
Hi
appols for late reply to this,
Have been reading through the posts, + also a possible link to these types of devices,
previously had posted on a verizon problem, well not so much a problem , since the device in some case does connect , had post on the thread , to look at how the HSO connect works, Well to cut a long story short.
have been checking out latest data. in the BCM , from betavine
and have found this in the wader core 
```
# -*- coding: utf-8 -*-
# Copyright (C) 2007-2010  Vodafone España, S.A.
# Copyright (C) 2008-2009  Warp Networks, S.L.
# Author:  Andrew Bird
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc.,
# 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

from wader.common.hardware.icera import IceraWCDMADevicePlugin
from wader.common.consts import MM_IP_METHOD_STATIC


class ZTEK3805(IceraWCDMADevicePlugin):
    """:class:`~wader.common.plugin.DevicePlugin` for ZTE's Vodafone K3805"""
    name = "ZTE K3805"
    version = "0.1"
    author = "Andrew Bird"

    __remote_name__ = "K3805-z"

    __properties__ = {
        'ID_VENDOR_ID': [0x19d2],
        'ID_MODEL_ID': [0x1003],
    }

    dialer = 'hso'
    ipmethod = MM_IP_METHOD_STATIC


zte_k3805 = ZTEK3805()
```Having read through all of the data as regards the modem-manager , an the Network manager , there may be a possible problem as regards getting a connecting: the main is probably the probing by the modem-manager
: had notice err buffer full ; + Network Manager pre probing the cdc_ether

So:
looks like all the necessary methods and checking can be done with BCM:
+ looks at the state of the device and will issue the necessary init codes etc: some of which would have been in the info i had requested , but not posted ; but never mind

Best advice is to possibly to use Latest BCM as suggested in a previous post: since you now have sakis3g on the system ; trying BCM should not present a problem
But there may be Two areas of concern  at this point : that been of the state of the Two Modem interfaces : so will be looking through BCM , udev rules: and were placed within the system.
+ the ATTRibutes identification  to which   indicates the modem or port to use , by the system udev rules.
Had noticed at one point , system states use of ACM0 then ACM1. The other been the state of the +CGDCONT , 1 

ADDED : here is one of the rules , notice the call to the ifconfig
> ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1003", RUN="/sbin/ifconfig %k -arp"as yet can't find any other rule in BMC which relates to ZTE 1003,

also entries for a ZTE K3806-Z ID's = 19d2:1015

**Found the init  codes within wader core **

once installed I would ensure that modem-manager is un-installed and if  Network Manager a problem try to disable
Have had experience with installing the latest version , any queries , Please post

Regards 

alexfish

Try this one
Development version: Beta 2.99 suitable for Ubuntu 10 ([download]("https://forge.betavine.net/frs/?group_id=76")) 
Site
[http://www.betavine.net/datacards/index.php/Main_Page](http://www.betavine.net/datacards/index.php/Main_Page)

other readers beware of downloading this software .. see below,

just ran an install from the site , opt for the install from Software Center it will guide you through ,

**of note :** own vodafone huawei device not recognized, although no problem with sakis3g
Looked in the udev rules : found 77-mm-zte-port-types.rules no longer exist : can still connect with sakis3g;; think there were some 35 + rules in there for ZTE devices
seem BCM use the same scheme number::: for there own rules '; have a spare copy in home dir ,, of note in the file "# do not edit this file, it will be overwritten on update"
Now looking through the system for Huawie rules.Phew what next


Must be Docking in Sidney Harbour by now
and if it works will fly back; + if all working then it should be easy to bridge the connection for sharing

---

### Post by alexfish on 2011-02-24
Hi

After the above problems , ran update on system , 
for the Huawie device looks as if there is still a problem with loading the option driver,
easy solved by modprobing the option driver , zte rules still missing , not a problem for me, but may be a headache for others

thing of note,the notification to enter pin code now comes up auto , 
as if the Gnome modem-manager was in existence'.
yet no connections show in the NM ico . or anything in the nm-tool , not a big deal if have alternate method of dial up , could prove to be a headache for others

the BCM now recognizes the Vodafone huawie device, none Vodafone devices not recognized, so will be looking further as regards any changes to the udev rules

log files show a modem-manager running , yet does not respond to a killall ? nor does a modem-manager shows as installed on the system , and not found by searching the system
> alexfish-desktop modem-manager: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:02.1/usb1/1-3 claimed port ttyUSB2of note from install files (DEBIAN , "control")

> Package: wader-core
Version: 0.5.5-1
Architecture: all
Maintainer: *suppressed*
Installed-Size: 1476
Depends: python (>= 2.5), python-central (>= 0.6.11), python-twisted-core, python-serial, python-dbus, python-tz, python-messaging (>= 0.5.9), usb-modeswitch (>= 1.1.0), usb-modeswitch-data (>= 20100322), python-gudev, wvdial | network-manager (>= 0.8), mobile-broadband-provider-info
Recommends: python-twisted-conch
Conflicts:[COLOR=Blue] modemmanager[/COLOR]
Replaces: [COLOR=Blue]modemmanager, vmc-core, wader-core[/COLOR]
Provides:[COLOR=Blue] modemmanager[/COLOR]
Section: net
Priority: optional
Homepage: [http://www.wader-project.org](http://www.wader-project.org)
Description: Internet connection assistant for mobile devices.
  Wader is a tool that manages 3G devices and mobile phones offering a dbus
  interface so other applications can use its services as connecting to the
  Internet, sending SMS, managing contacts, and such. This is the core
  package.
  .
Python-Version: >= 2.5stopping network manager and restarting NM shows

```
alexfish-desktop NetworkManager[8779]: <warn> could not get modem list: Traceback (most recent call last):#012  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb#012    retval = candidate_method(self, *args, **keywords)#012  File "/usr/local/lib/python2.6/dist-packages/wader/common/startup.py", line 94, in EnumerateDevices#012    d = self.hm.get_devices()#012  File "/usr/local/lib/python2.6/dist-packages/wader/common/oses/linux.py", line 130, in get_devices#012    return self._process_found_devices(devices)#012  File "/usr/local/lib/python2.6/dist-packages/wader/common/oses/linux.py", line 146, in _process_found_devices#012    for device in self._setup_devices(devices):#012  File "/usr/local/lib/python2.6/dist-packages/wader/common/oses/linux.py", line 223, in _setup_devices#012    for sysfs_path, info in found_devices.items()]#012  File "/usr/local/lib/python2.6/dist-packages/wader/common/oses/linux.py", line 399, in _get_device_from_info#012    raise RuntimeError("Could not find a plugin with info %s" % info)#012RuntimeError: Could not find a plugin with info {'ID_VENDOR_ID': 6610, 'DEVNAME': 'ttyUSB2', 'DEVICES': ['ttyUSB0', 'ttyUSB1', 'ttyUSB2'], 'ID_MODEL_ID': 49, 'ID_USB_DRIVER': 'option', 'ID_BUS': 'usb'}#012
```BCM shows in processes as " python"

ADDED for interest : worth reading

Vodafone (ZTE) K3805-Z and Vodafone (ZTE) K3806-Z : referenced to BCM from Betavine , in the wader core have found udev rules

```
# Vodafone (ZTE) K3805-Z
ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1003", RUN="/sbin/ifconfig %k -arp"

# Vodafone (ZTE) K3806-Z
ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1015", RUN="/sbin/ifconfig %k -arp"
```the path /etc/udev/rules.d/99-vmc-quirks.rules
if put on the system check there are no other 99* rules . reason: read the udev man pages
if so think about renaming the schema to avoid conflicts .. also note the priority of the RUN= ,, not the normal RUN+= , "RUN=" means override.
Also in the wader core there are plugins
for the devices mentioned, looks good , seems to be what I suspected , as regards the init codes and how to bring the interface up 

worth looking into.

ADDED:
OK : can start by looking in the wader core / icera.py @  /usr/...local/python2.6/dist-package/wader/common/hardware/icera.py
most of what is needed is in this file.
of note is the standard 2g 3g connections . so now looks like a standard 3g connection , and the increased speed of the connection is via the cdc_ether interface
Very similar to the HSO connect . also mention in one of the files ...called zte_k3805.py

[B]Info indicates the icera chipset can do a shutdown so can take between 2 and 7 seconds to connect ,other manager trying to connect may time out esp the pppd
for users trying these devices with a manager other than BCM , suggest looking through pppd options to persist until there is a response from the servers[/B]

this may be of interest . in Ubuntu the BCM log files are hidden in dot folder .. set nautilus to show hidden files /home/ directory  then look for .bcm
in the .bcm folder , will find the log file , along with db folder , database folder , inside of this , will find two data bases , " messages" and "usage"

---

### Post by buteobuteo on 2011-02-27
Hi 
Only just seen your post, please excuse my ignorance but I tried downloading BCM from the link but the only bit I could get to install was the python messaging file.  I see you said opt for software centre install but I don't know how to initiate this.  It comes up with open with GDebi Package installer but this doesn't like unsatisfied dependencies and I can't find the package via the Synaptic Package Manager.

---

### Post by alexfish on 2011-02-27
hi

think first package maybe python messaging
then BCM . or wader core
which ever dependency shows up in the error message , that will be the one to download next , don't think you need the usb_modeswitch data


normally when a download file .deb is clicked usually  is an option message to download and save or use Software center.

software center will show same errors, so don,t matter at this stage just use which method available. 

the packages are not listed in synaptic, but will list in synaptic once installed

Added if still a problem can list exact nature of any error message

alexfish

---

### Post by buteobuteo on 2011-02-27
I have downloaded the files but cannot do anything with them because I don't have enough knowledge to point Package Manager at them and they will not install with the default GDebi Package installer.  Also I cannot find where Package Manager is to change from default GDebi on the download dialogue.
I don't like being negative but I'm frustrated because I can't follow what are obviously plain instructions.

---

### Post by alexfish on 2011-02-27
Hi
can be frustrating if not used to doing;

lets assume have downloaded the three debian pakages from betavine( note to readers . the latest 10. version is Lucid , but hoping can get this device working with Meerkat,)

1. python-messaging_0.5.9-1_all.deb 
2. wader_core_0.5.5-1_all.deb
3. bcm_2.99.12-1_all.deb
and saved in downloads folder

here are the links
[  python-messaging_0.5.9-1_all.deb]("https://forge.betavine.net/frs/download.php/652/python-messaging_0.5.9-1_all.deb")

[  wader-core_0.5.5-1_all.deb]("https://forge.betavine.net/frs/download.php/653/wader-core_0.5.5-1_all.deb")

[  bcm_2.99.12-1_all.deb]("https://forge.betavine.net/frs/download.php/654/bcm_2.99.12-1_all.deb")

LINK TO THE source ( for info)
[https://forge.betavine.net/frs/?group_id=76](https://forge.betavine.net/frs/?group_id=76)

double clicking on the files normally brings up the software center see screen shots , also try right click
with the mouse , see what the install options are, if only install by package Gdeb package installer then select that option


the sequence of install is as listed above 1. 2. 3.

see how it goes

also note the error as shown in the screen shot :: hope this is superficial as 

the first install did not show any errors : IE this is a second install on my system // or maybe assuming if the best way to install is by absolute guidance with Software Manager  screen shot aded of what should
happen when clicking on the links

or to install the python-messaging Via Synaptic Package Manager;; can suggest un-install and try that route only if there is a problem

---

### Post by buteobuteo on 2011-02-27
Thank you, that worked Ok.  On my machine it demanded usb-mododem switch data before it would load wader core.  
Plugged dongle in and still only flashing blue, no connection.  Stopped Home Hub but that did not trigger a connection.  
I have noticed that, as you say, it takes time to connect.  In windows it takes approx twice as long as original dongle.
You were talking about stopping and starting the Managers, how do you do this?

---

### Post by alexfish on 2011-02-27
first lets see what happens with BCM it should be in the menus

from menu select ,Applications /Network/Betavine Connection Manager

what shows in the window ,bottom left ,example of a Vodafone device in screen shot

or it may show no device : if so will look further

---

### Post by buteobuteo on 2011-02-27
Yippeee:lolflag:  it works, nice solid blue light.  This is being posted via the ZTE dongle.  Thank you for your exceptional patience.  Now all I have to do is mark this enormous thread as solved.


Thank you alexfish.

---

### Post by alexfish on 2011-02-27
Thanks . and certainly hope many others with this type of chipset can get connected

don't forget, there will be users looking to other forums esp, Vodafone's own , and even more so at Betavine , 

regards

alexfish

---

### Post by Tom 6 on 2011-04-25
Hi :)
I also have a Vodafone K3805-Z and the 10 pages of reinstalls and false-starts in this thread look very daunting.

Is there a simple guide for this yet or could anyone help me trouble-shoot my problems with this K3805-Z
[http://ubuntuforums.org/showthread.php?p=10718007#post10718007](http://ubuntuforums.org/showthread.php?p=10718007#post10718007)

So far the native linux drivers seem to be installed and recognised but are no enabled.  SUrely all i have to do is enable them?

I'm keen to find the .inf and .bin files for the Windows driver because apparently i am already close to getting ndis-wrapper working?  Any clue where the .inf & .bin files are and what they are called?

Regards from
Tom :)

---

### Post by alexfish on 2011-04-25
> **Tom 6 said:**
> Hi :)
I also have a Vodafone K3805-Z and the 10 pages of reinstalls and false-starts in this thread look very daunting.

Is there a simple guide for this yet or could anyone help me trouble-shoot my problems with this K3805-Z
[http://ubuntuforums.org/showthread.php?p=10718007#post10718007](http://ubuntuforums.org/showthread.php?p=10718007#post10718007)

So far the native linux drivers seem to be installed and recognised but are no enabled.  SUrely all i have to do is enable them?

I'm keen to find the .inf and .bin files for the Windows driver because apparently i am already close to getting ndis-wrapper working?  Any clue where the .inf & .bin files are and what they are called?

Regards from
Tom :)
hi Tom 6 , welcome to the forums

As you can see from this long thread the k3805 has the ability to operate at higher speeds
than standard 3g , hence the use of ether_net type interface , as you can see it has been a problem to get the device up and running (it requires specific rules to bring the interface up and the necessary commands to connect), it is prone to locking up if incorrect commands are sent.

Vodafone  drivers on the device will not work with Ubuntu , hence the development of BCM 

BCM has the necessary drivers for the Vodafone family of re-branded devices including two particular devices  the K3805 and K3806. note it has to be "BCM version" (VMC is not compatable beyond 9.10).So should work in ubuntu 10.04 and 10.10.

It has been reported this device works out of the box with "Ubuntu Natty Narwhal". Final release due soon

if you decide on installing BCM , understand "modem-manager" will be removed from the system and be replaced by wader-core , it also installs it's own udev rules and plug-in's.

before installing , it is  best that the device is recognized on the system ( is it recognized as a modem ? )

To install BCM ,follow the links provided and allow the install to be done through Software Manager (RE-Post #92)

Note: a fair number of none Vodafone devices will not be recognized via the wader core and Network Manager

regards

alexfish

---

### Post by hackeron on 2011-04-25
How would you connect on ubuntu-server from the command line?

---

### Post by Tom 6 on 2011-04-25
Hi :)
I'm back at home for a couple of weeks now.  If i installed the wader then would i be able to reinstall the normal network manager afterwards to get things back the way they were?  

Would it be a better plan to install a dual/multi-boot with 10.10? or 11.04? instead of trying the wader? (just to see if it works).

On Windows the device rarely picks up any signal better than GPRS.  Is the one that is better than 3g only covered in certain areas?  On the boat we hardly ever even get 3g.
Regards from
Tom :)

---

### Post by Tom 6 on 2011-04-26
Hi :)
Ok, i have thought about this a lot.  I have downloaded the 3 packages required for Wader but if installing a newer version of Ubuntu is likely to fix the problem then that is the easiest 1st thing for me to try.

I have /home as a separate partition so if a test install or LiveCd/Usb works then a proper install to upgrade should be fairly easy.  It also gives me LibreOffice nicely installed.  This could all be quite serendipitous :)

Many thanks and regards from
Tom :)

---

### Post by VlatkoB on 2011-11-16
Hi,

I followed the steps below, but Betavine Connection Manager doesn't recognize my device. Statusbar message is "No device".

I uninstalled all three packages, and now my USB device doesn't get recognized by the system.


usb-devices returns: 

```
T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=**19d2** ProdID=**0117** Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=MF1900VIPD010000
C:  #Ifs= 4 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```

I'm using Maverick 64-bit, device is ZTE MF190. 
I have installed also the "vodafone-mobile-connect_2.25.01-1_all" before that, but have uninstalled it.

Everything worked without problems before this installation, I could connect and disconnect through NetworkManager, I just didn't have GUI for controlling the device.

What can be done to return the system to the previous state, so the system can recognize the device and ask for PIN after connecting? (apart from reinstalling the system :-) )

vlatko

> **alexfish said:**
> Hi
can be frustrating if not used to doing;

lets assume have downloaded the three debian pakages from betavine( note to readers . the latest 10. version is Lucid , but hoping can get this device working with Meerkat,)

1. python-messaging_0.5.9-1_all.deb 
2. wader_core_0.5.5-1_all.deb
3. bcm_2.99.12-1_all.deb
and saved in downloads folder

here are the links
[  python-messaging_0.5.9-1_all.deb]("https://forge.betavine.net/frs/download.php/652/python-messaging_0.5.9-1_all.deb")

[  wader-core_0.5.5-1_all.deb]("https://forge.betavine.net/frs/download.php/653/wader-core_0.5.5-1_all.deb")

[  bcm_2.99.12-1_all.deb]("https://forge.betavine.net/frs/download.php/654/bcm_2.99.12-1_all.deb")

LINK TO THE source ( for info)
[https://forge.betavine.net/frs/?group_id=76](https://forge.betavine.net/frs/?group_id=76)

double clicking on the files normally brings up the software center see screen shots , also try right click
with the mouse , see what the install options are, if only install by package Gdeb package installer then select that option


the sequence of install is as listed above 1. 2. 3.

see how it goes

also note the error as shown in the screen shot :: hope this is superficial as 

the first install did not show any errors : IE this is a second install on my system // or maybe assuming if the best way to install is by absolute guidance with Software Manager  screen shot aded of what should
happen when clicking on the links

or to install the python-messaging Via Synaptic Package Manager;; can suggest un-install and try that route only if there is a problem

---

### Post by alexfish on 2011-11-16
Hi VlatkoB 

your device is different to this thread[FONT=monospace]
your device [/FONT]P:  Vendor=**19d2** ProdID=**0117** Rev=00.00

the device on this thread[FONT=monospace][/FONT] P:  Vendor=19d2 ProdID=1002 Rev=00.01

suggest uninstall the software 

and reinstall modem-manager

---

### Post by Tom 6 on 2011-11-16
Hi :)
Sorry i can't help with the actual question except to point to these guides on trouble-shooting
[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
I think i prefer the 1st of those 3.  

It might be worth posting a new question at Launchpad (the official forum) although i think i got my best answers from here.  A link to launchpad here ...
[https://answers.launchpad.net/ubuntu/+addquestion](https://answers.launchpad.net/ubuntu/+addquestion)

Also for hardware and other issues that might also be an issue in other versions of Gnu&Linux, not just Ubuntu, then this link is often good
[http://www.linuxquestions.org](http://www.linuxquestions.org)

This is quite an old thread now and often forums respond better to newer questions.  UbuntuForums is clearly different and does things better.  Simply posting a comment appears to "bump the thread" back up to the top of the list.  

I think you need to start a new thread about your specific device.  
Regards from
Tom :)

---

### Post by VlatkoB on 2011-11-16
Hi alexfish,

Reinstalling modem-manager returned the system to what it was.

Yes, I have noticed the difference in product ID, but thought that maybe my device is supported as well. 

Couldn't find much info about 117.

Thanks a lot. :-)

vlatko


> **alexfish said:**
> Hi VlatkoB 

your device is different to this thread[FONT=monospace]
your device [/FONT]P:  Vendor=**19d2** ProdID=**0117** Rev=00.00

the device on this thread P:  Vendor=19d2 ProdID=1002 Rev=00.01

suggest uninstall the software 

and reinstall modem-manager

---

### Post by Philly888 on 2012-02-11
I too am experiencing a problem on ubuntu 11.10

Both my new laptops have 11.10 and both of them can see the vodacom dongle but there is no transfer of information.

Any help?

regards

Philip

---

### Post by wavesailor on 2012-05-30
> **Philly888 said:**
> I too am experiencing a problem on ubuntu 11.10


This works on 11.10 for me - see this: [http://askubuntu.com/questions/129284/connection-problems-with-3g-dongle-vodafone-k3805-z/144051#144051](http://askubuntu.com/questions/129284/connection-problems-with-3g-dongle-vodafone-k3805-z/144051#144051)

Specifically the part where you disable arp

---

