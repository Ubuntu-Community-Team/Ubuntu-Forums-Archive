---
title: "dont autostartr gnome-volume-manager-gthumb"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by bastard79 on 2006-10-29
hello evryone

after dist-upgrade to 6.10 my canon a610 doesn't start automaticly when i conetc to usb as it was in 6.06.

when i manualy put 


marcin@ubuntu:~$ gnome-volume-manager-gthumb %h
5117: arguments to dbus_message_new_method_call() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 797.
This is normally a bug in some application using the D-Bus library.
libhal.c 995 : Couldn't allocate D-BUS message
error: libhal_device_get_property_type: (null): (null)

its fine works, but i want it should be start automatic.

dmesg log seems to detect cam properly

[17181407.448000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17181407.672000] usb 1-1: configuration #1 chosen from 1 choice
[17181412.184000] usb 1-1: USB disconnect, address 2

everything is ok, but it doesn't work as i want :(

please help me, what i have do wrong, or what packages i need to fix this "bug" in 6.10 ?

ps. cam is PTP - canon a610
ps2. sorry for my english, i hope you undertand my problem :)

---

### Post by dentaku65 on 2006-10-30
You can try ivman

Unplug the camera then:
```
sudo apt-get install ivman
```
Then:
```
sudo ivman
```
Plug the camera and see.

Hope this help

---

### Post by SirPecanGum on 2006-10-30
Excellent. Thank you very much!

---

### Post by bastard79 on 2006-10-31
> **dentaku65 said:**
> You can try ivman

Unplug the camera then:
```
sudo apt-get install ivman
```
Then:
```
sudo ivman
```
Plug the camera and see.

Hope this help

thanks for reply, but unfortunately it's don't work for me :(


PS> to work i must have lvm2 or evms ??, i had this in dapper, but in edgy it was disabled at start by default so i purged this packages.
PS> whitch kernel module i need to run my camera ??
after  #cat /proc/bus/usb/devices
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04a9 ProdID=30fd Rev= 0.02
S:  Manufacturer=Canon Inc.
S:  Product=Canon Digital Camera
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 **Driver=(none)**
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=32ms

and when i'm typing manualy , i have

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04a9 ProdID=30fd Rev= 0.02
S:  Manufacturer=Canon Inc.
S:  Product=Canon Digital Camera
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 **Driver=usbfs**
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=32ms

---

