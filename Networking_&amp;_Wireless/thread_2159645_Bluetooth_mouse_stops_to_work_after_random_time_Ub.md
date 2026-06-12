---
title: "Bluetooth mouse stops to work after random time Ubuntu 13.04 on laptop"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by macmus on 2013-07-03
Hi,

Recently I bought bluetooth mouse as an addition to my ubuntu 13.04 with xfce.
The mouse paired strait away and kept going for some time.
After some time it lost a connection. Restarts of hcpi, deamon or even try to rediscover did not help.
The only cure was to restart my laptop, where everthing started to work (again for some time and then it stops)

When mouse stops to work in dmesg i see:

```
[  912.557942] Bluetooth: hci0 corrupted ACL packet
[  912.557990] Bluetooth: hci0 ACL packet for unknown connection handle 12
[  921.829716] Bluetooth: hci0 corrupted ACL packet
[  921.829751] Bluetooth: hci0 ACL packet for unknown connection handle 12
[  933.857641] Bluetooth: hci0 corrupted ACL packet
[  933.857680] Bluetooth: Frame is too short (len 1)
[  945.556674] Bluetooth: hci0 corrupted ACL packet
[  945.556801] Bluetooth: hci0 ACL packet for unknown connection handle 12
[  945.556805] Bluetooth: hci0 ACL packet for unknown connection handle 1
```

when i move mouse i see it tried to recconect. The dialog is stuck on  "Remote Name Req Complet" for some time.
And then there is a disconect, and again mouse tries to reconnect.

```
lech@HP-EliteBook:~$ hcidump 
HCI sniffer - Bluetooth packet analyzer ver 2.4
device: hci0 snap_len: 1028 filter: 0xffffffffffffffff
> HCI Event: Connect Request (0x04) plen 10
    bdaddr 00:1F:20:50:01:B4 class 0x002580 type ACL
> HCI Event: Command Status (0x0f) plen 4
    Accept Connection Request (0x01|0x0009) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 11 bdaddr 00:1F:20:50:01:B4 type ACL encrypt 0x00
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 11
    Features: 0xbc 0x02 0x04 0x38 0x08 0x00 0x00 0x00
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:1F:20:50:01:B4 name 'Dell BT Travel Mouse'
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 11 reason 0x16
    Reason: Connection Terminated by Local Host
> HCI Event: Connect Request (0x04) plen 10
    bdaddr 00:1F:20:50:01:B4 class 0x002580 type ACL
> HCI Event: Command Status (0x0f) plen 4
    Accept Connection Request (0x01|0x0009) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 12 bdaddr 00:1F:20:50:01:B4 type ACL encrypt 0x00
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 12
    Features: 0xbc 0x02 0x04 0x38 0x08 0x00 0x00 0x00
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:1F:20:50:01:B4 name 'Dell BT Travel Mouse'

```

When I remove the mouse and try to add it again I see it response but in linux the message show up that there was no response from applciation.

```

> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 11 bdaddr 00:1F:20:50:01:B4 type ACL encrypt 0x00
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 11
    Features: 0xbc 0x02 0x04 0x38 0x08 0x00 0x00 0x00
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:1F:20:50:01:B4 name 'Dell BT Travel Mouse'
> HCI Event: Command Complete (0x0e) plen 7
    Read RSSI (0x05|0x0005) ncmd 1
    status 0x00 handle 11 rssi -15
> HCI Event: Command Complete (0x0e) plen 7
    Read Link Quality (0x05|0x0003) ncmd 1
    status 0x00 handle 11 lq 255
> HCI Event: Command Complete (0x0e) plen 7
    Read Transmit Power Level (0x03|0x002d) ncmd 1
    status 0x00 handle 11 level 3
> HCI Event: Command Complete (0x0e) plen 7
    Read RSSI (0x05|0x0005) ncmd 1
    status 0x00 handle 11 rssi -13
> HCI Event: Command Complete (0x0e) plen 7
    Read Link Quality (0x05|0x0003) ncmd 1
    status 0x00 handle 11 lq 255
> HCI Event: Command Complete (0x0e) plen 7
    Read Transmit Power Level (0x03|0x002d) ncmd 1
    status 0x00 handle 11 level 3

```

and after a while we again see 

```

    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 11 reason 0x16
    Reason: Connection Terminated by Local Host


```

I would appreciate your help in this topic.

BR,
m.

---

### Post by Bucky Ball on 2013-07-04
I know this sounds insane and could be right off the money, but ...

My wife just bought a wireless mouse that had me bamboozled. After a short period of time, the mouse switches off to save battery power. To get it alive again you need to press the scroll wheel. Have you tried that? Does the mouse work fine then when you have a break and go back to it, it has stopped working?

As I say, could be totally off the mark just trying to help ... ;)

---

### Post by varunendra on 2013-07-04
> **macmus said:**
> The only cure was to restart my laptop, where everthing started to work (again for some time and then it stops)

