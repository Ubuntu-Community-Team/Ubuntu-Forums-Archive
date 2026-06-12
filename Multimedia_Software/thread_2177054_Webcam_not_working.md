---
title: "Webcam not working"
date: 2013-09-27
forum: Multimedia Software
---

### Post by subhendu2 on 2013-09-27
[COLOR=#000000]I have a webcam attached to the USB of my desktop running 12.04. 
I tried to access the webcam with cheese , but didnot suceeded. I also tried VLC. But it only gave a black screen output. I tried to give as much data as possible 
Please help
```
robot@robot:~$ uname -a
```[/COLOR]
[COLOR=#000000]Linux robot 3.5.0-40-generic #62~precise1-Ubuntu SMP Fri Aug 23 17:59:10 UTC 2013 i686 i686 i386 GNU/Linux[/COLOR]
[COLOR=#000000]```
robot@robot:~$ lsusb[/COLOR]
```
[COLOR=#000000]Bus 001 Device 003: ID 18ec:3399 Arkmicro Technologies Inc. [/COLOR]
[COLOR=#000000]Bus 001 Device 008: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS][/COLOR]
[COLOR=#000000]Bus 002 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
```
 lsb_release -a 
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
```
robot@robot:~$ lspci
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
03:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
robot@robot:~$ cat /proc/bus/input/devices
```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=18ec Product=3399 Version=0100
N: Name="USB2.0 PC CAMERA"
P: Phys=usb-0000:00:1d.7-3/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0003 Vendor=046d Product=c05a Version=0111
N: Name="Logitech USB Optical Mouse"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

[COLOR=#000000]```
robot@robot:~$ cheese
```[/COLOR]
[COLOR=#000000](cheese:2371): Gdk-WARNING **: The program 'cheese' received an X Window System error.[/COLOR]
[COLOR=#000000]This probably reflects a bug in the program.[/COLOR]
[COLOR=#000000]The error was 'GLXBadContext'.[/COLOR]
[COLOR=#000000](Details: serial 153 error_code 169 request_code 153 minor_code 6)[/COLOR]
[COLOR=#000000](Note to programmers: normally, X errors are reported asynchronously;[/COLOR]
[COLOR=#000000]that is, you will receive the error a while after causing it.[/COLOR]
[COLOR=#000000]To debug your program, run it with the GDK_SYNCHRONIZE environment[/COLOR]
[COLOR=#000000]variable to change this behavior. You can then get a meaningful[/COLOR]
[COLOR=#000000]backtrace from your debugger if you break on the gdk_x_error() function.)[/COLOR]

[COLOR=#000000]```
robot@robot:~$ vlc[/COLOR]
```
[COLOR=#000000]VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)[/COLOR]
[COLOR=#000000][0x8106908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.[/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("adjust") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("adjust") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("adjust") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("adjust") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("adjust") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("adjust") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("adjust") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("extract") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("extract") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("posterize") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("colorthres") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("colorthres") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("colorthres") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("colorthres") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("sepia") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("sepia") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("invert") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("gradient") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("gradient") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("gradient") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("gradient") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("motionblur") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("motionblur") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("motiondetect") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("psychedelic") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("sharpen") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("sharpen") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("ripple") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("wave") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("transform") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("transform") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("rotate") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("rotate") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("puzzle") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("puzzle") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("puzzle") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("puzzle") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("magnify") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("clone") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("clone") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("wall") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("wall") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("wall") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("erase") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("erase") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("erase") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("erase") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("marq") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("marq") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("marq") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("logo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("logo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("logo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("logo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("logo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("gradfun") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("gradfun") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("grain") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("grain") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("mirror") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("gaussianblur") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("gaussianblur") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("antiflicker") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("antiflicker") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x8106908] main libvlc error: vlc_object_find_name("atmo") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]
[COLOR=#000000][0x819bd58] main playlist error: vlc_object_find_name("v4l2") is not safe![/COLOR]


**[COLOR=#000000]But I can access the webcamera using opencv & Python. [/COLOR]**
[COLOR=#000000]Where am I going wrong?[/COLOR]

---

### Post by subhendu2 on 2013-09-28
gUYS PLEASE HELP

---

### Post by varunendra on 2013-09-29
Please edit your original post to enclose the outputs in 'Code' box too. Just cut-paste the outputs within the same tag sets in which their respective commands are.

Have you tried guvcview yet? It is a substitute of cheese, a bit more advanced. To install it -
```
sudo apt-get install guvcview
```

Please also post the following outputs -
```
usb-devices
lsmod
```

---

### Post by coldraven on 2013-09-29
> **varunendra said:**
> Please edit your original post to enclose the outputs in 'Code' box too. Just cut-paste the outputs within the same tag sets in which their respective commands are.

Have you tried guvcview yet? It is a substitute of cheese, a bit more advanced. To install it -
```
sudo apt-get install guvcview
```

Please also post the following outputs -
```
usb-devices
lsmod
```

Run guvcview and try adjusting the brightness. If it works there is no need to save, just quit guvcview and you should be good to go.
Edit: Also, in guvcview, turn off any "Auto Level" check box.

---

### Post by zozio32 on 2013-10-05
Hi,

I am having the same problem.
No camera in cheese, and guvcview won't even start, saying that there is no device installed:
> Please make sure the camera is connected
and that the correct driver is installed.

here are the results of:
> zozio@ZozioJogafePC:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-31-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c077 Rev=72.00
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04f2 ProdID=1060 Rev=14.00
S:  Manufacturer=CHICONY
S:  Product=USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1058 ProdID=1100 Rev=01.65
S:  Manufacturer=Western Digital 
S:  Product=My Book         
S:  SerialNumber=57442D574341553432303035313938
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-31-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=058f ProdID=6366 Rev=01.00
S:  Manufacturer=Generic
S:  Product=Mass Storage Device
S:  SerialNumber=058F63666433
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-31-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:02:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.08
S:  Manufacturer=Linux 3.8.0-31-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:02:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


and > zozio@ZozioJogafePC:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     36906  1 
joydev                 17377  0 
arc4                   12615  2 
rt2800pci              18582  0 
hid_generic            12540  0 
keucr                  67351  0 
nouveau               943184  3 
snd_hda_codec_idt      70256  1 
usbhid                 47074  0 
rt2800lib              66507  1 rt2800pci
snd_hda_intel          39619  5 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  2 
snd_hda_codec         136498  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
coretemp               13355  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mxm_wmi                13021  1 nouveau
snd_timer              29425  2 snd_pcm,snd_seq
wmi                    19070  2 mxm_wmi,nouveau
bnep                   18036  2 
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54925  3 rt2x00pci,rt2800lib,rt2800pci
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              511019  2 mac80211,rt2x00lib
kvm                   443165  0 
ttm                    83187  1 nouveau
drm_kms_helper         49394  1 nouveau
drm                   286028  5 ttm,drm_kms_helper,nouveau
psmouse                95905  0 
mei                    41158  0 
rfcomm                 42641  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
bluetooth             228808  10 bnep,rfcomm
snd                    68876  20 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
aes_x86_64             17255  1 aesni_intel
parport_pc             28152  0 
ppdev                  17073  0 
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
i2c_algo_bit           13413  1 nouveau
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
soundcore              12680  1 snd
lpc_ich                17061  0 
serio_raw              13215  0 
mac_hid                13205  0 
microcode              22881  0 
video                  19390  1 nouveau
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
binfmt_misc            17500  1 
nls_iso8859_1          12713  3 
ahci                   25731  3 
libahci                31364  1 ahci
r8169                  67466  0 


any idea?

---

### Post by varunendra on 2013-10-06
> **zozio32 said:**
> No camera in cheese, and guvcview won't even start, saying that there is no device installed

As per the outputs you posted, it seems guvcview is telling you the truth. There is no camera listed in your output. Is it an external USB camera or an internal laptop one? Do you have any indication to believe it is not broken and is connected correctly?

If there is some sort of hardware switch for it, make sure it is turned on. If it is an internal webcam, make sure it is "enabled" in BIOS.

Please post back the output of -
```
cat /proc/bus/input/devices
```

---

### Post by zozio32 on 2013-10-06
its a new external camera (Pluscom UC480-R)
The integrated microphone works, as well as the led on the camera
> zozio@ZozioJogafePC:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=2000

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Rear Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input3
U: Uniq=
H: Handlers=event3 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input4
U: Uniq=
H: Handlers=event4 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Front Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input5
U: Uniq=
H: Handlers=event5 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Speaker Side"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input6
U: Uniq=
H: Handlers=event6 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Speaker CLFE"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Speaker Surround"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Speaker Front"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0003 Vendor=046d Product=c077 Version=0111
N: Name="Logitech USB Optical Mouse"
P: Phys=usb-0000:00:1a.0-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input10
U: Uniq=
H: Handlers=mouse0 event10 
B: PROP=0
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=04f2 Product=1060 Version=0111
N: Name="CHICONY USB Keyboard"
P: Phys=usb-0000:00:1a.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input11
U: Uniq=
H: Handlers=sysrq kbd event11 
B: PROP=0
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=04f2 Product=1060 Version=0111
N: Name="CHICONY USB Keyboard"
P: Phys=usb-0000:00:1a.0-1.2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input12
U: Uniq=
H: Handlers=kbd event12 
B: PROP=0
B: EV=10001f
B: KEY=4837fff072ff32d bf54444600000000 1 20c130b17c000 267bfad941dfed 9e168000004400 10000002
B: REL=40
B: ABS=100000000
B: MSC=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA NVidia HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
U: Uniq=
H: Handlers=event14 
B: PROP=0
B: EV=21
B: SW=140



basicallt, it seems that the camera does not exist at all for the system...

---

### Post by varunendra on 2013-10-06
Is this the type of camera you have : [http://www.aliexpress.com/item-img/NEW-30-0-MEGA-PIXEL-30-0M-6-LED-USB-PC-WEBCAM-MIC/587902620.html#](http://www.aliexpress.com/item-img/NEW-30-0-MEGA-PIXEL-30-0M-6-LED-USB-PC-WEBCAM-MIC/587902620.html#) ?

Do you notice any change in the outputs of lsusb or dmesg when you plug <--> unplug the camera? Try different USB ports.

And do you have a card reader attached to the computer? I'm a little suspicious about this device -
```
T: Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#= 3 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=058f ProdID=6366 Rev=01.00
S: Manufacturer=Generic
S: Product=Mass Storage Device
S: SerialNumber=058F63666433
C: #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```
If your camera is similar to the one I linked to, it has an inbuilt memory to store snapshots. The above storage maybe that one if you don't have a separate card reader attached. But then you should notice some change in the outputs of both lsusb and dmesg when plugging <--> unplugging the camera.

**PS:**
And please use 'Code' tags instead of 'Quote' tags for posting your outputs. You should edit your previous posts to do that now (please follow the "Using Code Tags" link in my signature to see how).

---

### Post by zozio32 on 2013-10-08
works by trying the USB ports on the back on the PC. I really couldn't imagine it would make a difference. Tahnks

---

### Post by varunendra on 2013-10-08
Aha, old hardware bug.

Front USB tends to lose power due to extra length of the wire that connects the front USB port to the motherboard. Asus and Gigabyte (I think most modern motherboards) deliver extra power to the front ports to compensate that, maybe yours is one of the older types that suffer this problem. The back ports are directly attached to the motherboard, so no problem there. :)

[s]Please mark the thread as [SOLVED] now that it is.[/s]
[COLOR="#FF0000"]EDIT: Nevermind, just realized it's not your thread, so you can't mark it solved.[/COLOR]

---