Hmm.. if you have plenty of time to waste on possibly fruitless experiments : [http://ubuntuforums.org/showthread.php?t=2142366&p=12665382#post12665382](http://ubuntuforums.org/showthread.php?t=2142366&p=12665382#post12665382)

---

### Post by macmus on 2013-07-04
> **Bucky Ball said:**
> . After a short period of time, the mouse switches off to save battery power. 

Well as you can see there are events coming to laptop when I move mouse so i don't think that is a problem here.

How else I can check logs for bluetooth, maybe it's conflicting with something etc..

---

### Post by macmus on 2013-07-04
> **varunendra said:**
> Hmm.. if you have plenty of time to waste on possibly fruitless experiments : [http://ubuntuforums.org/showthread.php?t=2142366&p=12665382#post12665382](http://ubuntuforums.org/showthread.php?t=2142366&p=12665382#post12665382)

i see in dmesg when adding mouse for first time:

```

[  218.395387] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  218.395398] Bluetooth: HIDP socket layer initialized
[  218.865333] hid-generic 0005:046D:B006.0001: unknown main item tag 0x0
[  218.865405] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:12/input16
[  218.865581] hid-generic 0005:046D:B006.0001: input,hidraw0: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f

```


i see it is avaialbe in proc bus when it works.

```

lech@HP-EliteBook:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: PROP=0
B: EV=120013
B: KEY=20000 20000000020 0 0 500f02100002 3803078f900d401 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="ST LIS3LV02DL Accelerometer"
P: Phys=lis3lv02d/input0
S: Sysfs=/devices/platform/lis3lv02d/input/input4
U: Uniq=
H: Handlers=event4 js0 
B: PROP=0
B: EV=9
B: ABS=7

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="HP WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: PROP=0
B: EV=33
B: KEY=4000000000 0 1000700000000 2100400 0 0
B: MSC=10
B: SW=22

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=7"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input7
U: Uniq=
H: Handlers=event7 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Line"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=2000

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Dock Line Out"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input13
U: Uniq=
H: Handlers=mouse0 event13 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=04f2 Product=b2ef Version=5172
N: Name="HP HD Webcam [Fixed]"
P: Phys=usb-0000:00:1a.0-1.3/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input14
U: Uniq=
H: Handlers=kbd event14 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input15
U: Uniq=
H: Handlers=mouse1 event15 
B: PROP=9
B: EV=b
B: KEY=6420 30000 0 0 0 0
B: ABS=260800011000003

I: Bus=0005 Vendor=046d Product=b006 Version=0124
N: Name="Dell BT Travel Mouse"
P: Phys=b8:76:3f:db:05:2f
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:12/input16
U: Uniq=00:1f:20:50:01:b4
H: Handlers=mouse2 event16 
B: PROP=0
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=143
B: MSC=10


```

it seems that for some magical reason it disapears from there at some point.


When I start move mouse it goes to connection handler 12

```


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Dock Line Out"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=40


[ 1108.148515] Bluetooth: hci0 corrupted ACL packet
[ 1108.148553] Bluetooth: hci0 ACL packet for unknown connection handle 12
[ 1108.148558] Bluetooth: hci0 ACL packet for unknown connection handle 12
[ 1159.531342] Bluetooth: hci0 corrupted ACL packet
[ 1159.531384] Bluetooth: Frame is too short (len 1)
[ 1167.929756] Bluetooth: hci0 corrupted ACL packet
[ 1167.929799] Bluetooth: Frame is too long (len 8, expected len 5)
[ 1181.490929] Bluetooth: hci0 corrupted ACL packet
[ 1181.490980] Bluetooth: hci0 ACL packet for unknown connection handle 12


```

instead of 16 which is suppose to be assigned to bluetooth mouse.

Any reason why all of the suddent 12 take over handler from 16 ? Do I get this behaviour right ?

---

### Post by varunendra on 2013-07-04
> **macmus said:**
> ..it seems that for some magical reason it disapears from there at some point.
Maybe connection error, bad packets, driver crash.... who knows? I don't.

As for the connection handler, I don't even understand most of it. All I know is that in my experiments, resetting the hub on which bluetooth resides resets bluetooth itself, and the adapter starts working again. However, the connected devices need to be connected again. If this connection is done automatically, then a power-cycle on the mouse should do the job. Definitely annoying, but still better than a system reboot :(

The USB hub in your case is "0000:00:1d.0" -
```

[  218.865405] input: Dell BT Travel Mouse as /devices/pci0000:00/**[COLOR="#B22222"]0000:00:1d.0[/COLOR]**/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:12/input16

```
So you may try-
```
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
```
then -
```
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/bind
```

If you find an explanation to why the problem occurs, please share with us. Thanks!

---

### Post by macmus on 2013-07-05
hmm i do not have ehci :(

```

root@HP-EliteBook:~# echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
tee: /sys/bus/pci/drivers/ehci_hcd/unbind: No such file or directory
0000:00:1d.0root@HP-E
root@HP-EliteBook:~# 
root@HP-EliteBook:~# 
root@HP-EliteBook:~# 
root@HP-EliteBook:~# cat /sys/bus/pci
pci/         pci_express/ 
root@HP-EliteBook:~# cat /sys/bus/pci
pci/         pci_express/ 
root@HP-EliteBook:~# cat /sys/bus/pci/
devices/            drivers_autoprobe   rescan              slots/              
drivers/            drivers_probe       resource_alignment  uevent              
root@HP-EliteBook:~# cat /sys/bus/pci/
devices/            drivers_autoprobe   rescan              slots/              
drivers/            drivers_probe       resource_alignment  uevent              
root@HP-EliteBook:~# cat /sys/bus/pci/

```

---

### Post by varunendra on 2013-07-05
> **macmus said:**
> hmm i do not have ehci :(

Uh.. it was an assumption, I forgot to ask to confirm which one you have in use. It maybe uhci, xhci.. just run -
[code]usb-devices[code]
to see which one is used for that bus. Replace ehci with that one.

---

### Post by macmus on 2013-07-05
how do i know which one is for bluetooth ?

```

lech@HP-EliteBook:~$ usb-devices 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-26-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b2ef Rev=51.72
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=HP HD Webcam [Fixed]
S:  SerialNumber=SN0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-26-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=21e1 Rev=01.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM20702A0
S:  SerialNumber=B8763FDB052F
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-26-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.08
S:  Manufacturer=Linux 3.8.0-26-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

---

### Post by macmus on 2013-07-05
both options do nothing.
```

root@HP-EliteBook:~# usb-devices | grep ci
S:  Manufacturer=Linux 3.8.0-26-generic ehci_hcd
S:  Manufacturer=Linux 3.8.0-26-generic ehci_hcd
S:  Manufacturer=Linux 3.8.0-26-generic xhci_hcd
S:  Manufacturer=Linux 3.8.0-26-generic xhci_hcd
root@HP-EliteBook:~# 
root@HP-EliteBook:~# 
root@HP-EliteBook:~# 
root@HP-EliteBook:~# echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
tee: /sys/bus/pci/drivers/ehci_hcd/unbind: No such file or directory
0000:00:1d.0root@HP-EliteBook:~# echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/xhci_hcd/unbind
0000:00:1d.0tee: /sys/bus/pci/drivers/xhci_hcd/unbind: No such device

```

---

### Post by varunendra on 2013-07-05
> **macmus said:**
> ```

tee: /sys/bus/pci/drivers/ehci_hcd/unbind: No such file or directory
```

That's strange! Read through the posts so far more thoroughly and everything suggests that the bluetooth adapter is located on USB bus=2 on pci address "0000:00:1d.0", which is being controlled by ehci_hcd driver.

Let's find out the typical way -
```
find /sys/bus -name "ehci_hcd" -type d
```

What does it return?

---

### Post by macmus on 2013-07-05
```

lech@HP-EliteBook:~$ sudo find /sys/bus -name "ehci*"
/sys/bus/pci/drivers/ehci-pci
/sys/bus/platform/drivers/ehci-platform

```


This is what I get.

---

### Post by macmus on 2013-07-05
ok i found out :P

```

lech@HP-EliteBook:~$ echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/bind
0000:00:1d.0lech@HP-EliteBook:~$ 
lech@HP-EliteBook:~$ 
lech@HP-EliteBook:~$ echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
0000:00:1d.0lech@HP-EliteBook:~$ 

```

I did try to pair but same result... Once it gone only restarts helps...:(

---

### Post by varunendra on 2013-07-05
> **macmus said:**
> ok i found out :P

```

lech@HP-EliteBook:~$ echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/**[COLOR="#FF0000"]ehci-pci[/COLOR]**/bind
0000:00:1d.0lech@HP-EliteBook:~$ 
lech@HP-EliteBook:~$ 
lech@HP-EliteBook:~$ echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
0000:00:1d.0lech@HP-EliteBook:~$ 

```

I did try to pair but same result... Once it gone only restarts helps...:(

Now it's getting 'little' over my head. The output of usb-devices (and standard way of calling it) clearly lists the driver as "ehci_hcd".

Anyway, if you really actually tried the commands in the above sequence, you ended up 'removing' the driver from the bus. The sequence of running those commands should be opposite (first you 'unbind', THEN 'bind' again). This is in consistence to your statement that the command (sequence) makes it gone, and only a reboot enables it again.

Also, since I'm not sure about whether we got it right, I think you should manually browse to the /sys/bus/pci/drivers/ehci-pci/ directory, and see if the "0000:00:1d.0" 'link' appears there. If not, we're trying at a wrong address. (oh, but then again, that's the only address we've got ! So it must be the correct one !)

---

### Post by macmus on 2013-07-05
sorry the seqeunce is wrong .. I tried it multiple times.

Each time I use unbind the icon is disapering from tray and when I use bind it shows up again, so i belive this is correct.

I tried with standard bluetooth-aplet instead of bluemon. Its did not help. I have same behaviour.

---

### Post by macmus on 2013-07-05
hmm i did update to new kernel

and now I see in dmesg shortly before bluetooth got disconnected:

```

[ 1733.173754] hub 2-1:1.0: port 6 disabled by hub (EMI?), re-enabling...
[ 1733.262006] usb 2-1.6: reset full-speed USB device number 3 using ehci-pci
[ 1733.355673] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[ 1733.355683] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[ 1733.355698] usb 2-1.6: USB disconnect, device number 3
[ 1733.565252] usb 2-1.6: new full-speed USB device number 4 using ehci-pci
[ 1733.661454] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
[ 1733.661463] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1733.661467] usb 2-1.6: Product: BCM20702A0
[ 1733.661471] usb 2-1.6: Manufacturer: Broadcom Corp
[ 1733.661474] usb 2-1.6: SerialNumber: B8763FDB052F

```

what is going on ...

---

### Post by macmus on 2013-07-05
```

Jul  5 18:29:35 HP-EliteBook kernel: [ 6079.630753] hub 2-1:1.0: port 6 disabled by hub (EMI?), re-enabling...
Jul  5 18:29:35 HP-EliteBook kernel: [ 6079.718067] usb 2-1.6: reset full-speed USB device number 3 using ehci-pci
Jul  5 18:29:35 HP-EliteBook kernel: [ 6079.811647] btusb 2-1.6:1.0: no reset_resume for driver btusb?
Jul  5 18:29:35 HP-EliteBook kernel: [ 6079.811655] btusb 2-1.6:1.1: no reset_resume for driver btusb?
Jul  5 18:29:35 HP-EliteBook kernel: [ 6079.811668] usb 2-1.6: USB disconnect, device number 3
Jul  5 18:29:35 HP-EliteBook bluetoothd[1203]: Adapter /org/bluez/1203/hci0 has been disabled
Jul  5 18:29:35 HP-EliteBook bluetoothd[1203]: Unregister path: /org/bluez/1203/hci0
Jul  5 18:29:35 HP-EliteBook bluetoothd[1203]: Endpoint unregistered: sender=:1.85 path=/MediaEndpoint/A2DPSink
Jul  5 18:29:35 HP-EliteBook bluetoothd[1203]: Endpoint unregistered: sender=:1.85 path=/MediaEndpoint/A2DPSource
Jul  5 18:29:35 HP-EliteBook bluetoothd[1203]: Endpoint unregistered: sender=:1.85 path=/MediaEndpoint/HFPAG
Jul  5 18:29:35 HP-EliteBook bluetoothd[1203]: Endpoint unregistered: sender=:1.85 path=/MediaEndpoint/HFPHS
Jul  5 18:29:36 HP-EliteBook kernel: [ 6080.041426] usb 2-1.6: new full-speed USB device number 5 using ehci-pci
Jul  5 18:29:36 HP-EliteBook kernel: [ 6080.137798] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
Jul  5 18:29:36 HP-EliteBook kernel: [ 6080.137806] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul  5 18:29:36 HP-EliteBook kernel: [ 6080.137810] usb 2-1.6: Product: BCM20702A0
Jul  5 18:29:36 HP-EliteBook kernel: [ 6080.137813] usb 2-1.6: Manufacturer: Broadcom Corp
Jul  5 18:29:36 HP-EliteBook kernel: [ 6080.137816] usb 2-1.6: SerialNumber: B8763FDB052F
Jul  5 18:29:36 HP-EliteBook mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6"
Jul  5 18:29:36 HP-EliteBook mtp-probe: bus: 2, device: 5 was not an MTP device
Jul  5 18:29:36 HP-EliteBook bluetoothd[1203]: Adapter /org/bluez/1203/hci0 has been enabled
Jul  5 18:29:36 HP-EliteBook bluetoothd[1203]: Endpoint registered: sender=:1.85 path=/MediaEndpoint/HFPAG
Jul  5 18:29:36 HP-EliteBook bluetoothd[1203]: Endpoint registered: sender=:1.85 path=/MediaEndpoint/HFPHS
Jul  5 18:29:36 HP-EliteBook bluetoothd[1203]: Endpoint registered: sender=:1.85 path=/MediaEndpoint/A2DPSource
Jul  5 18:29:36 HP-EliteBook bluetoothd[1203]: Endpoint registered: sender=:1.85 path=/MediaEndpoint/A2DPSink
Jul  5 18:29:41 HP-EliteBook kernel: [ 6085.680849] Bluetooth: hci0 corrupted ACL packet
Jul  5 18:29:41 HP-EliteBook kernel: [ 6085.680883] Bluetooth: hci0 ACL packet for unknown connection handle 12

```

---

### Post by macmus on 2013-07-05
i have just discovered that when i go into suspend and then back open a cover mosue is working again.

why usb is getting disconencted as ger above logs/

---

### Post by varunendra on 2013-07-06
> **macmus said:**
> why usb is getting disconencted as ger above logs/

Because that's exactly what we are trying - logical disconnect --> reconnect the usb hub on which the bluetooth adapter is located. And that seems to be working fine -
> **macmus said:**
> 
```

[ 1733.661454] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
[ 1733.661463] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1733.661467] usb 2-1.6: Product: **[COLOR="#B22222"]BCM20702A0[/COLOR]**
[ 1733.661471] usb 2-1.6: Manufacturer: Broadcom Corp
[ 1733.661474] usb 2-1.6: SerialNumber: B8763FDB052F

```

Once it is done, do you see the mouse again in -
```
cat /proc/bus/input/devices
```??
It will be missing after "unbind", but should be back after "bind" and re-connecting the mouse (the unbind-bind cycles only resets the bluetooth adapter, any connections to it will need to be re-established).

---

### Post by macmus on 2013-07-06
no no I think u got me wrong on this one.
When mouse stops working I see this message poping up in dmesg.
I don't do unbind to get it....

I simply work on laptop with mouse... aftersome time mouse stops to work .. and in the same time I see this message poping up.

This message is not inicialized by me :(

I did download new kernel 3.10 and 3.8.26, could that have any impact ? I'm still using old version though ..

I also see that when it disconnects some icon is showing for a short time in system tray. 
It is just a split of second so i have no idea what is that.

---

### Post by varunendra on 2013-07-06
Well then it is doing the same thing all by itself. I can't say how or why, but as per the logs, it is exactly the same thing that we are trying with the "unbind --> bind" cycle.

As per logs in your posts #16, #17, the last status is clearly that the bluetooth adapter was (again) detected and enabled. Like I said, whether it is happening by itself (which would be very strange and surprising to me) or initiated by our commands, the devices connected to that adapter will need to be re-connected. That also implies that the device (mouse in your case) will have to be reset.

All of this problem seems to be a known bug : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1036401](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1036401)
...we are just trying to work out a workaround that works perfectly well on my laptop, but I never tried a bluetooth mouse, only mobile phones. But I think all the bluetooth mice have a power off button on them that can be used as a hard reset. So once these messages appear (by themselves or after the commands), power cycle the mouse and check "cat /proc/bus/input/devices" to see if the mouse gets connected again.

I'd like to add that I've used my mobile phone in HID device mode (that controls the pointer like a mouse), and the above procedure works with that. The mobile then appears in "/proc/bus/input/devices" just like a mouse. And needs to be re-connected after the "unbind-bind" cycle (the mobile needs about 4-6 seconds before I can attempt a re-connect from bluetooth applet in the laptop).

---

### Post by macmus on 2013-07-06
well... even when it's reenabling itselfe  I still cannot use it. 
Even If i re-pair it it won't allow to do that.. I have to close and open a lid, the mouse works again...

Any reasons why ?

---

### Post by varunendra on 2013-07-06
> **macmus said:**
> well... even when it's reenabling itselfe  I still cannot use it. 
Even If i re-pair it it won't allow to do that.. I have to close and open a lid, the mouse works again...

Any reasons why ?
Most probably at least one of the drivers handling one of the involved components needs to be reset as well. But that should happen in a sleep --> wake cycle (module gets suspended, then resumed again), not just lid closing --> opening (of course unless the laptop is set to immediately going to sleep on lid closing).

We had an error message about btusb in the dmesg, we can try to start from there. What is the output of -
```
cat /sys/module/btusb/parameters/reset
```
? It should be "Y". If it is, then we may have to try resetting all the involved modules that handle bluetooth/mouse, but since many of them are interdependent, it may take quite some experimenting to see which ones have to be unloaded --> reloaded and in which sequence.

In my experiments once, I found it to be at lease six different drivers (don't remember, but any six of - usbhid, hid, hidp, ath3k, btusb, bluetooth, rfcomm, bnep) in a particular sequence because they were interdependent somehow. But I found it easier to just reset the hub as we are doing here. Didn't need to reset drivers after that, but your case is clearly much different than mine.

If you wish to try that, post back the full output of "lsmod". If this works, we can write a small script to do all this in one go (reset hub, reset driver(s)).

Not only drivers, it may also be the bluetooth daemon that probably gets confused. To reset that, you may use -
```
sudo service bluetooth restart
```
to see if it can do the magic.

Another way to test whether it is just the mouse or entire bluetooth functionality is to try pairing a new device (like a mobile phone) after resetting the hub. If it fails too, then we are still missing something in the bluetooth reset process. If it works, then probably it is drivers specific to the mouse, or the daemon resetting above that should work.

Remember, we are dealing with a bug here that frequently keeps resurrecting itself, and my tested workaround has failed to work for you. So we are now mostly shooting in the dark, with whatever leads we can get. I'd be happy to help you try whatever we can, but I know you may not have plenty of time/interest to go through this. So it's up to you how far you wish to go, I just wanted to let you know that while I'm not very certain about things at this point, I would love to try different things if you wish.

---

### Post by macmus on 2013-07-06
I'm avaialbe to do this debuging.

```

lech@HP-EliteBook:~$ cat /sys/module/btusb/parameters/reset
Y

```

I will post you detaisl about reset the daemon, once the bluetooth driver brakes again.

---

### Post by varunendra on 2013-07-07
In the meanwhile you can post the full output of -
```
lsmod
```

---

### Post by macmus on 2013-07-08
ok the mouse went out I did unbind bind again and restart bluetooth service and it did not help out.

```

[ 9933.534203] hub 2-1:1.0: port 6 disabled by hub (EMI?), re-enabling...
[ 9933.619034] usb 2-1.6: reset full-speed USB device number 3 using ehci-pci
[ 9933.712457] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[ 9933.712466] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[ 9933.712478] usb 2-1.6: USB disconnect, device number 3
[ 9933.942509] usb 2-1.6: new full-speed USB device number 8 using ehci-pci
[ 9934.038335] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
[ 9934.038343] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9934.038347] usb 2-1.6: Product: BCM20702A0
[ 9934.038350] usb 2-1.6: Manufacturer: Broadcom Corp
[ 9934.038353] usb 2-1.6: SerialNumber: B8763FDB052F
[ 9942.768763] Bluetooth: hci0 corrupted ACL packet
[ 9942.768792] Bluetooth: hci0 ACL packet for unknown connection handle 12
[ 9945.236711] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:30:96:13:b2:bc:08:00 SRC=10.138.120.253 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=22605 PROTO=2 
[ 9945.964718] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:00:aa:ce:b0:d1:08:00 SRC=10.138.120.242 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=15508 PROTO=2 
[ 9945.966321] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:00:aa:ce:b0:d1:08:00 SRC=10.138.120.242 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=15508 PROTO=2 
[ 9954.888333] Bluetooth: hci0 corrupted ACL packet
[ 9954.888354] Bluetooth: hci0 ACL packet for unknown connection handle 11
[ 9954.888360] Bluetooth: Frame is too long (len 8, expected len 5)
[ 9974.309771] init: patchram main process (8341) terminated with status 5
[ 9980.881620] Bluetooth: hci0 corrupted ACL packet
[ 9980.881630] Bluetooth: hci0 ACL packet for unknown connection handle 12
[ 9988.317523] Bluetooth: hci0 ACL packet for unknown connection handle 16
[10005.131567] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:30:96:13:b2:bc:08:00 SRC=10.138.120.253 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=23105 PROTO=2 
[10005.231261] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:1a:4b:7a:a5:1a:08:00 SRC=10.138.120.123 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=23892 PROTO=2 
[10009.628440] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:00:aa:ce:b0:d1:08:00 SRC=10.138.120.242 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=15663 PROTO=2 
[10026.238352] ehci-pci 0000:00:1d.0: remove, state 1
[10026.238366] usb usb2: USB disconnect, device number 1
[10026.238370] usb 2-1: USB disconnect, device number 2
[10026.238374] usb 2-1.6: USB disconnect, device number 8
[10026.240536] usb 2-1: clear tt 1 (9082) error -19
[10026.261746] ehci-pci 0000:00:1d.0: USB bus 2 deregistered
[10031.557866] ehci-pci 0000:00:1d.0: setting latency timer to 64
[10031.557877] ehci-pci 0000:00:1d.0: EHCI Host Controller
[10031.557891] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[10031.557919] ehci-pci 0000:00:1d.0: debug port 2
[10031.561850] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[10031.561873] ehci-pci 0000:00:1d.0: irq 16, io mem 0xd4738000
[10031.570797] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[10031.570837] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[10031.570841] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[10031.570845] usb usb2: Product: EHCI Host Controller
[10031.570848] usb usb2: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
[10031.570851] usb usb2: SerialNumber: 0000:00:1d.0
[10031.571087] hub 2-0:1.0: USB hub found
[10031.571094] hub 2-0:1.0: 3 ports detected
[10031.882232] usb 2-1: new high-speed USB device number 2 using ehci-pci
[10032.014347] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[10032.014355] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[10032.014756] hub 2-1:1.0: USB hub found
[10032.014815] hub 2-1:1.0: 8 ports detected
[10032.285565] usb 2-1.6: new full-speed USB device number 3 using ehci-pci
[10032.381255] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
[10032.381278] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[10032.381283] usb 2-1.6: Product: BCM20702A0
[10032.381291] usb 2-1.6: Manufacturer: Broadcom Corp
[10032.381301] usb 2-1.6: SerialNumber: B8763FDB052F
[10035.700256] init: patchram main process (8662) terminated with status 5
[10043.666611] Bluetooth: hci0 corrupted ACL packet
[10043.666639] Bluetooth: hci0 ACL packet for unknown connection handle 12
[10062.839042] Bluetooth: hci0 corrupted ACL packet
[10062.839066] Bluetooth: hci0 ACL packet for unknown connection handle 11
[10062.839073] Bluetooth: Frame is too long (len 8, expected len 5)
[10065.026222] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:30:96:13:b2:bc:08:00 SRC=10.138.120.253 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=23677 PROTO=2 
[10065.101387] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:1f:29:7e:72:9a:08:00 SRC=10.138.120.79 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=10323 PROTO=2 
[10069.269178] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:00:aa:ce:b0:d1:08:00 SRC=10.138.120.242 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=15797 PROTO=2 
[10085.474949] Bluetooth: hci0 corrupted ACL packet
[10085.474978] Bluetooth: Frame is too short (len 1)
[10124.932926] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:30:96:13:b2:bc:08:00 SRC=10.138.120.253 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=24195 PROTO=2 
[10125.006748] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:1a:4b:7a:a5:1a:08:00 SRC=10.138.120.123 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=24983 PROTO=2

```

and lsmod

```

lech@HP-EliteBook:~$ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  2 
vboxdrv               320372  4 vboxnetadp,vboxnetflt,vboxpci
snd_usb_audio         140685  1 
snd_usbmidi_lib        24938  1 snd_usb_audio
usbhid                 47074  0 
hid_generic            12540  0 
hidp                   22292  0 
hid                   101002  3 hidp,hid_generic,usbhid
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  12 
btusb                  22474  0 
uvcvideo               80847  0 
bluetooth             228619  23 bnep,hidp,btusb,rfcomm
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
snd_hda_codec_hdmi     36913  1 
binfmt_misc            17500  1 
snd_hda_codec_idt      70256  1 
tpm_infineon           17410  0 
ip6t_REJECT            12545  1 
xt_hl                  12521  6 
ip6t_rt                12529  3 
nf_conntrack_ipv6      18335  7 
nf_defrag_ipv6         13201  1 nf_conntrack_ipv6
ipt_REJECT             12541  1 
xt_LOG                 17400  10 
xt_limit               12711  13 
xt_tcpudp              12603  18 
xt_addrtype            12635  4 
nf_conntrack_ipv4      14487  7 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_state               12578  14 
arc4                   12615  2 
ip6table_filter        12815  1 
ip6_tables             27025  1 ip6table_filter
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12620  0 
nf_nat                 25867  1 nf_nat_ftp
nf_conntrack_ftp       13342  1 nf_nat_ftp
nf_conntrack           83275  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_state,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iwldvm                241872  0 
iptable_filter         12810  1 
ip_tables              26995  1 iptable_filter
x_tables               29803  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_state,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
mac80211              606457  1 iwldvm
snd_hda_intel          39619  4 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
joydev                 17377  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
aesni_intel            55399  1 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
snd_timer              29425  2 snd_pcm,snd_seq
hp_accel               26012  0 
tpm_tis                18675  0 
lis3lv02d              20111  1 hp_accel
wmi                    19070  1 hp_wmi
mac_hid                13205  0 
input_polldev          13896  1 lis3lv02d
i915                  600396  4 
iwlwifi               173477  1 iwldvm
snd                    68876  22 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
video                  19390  1 i915
coretemp               13355  0 
drm_kms_helper         49394  1 i915
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
drm                   286028  5 i915,drm_kms_helper
psmouse                95870  0 
i2c_algo_bit           13413  1 i915
serio_raw              13215  0 
mei                    41158  0 
lpc_ich                17061  0 
microcode              22881  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
sdhci_pci              18590  0 
sdhci                  32522  1 sdhci_pci
ahci                   25731  2 
libahci                31364  1 ahci
e1000e                198832  0 

```

---

### Post by macmus on 2013-07-08
any idea how to go forward with that? :>

---

### Post by macmus on 2013-07-09
it seems to be similar behaviour to 

```

https://bugzilla.redhat.com/show_bug.cgi?id=528744

```

---

### Post by macmus on 2013-07-09
it seems to be similar behaviour to 

```

https://bugzilla.redhat.com/show_bug.cgi?id=528744
http://permalink.gmane.org/gmane.linux.kernel.commits.head/285695
http://comments.gmane.org/gmane.linux.kernel/1494393
http://www.gossamer-threads.com/lists/linux/kernel/1716114

```

workaround is 

"I deactivated it with usbcore.autosuspend=-1 appended to the kernel command line"

but where i should put this line ?

---

### Post by varunendra on 2013-07-09
Did the mouse show up in "cat /proc/bus/input/devices" after re-binding the ehci driver?.

If yes, I would try to remove --> reload the bluetooth driver and any other that looks like working with the bt mouse. As per lsmod, the bluetooth driver is already used by 4 different drivers. So they will have to be removed first to be able to safely remove "bluetooth". Then they will have to be reloaded in the reverse sequence (last removed loaded first). This will help in case a driver get confused and needs resetting after resetting the USB adapter.

These are the drivers in my "usual-suspects" list -
> **macmus said:**
> ```

lech@HP-EliteBook:~$ lsmod
Module                  Size  Used by
usbhid                 47074  0 
hid_generic            12540  0 
hidp                   22292  0 
hid                   101002  3 hidp,hid_generic,usbhid
bnep                   18036  2 
rfcomm                 42641  12 
btusb                  22474  0 
**[COLOR="#FF0000"]bluetooth[/COLOR]**             228619  23 **[COLOR="#FF0000"]bnep,hidp,btusb,rfcomm[/COLOR]**
....
psmouse                95870  0 

```

As for the patch update, I'll have to lookup myself where to find the updates about the so called "bluetooth stack" (and related drivers). Should be a git-hub or something alike, but right now, I've no idea.

---

### Post by varunendra on 2013-07-09
> **macmus said:**
> 
workaround is 

"I deactivated it with usbcore.autosuspend=-1 appended to the kernel command line"

but where i should put this line ?

To test it temporarily, bring up the Grub menu (if it doesn't come up by default) by pressing a key during boot, then press "e" to edit the boot line. Then type **usbcore.autosuspend=-1** at the end (and before the last "--") of the boot line. Make sure the line ends with the hypens that are in the last. Then Ctrl+X to boot with the option.

If it seems to work (or if you want to make it permanent anyway), add the usbcore.autosuspend=-1 line in the relevant line in /etc/default/grub file, then update grub. Here's how -

Open the '/etc/default/grub file -
```
gksu gedit /etc/default/grub
```

Then look for the line "**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**".

Add the parameter **usbcore.autosuspend=-1** in-between the quotes before **quiet splash**. It should look like -
```
GRUB_CMDLINE_LINUX_DEFAULT="usbcore.autosuspend=-1 quiet splash"
```
Proofread, save and close the file.

Now update grub -
```
sudo update-grub
```

On next boot, the os will boot with the parameter you added above. To reset it to default, just remove it again from the /etc/default/grub file and redo "update-grub".

Good luck!

---

### Post by macmus on 2013-07-09
ok the kernel option did not help :((

what is more mouse do not show up after restart, unbid, bind again in /proc/bus/input/device

the closing/opening lid after mouse failing to respond still solves the issue :) Is there any way to copy filimar beaviour in regards to bluetooth driver?

---

### Post by varunendra on 2013-07-09
> **macmus said:**
> Is there any way to copy filimar beaviour in regards to bluetooth driver?

There is definitely a way, only I don't yet know how/where to find it (it is a group of drivers that is set to "SUSPEND" at sleep). It can be any of the drivers I quoted in post #30, and/or can be embedded drivers like ehci.

Modifications to this list is added in /etc/pm/config.d, or /etc/pm/sleep.d directory. But I am yet to figure out where the original list (or dynamic selection script, whatever) is located. One possible location is /usr/lib/pm-utils directory. I may start looking (brute-forcing :( ) from there if couldn't find help on net. You should do the same.

---

### Post by macmus on 2013-07-09
I found out something more. When mouse stops working it seems it's not added back to x.org.
When it disconnects I see in log 3 lines:

```

root@HP-EliteBook:~# tail -3 /var/log/Xorg.0.log
[  7562.456] (II) config/udev: removing device Dell BT Travel Mouse
[  7562.480] (II) evdev: Dell BT Travel Mouse: Close
[  7562.480] (II) UnloadModule: "evdev"

```


when i close/open lid of laptop i see following lines sowing up:

```

[  7787.992] (II) PM Event received: Capability Changed
[  7791.408] (II) AIGLX: Suspending AIGLX clients for VT switch
[  7794.934] (II) Open ACPI successful (/var/run/acpid.socket)
[  7794.934] (II) AIGLX: Resuming AIGLX clients after VT switch
[  7794.934] (II) intel(0): switch to mode 1366x768 on pipe 0 using LVDS1
[  7795.044] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  7799.457] (II) config/udev: Adding input device Dell BT Travel Mouse (/dev/input/mouse2)
[  7799.457] (II) No input driver specified, ignoring this device.
[  7799.457] (II) This device may have been added with another device file.
[  7799.457] (II) config/udev: Adding input device Dell BT Travel Mouse (/dev/input/event16)
[  7799.457] (**) Dell BT Travel Mouse: Applying InputClass "evdev pointer catchall"
[  7799.457] (II) Using input driver 'evdev' for 'Dell BT Travel Mouse'
[  7799.457] (**) Dell BT Travel Mouse: always reports core events
[  7799.457] (**) evdev: Dell BT Travel Mouse: Device: "/dev/input/event16"
[  7799.457] (--) evdev: Dell BT Travel Mouse: Vendor 0x46d Product 0xb006
[  7799.457] (--) evdev: Dell BT Travel Mouse: Found 12 mouse buttons
[  7799.457] (--) evdev: Dell BT Travel Mouse: Found scroll wheel(s)
[  7799.457] (--) evdev: Dell BT Travel Mouse: Found relative axes
[  7799.457] (--) evdev: Dell BT Travel Mouse: Found x and y relative axes
[  7799.457] (II) evdev: Dell BT Travel Mouse: Configuring as mouse
[  7799.457] (II) evdev: Dell BT Travel Mouse: Adding scrollwheel support
[  7799.457] (**) evdev: Dell BT Travel Mouse: YAxisMapping: buttons 4 and 5
[  7799.457] (**) evdev: Dell BT Travel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  7799.457] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:11/input24/event16"
[  7799.457] (II) XINPUT: Adding extended input device "Dell BT Travel Mouse" (type: MOUSE, id 14)
[  7799.458] (II) evdev: Dell BT Travel Mouse: initialized for relative axes.
[  7799.458] (**) Dell BT Travel Mouse: (accel) keeping acceleration scheme 1
[  7799.458] (**) Dell BT Travel Mouse: (accel) acceleration profile 0
[  7799.458] (**) Dell BT Travel Mouse: (accel) acceleration factor: 2.000
[  7799.458] (**) Dell BT Travel Mouse: (accel) acceleration threshold: 4

```

maybe we should fix xorg instead somehow ?

---

### Post by varunendra on 2013-07-09
> **macmus said:**
> maybe we should fix xorg instead somehow ?

Not sure on this. To me it seems that xorg is only reacting on what is triggered by something else - maybe udev.

And what is this module - "evdev"? Can you locate it with "locate" or "find" commands?


**PS:**
Nice finding by the way. Looks most promising lead so far, not for cause, but for a possible workaround.

---

### Post by macmus on 2013-07-09
results below:

```

lech@HP-EliteBook:~$ sudo locate evdev
/usr/lib/pulse-3.0/modules/module-mmkbd-evdev.so
/usr/lib/xorg/modules/input/evdev_drv.so
/usr/share/X11/xkb/keycodes/evdev
/usr/share/X11/xkb/rules/evdev
/usr/share/X11/xkb/rules/evdev.extras.xml
/usr/share/X11/xkb/rules/evdev.lst
/usr/share/X11/xkb/rules/evdev.xml
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/11-evdev-trackpoint.conf
/usr/share/apport/package-hooks/source_xserver-xorg-input-evdev.py
/usr/share/bug/xserver-xorg-input-evdev
/usr/share/bug/xserver-xorg-input-evdev/script
/usr/share/doc/xserver-xorg-input-evdev
/usr/share/doc/xserver-xorg-input-evdev/changelog.Debian.gz
/usr/share/doc/xserver-xorg-input-evdev/copyright
/usr/share/man/man4/evdev.4.gz
/usr/src/linux-headers-3.10.0-031000-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.10.0-031000-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.10.0-031000-generic/include/config/usb/video/class/input/evdev.h
/usr/src/linux-headers-3.8.0-19-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.8.0-19-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.8.0-19-generic/include/config/usb/video/class/input/evdev.h
/usr/src/linux-headers-3.8.0-25-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.8.0-25-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.8.0-25-generic/include/config/usb/video/class/input/evdev.h
/usr/src/linux-headers-3.8.0-26-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.8.0-26-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.8.0-26-generic/include/config/usb/video/class/input/evdev.h
/var/lib/dpkg/info/xserver-xorg-input-evdev.list
/var/lib/dpkg/info/xserver-xorg-input-evdev.md5sums
lech@HP-EliteBook:~$ 
lech@HP-EliteBook:~$ 
lech@HP-EliteBook:~$ 
lech@HP-EliteBook:~$ sudo find / -name "evdev*"
/usr/share/X11/xkb/keycodes/evdev
/usr/share/X11/xkb/rules/evdev
/usr/share/X11/xkb/rules/evdev.lst
/usr/share/X11/xkb/rules/evdev.extras.xml
/usr/share/X11/xkb/rules/evdev.xml
/usr/share/man/man4/evdev.4.gz
/usr/lib/xorg/modules/input/evdev_drv.so
/usr/src/linux-headers-3.8.0-19-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.8.0-19-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.8.0-19-generic/include/config/usb/video/class/input/evdev.h
/usr/src/linux-headers-3.10.0-031000-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.10.0-031000-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.10.0-031000-generic/include/config/usb/video/class/input/evdev.h
/usr/src/linux-headers-3.8.0-26-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.8.0-26-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.8.0-26-generic/include/config/usb/video/class/input/evdev.h
/usr/src/linux-headers-3.8.0-25-generic/include/config/input/evdev.h
/usr/src/linux-headers-3.8.0-25-generic/include/config/usb/pwc/input/evdev.h
/usr/src/linux-headers-3.8.0-25-generic/include/config/usb/video/class/input/evdev.h

```

---

### Post by macmus on 2013-07-09
from wiki
```

evdev
From Wikipedia, the free encyclopedia
Jump to: navigation, search
Portal icon 	Linux portal

In computing, evdev (for event device) is a component of the Linux kernel for handling input (from keyboards, mice, joysticks, etc.) and a closely related input driver for the X.Org Server. The kernel component is glue code which translates input events from peripheral-specific drivers into a generic structure which the input driver can easily translate into X11 events. Thus every input device with a Linux driver is compatible with the X.Org input driver, making X.Org much easier to configure.

Most recent Linux distributions install evdev by default.[1]

Using evdev makes it easier for the X.Org server to support hotplugging of input devices and allows advanced input devices, like multi-button mice and multimedia keyboards, to work correctly. The previous approach involved a kernel-level sink device emulating a PS/2 mouse and an AT keyboard, which collected events from all input devices, while the X server was configured for one keyboard and one mouse.

```

---

### Post by macmus on 2013-07-09
when i unbind, bind, reset device do not show up

only closing, opening lid is reenebling it:

```

I: Bus=0005 Vendor=046d Product=b006 Version=0124
N: Name="Dell BT Travel Mouse"
P: Phys=b8:76:3f:db:05:2f
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:11/input28
U: Uniq=00:1f:20:50:01:b4
H: Handlers=mouse0 event4 
B: PROP=0
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=143
B: MSC=10

```

---

### Post by macmus on 2013-07-09
> **varunendra said:**
> 
If yes, I would try to remove --> reload the bluetooth driver and any other that looks like working with the bt mouse. As per lsmod, the bluetooth driver is already used by 4 different drivers. So they will have to be removed first to be able to safely remove "bluetooth". Then they will have to be reloaded in the reverse sequence (last removed loaded first). This will help in case a driver get confused and needs resetting after resetting the USB adapter.
These are the drivers in my "usual-suspects" list -
As for the patch update, I'll have to lookup myself where to find the updates about the so called "bluetooth stack" (and related drivers). Should be a git-hub or something alike, but right now, I've no idea.


how to unload and reload all of the drivers ?
I have never done such a trick :(

---

### Post by macmus on 2013-07-09
one more interesting thing:

It seems  each open/close of lid .. binds it to next input device... i have already input 27!!!

```

root@HP-EliteBook:~# dmesg  | grep input
[ 7638.841567] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:12/input22
[ 7638.841961] hid-generic 0005:046D:B006.0007: input,hidraw0: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f
[ 7648.868975] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:11/input23
[ 7648.869222] hid-generic 0005:046D:B006.0008: input,hidraw0: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f
[ 8352.995878] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:11/input24
[ 8352.996089] hid-generic 0005:046D:B006.0009: input,hidraw0: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f
[ 8450.612472] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:12/input25
[ 8450.612635] hid-generic 0005:046D:B006.000A: input,hidraw0: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f
[ 9057.276290] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:11/input26
[ 9057.276515] hid-generic 0005:046D:B006.000B: input,hidraw0: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f
[10341.928203] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:11/input27
[10341.929209] hid-generic 0005:046D:B006.000C: input,hidraw0: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f
[12465.096810] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:11/input28
[12465.097073] hid-generic 0005:046D:B006.000D: input,hidraw0: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f

```

because it bind to next one it works again... I may be paranoid but each time it works shorter .. then previsouly.

Is there a way how to clean this register of input devices?

---

### Post by varunendra on 2013-07-09
> **macmus said:**
> one more interesting thing:

It seems  each open/close of lid .. binds it to next input device... i have already input 27!!!
.....
Is there a way how to clean this register of input devices?
That is normal for removable devices. I think it is the kernel's own way of keeping records, we better not mess with that.
*(Try plugging-unplugging a usb device in the same port and monitor "dmesg". It's device id will increment in the same way each time, but it doesn't make it less stable)*

> **macmus said:**
> how to unload and reload all of the drivers ?
I have never done such a trick :(

Before explaining that, let me make it clear that this is an approach totally based on guess and assumptions.

Now, for example, to unload only the "bluetooth" module, we need to unload all the modules that are using it -
*[Note : Text after a '**[COLOR="#0000CD"]#[/COLOR]**' are comments, I've put them just to explain things.*
```
*[COLOR="#0000CD"]# Change to Root so you don't have to use "sudo" each time -[/COLOR]*
sudo su

*[COLOR="#0000CD"]# Stop the Bluetooth service so no drivers remain in use by it[/COLOR]*
service bluetooth stop

*[COLOR="#0000CD"]# Now remove the drivers[/COLOR]*
modprobe -rv btusb *[COLOR="#0000CD"]# Should make bt icon disappear[/COLOR]*
modprobe -rv bnep *[COLOR="#0000CD"]# This is the driver I suspect the most, but resetting others as well just because I'm paranoid..[/COLOR]*
modprobe -rv hidp
modprobe -rv rfcomm *[COLOR="#0000CD"]# This should also remove the "bluetooth" with it. If not, remove it manually -[/COLOR]*
modprobe -rv bluetooth *[COLOR="#0000CD"]# Shouldn't be needed. Post back if it gives errors.[/COLOR]*

*[COLOR="#0000CD"]# Reload the drivers in reverse sequence[/COLOR]*
modprobe -v bluetooth *[COLOR="#0000CD"]# Not needed if it was removed automatically[/COLOR]*
modprobe -v rfcomm
modprobe -v hidp
modprobe -v bnep
modprobe -v btusb *[COLOR="#0000CD"]# The BT systray icon should return with this[/COLOR]*

*[COLOR="#0000CD"]# Now restart the bluetooth service[/COLOR]*
service bluetooth start

*[COLOR="#0000CD"]# Exit root[/COLOR]*
exit
```

I am not sure whether the above should be done before or after resetting the hub (unbind - bind ehci), because I never needed the above at all. I'm also not sure whether or not it is going to help, especially after reading the **evdev** module part. So try both ways, and most important - keep the fingers as well as toes crossed ! ;)

---

### Post by macmus on 2013-07-10
Ok i used your script, but no good news :(
Did not help at all.

```

root@HP-EliteBook:/home/lech/scripts# cat bluereset 
#!/bin/bash

echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/bind
# Stop the Bluetooth service so no drivers remain in use by it
service bluetooth stop

# Now remove the drivers
modprobe -rv btusb # Should make bt icon disappear
modprobe -rv bnep # This is the driver I suspect the most, but resetting others as well just because I'm paranoid..
modprobe -rv hidp
modprobe -rv rfcomm # This should also remove the "bluetooth" with it. If not, remove it manually -
modprobe -rv bluetooth # Shouldn't be needed. Post back if it gives errors.

# Reload the drivers in reverse sequence
modprobe -v bluetooth # Not needed if it was removed automatically
modprobe -v rfcomm
modprobe -v hidp
modprobe -v bnep
modprobe -v btusb # The BT systray icon should return with this

# Now restart the bluetooth service
service bluetooth start

# Exit root
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/unbind
echo -n "0000:00:1d.0" | sudo tee /sys/bus/pci/drivers/ehci-pci/bind
#exit

```

and the result in dmesg:

```

[25426.998401] hid-generic 0005:046D:B006.001D: unknown main item tag 0x0
[25426.998521] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:12/input35
[25426.998965] hid-generic 0005:046D:B006.001D: input,hidraw3: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on b8:76:3f:db:05:2f
[25528.754857] hub 2-1:1.0: port 6 disabled by hub (EMI?), re-enabling...
[25528.841691] usb 2-1.6: reset full-speed USB device number 3 using ehci-pci
[25528.934977] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[25528.934985] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[25528.934996] usb 2-1.6: USB disconnect, device number 3
[25529.169048] usb 2-1.6: new full-speed USB device number 5 using ehci-pci
[25529.264854] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
[25529.264862] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[25529.264866] usb 2-1.6: Product: BCM20702A0
[25529.264869] usb 2-1.6: Manufacturer: Broadcom Corp
[25529.264872] usb 2-1.6: SerialNumber: B8763FDB052F
[25534.417021] Bluetooth: hci0 corrupted ACL packet
[25534.417045] Bluetooth: hci0 ACL packet for unknown connection handle 12
[25543.895707] ehci-pci 0000:00:1d.0: remove, state 4
[25543.895715] usb usb2: USB disconnect, device number 1
[25543.895716] usb 2-1: USB disconnect, device number 2
[25543.895718] usb 2-1.6: USB disconnect, device number 5
[25543.915185] ehci-pci 0000:00:1d.0: USB bus 2 deregistered
[25543.923802] ehci-pci 0000:00:1d.0: setting latency timer to 64
[25543.923809] ehci-pci 0000:00:1d.0: EHCI Host Controller
[25543.923816] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[25543.923834] ehci-pci 0000:00:1d.0: debug port 2
[25543.927742] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[25543.927755] ehci-pci 0000:00:1d.0: irq 16, io mem 0xd4738000
[25543.937227] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[25543.937291] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[25543.937293] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[25543.937294] usb usb2: Product: EHCI Host Controller
[25543.937295] usb usb2: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
[25543.937297] usb usb2: SerialNumber: 0000:00:1d.0
[25543.937403] hub 2-0:1.0: USB hub found
[25543.937406] hub 2-0:1.0: 3 ports detected
[25543.973177] usbcore: deregistering interface driver btusb
[25544.001251] NET: Unregistered protocol family 31
[25544.015872] Bluetooth: Core ver 2.16
[25544.015908] NET: Registered protocol family 31
[25544.015913] Bluetooth: HCI device and connection manager initialized
[25544.015926] Bluetooth: HCI socket layer initialized
[25544.015931] Bluetooth: L2CAP socket layer initialized
[25544.015944] Bluetooth: SCO socket layer initialized
[25544.025477] Bluetooth: RFCOMM TTY layer initialized
[25544.025488] Bluetooth: RFCOMM socket layer initialized
[25544.025490] Bluetooth: RFCOMM ver 1.11
[25544.030116] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[25544.030134] Bluetooth: HIDP socket layer initialized
[25544.034544] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[25544.034551] Bluetooth: BNEP filters: protocol multicast
[25544.034567] Bluetooth: BNEP socket layer initialized
[25544.038015] usbcore: registered new interface driver btusb
[25544.052385] init: patchram main process (9070) terminated with status 5
[25544.062393] ehci-pci 0000:00:1d.0: remove, state 1
[25544.062400] usb usb2: USB disconnect, device number 1
[25544.066428] ehci-pci 0000:00:1d.0: USB bus 2 deregistered
[25544.074032] ehci-pci 0000:00:1d.0: setting latency timer to 64
[25544.074039] ehci-pci 0000:00:1d.0: EHCI Host Controller
[25544.074044] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[25544.074060] ehci-pci 0000:00:1d.0: debug port 2
[25544.077941] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[25544.077950] ehci-pci 0000:00:1d.0: irq 16, io mem 0xd4738000
[25544.088944] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[25544.088985] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[25544.088990] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[25544.088994] usb usb2: Product: EHCI Host Controller
[25544.088997] usb usb2: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
[25544.089000] usb usb2: SerialNumber: 0000:00:1d.0
[25544.089225] hub 2-0:1.0: USB hub found
[25544.089232] hub 2-0:1.0: 3 ports detected
[25544.400362] usb 2-1: new high-speed USB device number 2 using ehci-pci
[25544.532432] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[25544.532440] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[25544.532714] hub 2-1:1.0: USB hub found
[25544.532786] hub 2-1:1.0: 8 ports detected
[25544.803650] usb 2-1.6: new full-speed USB device number 3 using ehci-pci
[25544.899222] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
[25544.899230] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[25544.899234] usb 2-1.6: Product: BCM20702A0
[25544.899237] usb 2-1.6: Manufacturer: Broadcom Corp
[25544.899240] usb 2-1.6: SerialNumber: B8763FDB052F
[25547.312679] Bluetooth: hci0 corrupted ACL packet

```


as you can see restart happens and hci currpted ACL packets shows up again :(

---

### Post by macmus on 2013-07-10
for me it would be rather now a quation how to make it back in devices list after mouse reinialize itselfe.

I'm reading now about EMI at this would be more like HW issue with mouse itselfe. 
However linux should reattach it automaticly ,but it does not ..

this issue is comming back thruout history of linux e.g 

[http://forums.fedoraforum.org/archive/index.php/t-244660.html](http://forums.fedoraforum.org/archive/index.php/t-244660.html)
[http://forums.m-audio.com/archive/index.php/t-16441.html](http://forums.m-audio.com/archive/index.php/t-16441.html)

or even recent :

[https://bbs.archlinux.org/viewtopic.php?id=163730](https://bbs.archlinux.org/viewtopic.php?id=163730)

have not found yet if anyone solve it ...

it all the cases you can see however that bluetooth device is added shortly after, in case of ubuntu this does not happen....!!!

---

### Post by macmus on 2013-07-10
> **varunendra said:**
>  especially after reading the **evdev** module part. So try both ways, and most important - keep the fingers as well as toes crossed ! ;)

this part is interesting for me:

```

[B][  799.457] (II) config/udev: Adding input device Dell BT Travel Mouse (/dev/input/mouse2)
[  7799.457] (II) No input driver specified, ignoring this device.[/B]
[  7799.457] (II) This device may have been added with another device file.
[  7799.457] (II) config/udev: Adding input device Dell BT Travel Mouse (/dev/input/event16)
[  7799.457] (**) Dell BT Travel Mouse: Applying InputClass "evdev pointer catchall"

```

why ?

---

### Post by macmus on 2013-07-10
i'm continuing my investigation:

when i move my mouse with blueooth dump i can see:

```

> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(d): cid 0x0041 len 8 [psm 0]
      A1 02 00 01 10 00 00 00 
> ACL data: handle 12 flags 0x02 dlen 12
    L2CAP(d): cid 0x0041 len 8 [psm 0]
      A1 02 00 01 00 00 00 00 
> **ACL data: handle 12 **flags 0x02 dlen 12
    L2CAP(d): cid 0x0041 len 8 [psm 0]
      A1 02 00 00 10 00 00 00 

```

which means handle 12 is a usual receiver.

when mouse stop working in dmesg I can see:

```

[29613.906151] Bluetooth: hci0 corrupted ACL packet
[29613.906173] Bluetooth: hci0 ACL packet for unknown connection handle 12

```

---

### Post by macmus on 2013-07-10
ok few more findings! :) i think i may found a cause of this but I will need some expert from udev to help me debug it:

when everthing works we can see (shortly after opening laptop, after coming from suspend)

```


:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 **Dev#=  3** Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=21e1 Rev=01.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM20702A0
S:  SerialNumber=B8763FDB052F
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

[30171.941852] usb 1-1.3: reset high-speed USB device **number 3** using ehci-pci
[30172.045501] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[30172.053486] ata6: SATA link down (SStatus 0 SControl 300)
[30172.061493] ata5: SATA link down (SStatus 0 SControl 300)
[30172.105549] usb 2-1.6: reset full-speed USB device number 3 using ehci-pci
[30172.178762] ata2.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[30172.181677] ata2.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[30172.181697] ata2.00: configured for UDMA/100
[30172.199240] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[30172.199243] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[30172.269233] usb 1-1.2: reset full-speed USB device number 6 using ehci-pci
[30172.391071] psmouse serio1: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[30173.143630] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[30173.666488] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[30173.668074] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[30173.669983] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[30173.670182] ata1.00: configured for UDMA/133

```

```

lech@HP-EliteBook:~$ usb-devices  | grep  Dev#=
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
**T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 0**
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
**T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  3 Spd=12  MxCh= 0**
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4

```

the first 3 is my web cammera:
```

T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b2ef Rev=51.72
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=HP HD Webcam [Fixed]
S:  SerialNumber=SN0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

```

the other 3 is bluetooth mouse 
bus input
```

I: Bus=0005 Vendor=046d Product=b006 Version=0124
N: Name="Dell BT Travel Mouse"
P: Phys=b8:76:3f:db:05:2f
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/bluetooth/hci0/hci0:12/input37
U: Uniq=00:1f:20:50:01:b4
H: Handlers=mouse3 event6 
B: PROP=0
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=143
B: MSC=10

```

when its stop working it resets device number 3 and reinisalize the usb chipset BCM20702A0 on as device 5 which causes bluetooth not working.
That is why my dump got disconencted and because all events seems to be addressed old handler still!

```

[29607.386090] usb 2-1.6: reset full-speed USB device number 3 using ehci-pci
[29607.479544] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[29607.479552] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[29607.479563] usb 2-1.6: USB disconnect, device number 3
[29607.693517] usb 2-1.6: new full-speed USB device number 5 using ehci-pci
[29607.789069] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
[29607.789072] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[29607.789074] usb 2-1.6: Product: BCM20702A0
[29607.789076] usb 2-1.6: Manufacturer: Broadcom Corp
[29607.789077] usb 2-1.6: SerialNumber: B8763FDB052F
[29613.906151] Bluetooth: hci0 corrupted ACL packet

```

bluetooth chipset moved to Dev #5
```

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=21e1 Rev=01.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM20702A0
S:  SerialNumber=B8763FDB052F
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

```
```

root@HP-EliteBook:/home/lech/scripts# usb-devices | grep Dev
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
**T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 0**
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
**T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=01 Dev#=  5 Spd=12  MxCh= 0**
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4

```

when I close/open lid is again become Dev 3 and mouse starts responding again (and we go to begning of this post :) )

I see couple ofthings here:

1. EMI is cased because WebCamera and Bluetooth chipset is defined as some Device #3
2. Bluetooth stops responding becasue new device is diffrent then old one after reasiging 

Solution: ( I have no idea how to do it!! )

1. Make WebCamera diffrent ID then Bluetooth and check if it causes EMI
2. Remove Camera and  check it it casues EMI. (it's build in so i don't know how to do it :( )
3. Move Bluetooth to diffrent ID and check if after bluetooth will work!
4. Make Bluetooth go back to Dev #3  to check if mouse work again.

HELP i am so close now :P

---

### Post by varunendra on 2013-07-10
Wow ! I'm getting dizzy :P
You made me do quite some experimenting before posting..
> **macmus said:**
> Ok i used your script, but no good news :(
[/code]
I wasn't expecting that you'll quickly turn it into a script. Although everything as per dmesg is happening as expected, I think we should give some time to certain operations. I'd suggest to insert "**sleep 6**" in-between 'unbind-bind' commands both times, after "service bt stop", after unloading the last module, and after "service bt start". Although sleep time 2 to 4 seconds should be sufficient, we are desperate here and don't want to take chance *(given all the clues you dug up, this may seem futile, but, we ARE desperate !)*. :)

> **macmus said:**
> this part is interesting for me:

```

[B][  799.457] (II) config/udev: Adding input device Dell BT Travel Mouse (/dev/input/mouse2)
[  7799.457] (II) No input driver specified, ignoring this device.[/B]
[  7799.457] (II) This device may have been added with another device file.
[  7799.457] (II) config/udev: Adding input device Dell BT Travel Mouse (/dev/input/event16)
[  7799.457] (**) Dell BT Travel Mouse: Applying InputClass "evdev pointer catchall"

```

why ?
I noticed that earlier. To me it seems like a routine 'check, probe & move on' type device probing event, where finally the device gets correctly identified and associated with the correct driver 'evdev'.

> **macmus said:**
> ```

[29613.906151] Bluetooth: hci0 corrupted ACL packet
[29613.906173] Bluetooth: hci0 ACL packet for unknown connection handle 12

```
This is typically an indication/symptom of bt connection failure, but I don't think it tells anything more than that.

> **macmus said:**
> the first 3 is my web cammera:
....
the other 3 is bluetooth mouse
Nope! The other 3 is your internal bluetooth adapter, not the mouse (see usb-devices).

> **macmus said:**
> when its stop working it resets device number 3 and reinisalize the usb chipset BCM20702A0 on as device 5 **[COLOR="#FF0000"]which causes bluetooth not working.[/COLOR]**
That is why my dump got disconencted and because all events seems to be addressed old handler still!

```

[29607.386090] usb 2-1.6: reset full-speed USB device number 3 using ehci-pci
[29607.479544] btusb 2-1.6:1.0: no reset_resume for driver btusb?
[29607.479552] btusb 2-1.6:1.1: no reset_resume for driver btusb?
[29607.479563] usb 2-1.6: USB disconnect, device number 3
[29607.693517] usb 2-1.6: new full-speed USB device number 5 using ehci-pci
[29607.789069] usb 2-1.6: New USB device found, idVendor=0a5c, idProduct=21e1
[29607.789072] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[29607.789074] usb 2-1.6: Product: BCM20702A0
[29607.789076] usb 2-1.6: Manufacturer: Broadcom Corp
[29607.789077] usb 2-1.6: SerialNumber: B8763FDB052F
[29613.906151] Bluetooth: hci0 corrupted ACL packet

```

bluetooth chipset moved to Dev #5
That behaviour is same as removing a usb device from a port, then plugging it back. Its device no. will change, but it doesn't mean it won't work properly. Your bt adapter is just like a usb device, only connected internally. I'm quite positive that once you do the hub reset, the device id should get reset (to 3) too.

As per the dmesg part above, it seems like the bt adapter was reset properly and should work properly afterwards. The corrupt ACL packet may be an indication that either the adapter itself, or the device sending those packets (mouse??) is not yet reset properly. If you have another bt device, like a mobile phone, you may experiment with its connection to see whether it works after the new dev id is assigned to the adapter. If it does, it would mean that the adapter is being reset properly. Keep in mind that once a bluetooth connection is interrupted, it needs to be re-established and that may require that the external device is reset too (implying a power reset on devices like mouse where you have no other way to re-initiate a connection).

> **macmus said:**
> when I close/open lid is again become Dev 3 and mouse starts responding again (and we go to begning of this post :) )

I see couple ofthings here:

1. EMI is cased because WebCamera and Bluetooth chipset is defined as some Device #3
2. Bluetooth stops responding **[COLOR="#FF0000"]becasue[/COLOR]** new device is diffrent then old one after reasiging 

On a sleep-wake cycle, the usb devices are put to sleep and reset again, something like we are doing with our unbind-bind cycle. Obviously a sleep-wake cycle does a lot more than that and some part of it is helping the case. But I'm quite sure it is not the device id that is causing trouble. Furthermore -

1. Not only the device no, but the bus no. is also taken into consideration, and no two devices can have same device no in that perspective (at lease one of the no. or bus will be different)

2. Nope. The new dev no. (remember - it is the internal bt adapter, not the mouse) is a result of the device reset, not the cause of the problem (unless it fails to properly reset).

However, despite these misunderstandings, I'm interested in your solution part -

> **macmus said:**
> Solution: ( I have no idea how to do it!! )

1. Make WebCamera diffrent ID then Bluetooth and check if it causes EMI
2. Remove Camera and  check it it casues EMI. (it's build in so i don't know how to do it :( )
3. Move Bluetooth to diffrent ID and check if after bluetooth will work!
4. Make Bluetooth go back to Dev #3  to check if mouse work again.
**1.** Try (I'm picking IDs from your outputs, but you still may have to correct addresses like you had to with 'ehci_hcd')-
```
echo -n "1-1.3:1.0" | sudo tee /sys/bus/usb/drivers/uvcvideo/unbind
echo -n "1-1.3:1.0" | sudo tee /sys/bus/usb/drivers/uvcvideo/bind
```
Keep a gap of at least 4 seconds between both, then check usb-devices to see if the dev no. changed.

**2.** Don't use the 'bind' command in above. Simple as that ;)

**3.** Do the same as 1 above, with bt driver (btusb) and the adapter's ID -
```
echo -n "2-1.6:1.0" | sudo tee /sys/bus/usb/drivers/btusb/unbind
echo -n "2-1.6:1.0" | sudo tee /sys/bus/usb/drivers/btusb/bind
```
4 second gap as above, then check usb-devices.

**4.** Do the usual unbind-bind cycle that we have been doing (with the hub). Check usb-devices and I'm sure you'll get your wish. Not with the mouse functionality though, only with the dev no. ;)

Let me know if you have success with any of them.

---

### Post by macmus on 2013-07-10
> **varunendra said:**
> 

**1.** Try (I'm picking IDs from your outputs, but you still may have to correct addresses like you had to with 'ehci_hcd')-
```
echo -n "1-1.3:1.0" | sudo tee /sys/bus/usb/drivers/uvcvideo/unbind
echo -n "1-1.3:1.0" | sudo tee /sys/bus/usb/drivers/uvcvideo/bind
```
Keep a gap of at least 4 seconds between both, then check usb-devices to see if the dev no. changed.


when I do unbind something is unbinding but that isn't WebCamera. It simply does not disapears from device list.
When i do bind WebCamera does not change its device ID :(

---

### Post by varunendra on 2013-07-10
I picked up that ID from post #5 -
> S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/**1-1.3:1.0**/input/input14
Before you try the above command, check "cat /proc/but/input/devices" to see if the camera is listed and is on the same bus/port, then you may also check "ls /sys/bus/usb/drivers/uvcvideo/" to confirm that "1-1.3:1.0" exists there. (I wrote all of the above behaviours after testing on my lappy here).

---

### Post by macmus on 2013-07-10
this is what is see there

```

I: Bus=0003 Vendor=04f2 Product=b2ef Version=5172
N: Name="HP HD Webcam [Fixed]"
P: Phys=usb-0000:00:1a.0-1.3/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input17
U: Uniq=
H: Handlers=kbd event17 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


``` 

```

lech@HP-EliteBook:~$ ls /sys/bus/usb/drivers/uvcvideo
1-1.3:1.0  1-1.3:1.1  bind  module  new_id  remove_id  uevent  unbind

```

it seems what you wrote is correct?

---

### Post by varunendra on 2013-07-11
Yes, that's exactly as expected. Do you have cheese or another webcam application installed? What do they say when you unbind uvcvideo driver from "1-1.3:1.0"? Mine says - "No video device found" (or something similar).

I'm wondering how different the bus/device handling on two different machines can be when their logical arrangement seems same ! :(

PS:
My laptop is an Asus X54C - SX261D by the way. Not that it matters.

---

### Post by macmus on 2013-07-18
sorry do delay I was busy with other stuff :)

Could we come back to this issue. It seems it is still there.

Last point was to unbind video cam:

```

lech@HP-EliteBook:~$ echo -n "1-1.3:1.0" | sudo tee /sys/bus/pci/drivers/ehci_hcd/unbind
tee: /sys/bus/pci/drivers/ehci_hcd/unbind: No such file or directory

```

It does not work :(

---

### Post by varunendra on 2013-07-18
> **macmus said:**
> ```
lech@HP-EliteBook:~$ echo -n "1-1.3:1.0" | sudo tee /sys/bus/pci/drivers/**[COLOR="#FF0000"]ehci_hcd[/COLOR]**/unbind
```
Not ehci_hcd, it was uvcvideo. If you tried ehci_hcd, it was wrong, try the correct one - uvcvideo - as in my post.

However, it the mistake is just in your post and you already tried the correct form, then
> **macmus said:**
> It seems it is still there.

Means the webcam applications can still detect and use it?

If so, assuming the webcam is controlled by (ONLY) uvcvideo driver, since the only other device in "/sys/bus/usb/drivers/uvcvideo" directory is "**1-1.3:1.1**", please try instead :
```
echo -n "1-1.3:1.**[COLOR="#0000CD"]1[/COLOR]**" | sudo tee /sys/bus/usb/drivers/uvcvideo/unbind
echo -n "1-1.3:1.**[COLOR="#0000CD"]1[/COLOR]**" | sudo tee /sys/bus/usb/drivers/uvcvideo/bind
```
..and check the webcam again if it is disabled after the first command, and its ID changed after the 2nd.

---

### Post by luis.nando on 2013-08-18
Guys just I would like to add I have the very same issue with a multilaser bluetooth mouse, I am also following your discussion, but so far couldn't find an answer either. Oh, and I get the very same behaviour, when I close and open the lid, the mouse comes back. It is interesting how frequently that affects other people, googling a bit you can find this out, but no answer for the problem, though.

---

### Post by alessio_c2 on 2013-08-26
Hi,
I've the same problem, Toshiba Satellite Pro C850 series notebook and Dell Bluetooth Travel mouse with Ubuntu 13.04 x64.

However, the problem occurs only when the notebook is running on battery. The problem does not occur if the laptop is connected to the power supply.

BR,
Alessio

---

### Post by lucas-we2 on 2013-09-15
Hey, 
I don't know whether this could be a solution/workaround, but it helped me. Have a look at cuichi's answer here: [http://askubuntu.com/questions/286112/bluetooth-loses-connection-with-mouse-in-13-04/345871#345871](http://askubuntu.com/questions/286112/bluetooth-loses-connection-with-mouse-in-13-04/345871#345871)

---

### Post by obadz on 2014-02-11
Same issue with Lenovo Yoga Pro 2.  I've tried a bunch of things and so far nothing.. [SOLUTION BELOW]

UPDATE #1:

So far this seems to work for me:

echo -1 | sudo tee /sys/bus/usb/devices/2-4/power/autosuspend_delay_ms

(where 2-4 is the USB id of the bluetooth card)

UPDATE #2:

I had what felt like it should have been a disconnect and the mouse wouldn't work for a couple of seconds but then it recovered!

The log showed this:
```
Feb 12 10:21:44 riker kernel: [ 5533.421298] hid-generic 0005:0A5C:0001.0008: unknown main item tag 0x0
Feb 12 10:21:44 riker kernel: [ 5533.489341] input: Bluetooth 3.0 mouse as /devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4:1.0/bluetooth/hci0/hci0:256/input18
Feb 12 10:21:44 riker kernel: [ 5533.489748] hid-generic 0005:0A5C:0001.0008: input,hidraw1: BLUETOOTH HID v1.29 Mouse [Bluetooth 3.0 mouse] on 5c:51:4f:a9:0d:b1
```

Will update again if an actual disconnect happens.

UPDATE #3:

After a whole day without disconnects, I'm relatively convinced that it works!

I added the following to my rc.local:

```
# Prevents the Bluetooth USB card from getting reset which disconnects the mouse
BTUSB_DEV="8087:07dc"
BTUSB_BINDING="$(lsusb -d "$BTUSB_DEV" |
    cut -f 1 -d : |
    sed -e 's,Bus ,,' -e 's, Device ,/,' |
    xargs -I {} udevadm info -q path -n /dev/bus/usb/{} |
    xargs basename)"


echo "Disabling autosuspend for Bluetooth USB Soundcard: $BTUSB_BINDING..."
echo -1 > "/sys/bus/usb/devices/$BTUSB_BINDING/power/autosuspend_delay_ms"
```

Pls post if this works/doesn't for you.

---

### Post by obadz on 2014-02-14
3 [UPDATE: now 30!] days without a mouse disconnect! This definitely worked for me.

---

### Post by iphobbes on 2014-05-16
Thanks obadz ,
this remedy worked for me too , on my lenovob490 i have [h=1]Broadcom BCM43142 WIFI+BT combo adapter and i had to manually make fw file , post that i was facing bt mouse going in to sleep and your method worked for me . thanks again[/h]

---

### Post by redfox7691 on 2014-06-16
> **obadz said:**
> Pls post if this works/doesn't for you.

HP EliteBook 850G1 + Mouse Bluetooth "HP Touch to Pair Mouse", frequent disconnect. Tried to upgrade latest kernel version and latest firmware version, without resolve the problem. Your script seems to resolve my problem: bravo, thank you very much.

---

