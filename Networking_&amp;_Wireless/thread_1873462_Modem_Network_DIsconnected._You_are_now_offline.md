---
title: "Modem Network DIsconnected. You are now offline"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by apocalyptod on 2011-11-01
I'm a new user of linux environment. I'm using ubuntu 11.10  and a MTS Mblaze USB modem. I have installed it correctly and it was  working good at first but when I restarted my system then I was unable  to connect my Modem again. Whenever I click on that MTS connection,  a message prompts up "Modem Network Disconnected. You are now offline."  Please help to get me out of this problem.


  Thanks & Regards.

---

### Post by alexfish on 2011-11-01
can try this command from the terminal

```
sudo killall modem-manager
```wait for a few moments , see what happens

---

### Post by tariqsheikh on 2011-11-02
Same problem with BSNL EVDO Card. No solution yet.

---

### Post by apocalyptod on 2011-11-06
@alexfish > still not working. :S

---

### Post by arundracula on 2011-11-20
Me too.. BSNL EVDO is not working..
"Modem Network Disconnected. You are now offline."

It was working for 11.04 and 10.10. What they have changed..?

---

### Post by alexfish on 2011-11-20
Hi all

can have a look at
[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490")

Take Note of:
**11.04 users: First read post #59 **
and
**TESTING MODEM-MANAGER: need to get mm-test.py :: To do the test disable all networking on the Network Manager**

but follow the link [FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]To get this to work as it should can Look here [/COLOR][/COLOR][/SIZE][/FONT]: [http://ubuntuforums.org/showpost.php...83&postcount=9]("http://ubuntuforums.org/showpost.php?p=11469183&postcount=9")

at post **#61** there is a script for checking modems would be interested in the output from the **argv "tty"**

alexfish

---

### Post by arundracula on 2011-12-03
usb-devices outputs this

```

 usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:12.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:16.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:12.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c31d Rev=66.00
S:  Manufacturer=Logitech
S:  Product=USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=90mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c05a Rev=63.00
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=05 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=fffe Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Tech
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:14.5
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:16.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:02:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=09 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.00
S:  Manufacturer=Linux 3.0.0-12-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:02:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


```

lsusb -t -d 19d2:fffe outputs this

```

/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/4p, 12M
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/2p, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/5p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 3: Dev 4, If 0, Class=vend., Driver=option, 12M
    |__ Port 3: Dev 4, If 1, Class=vend., Driver=option, 12M
    |__ Port 3: Dev 4, If 2, Class=vend., Driver=option, 12M
    |__ Port 3: Dev 4, If 3, Class=vend., Driver=option, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/5p, 12M
    |__ Port 5: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 5: Dev 2, If 1, Class=HID, Driver=usbhid, 1.5M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/4p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/5p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/5p, 480M


```

And
ls -al /dev/serial/by-id/*

```
lrwxrwxrwx 1 root root 13 2011-12-03 12:32 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-12-03 12:32 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2011-12-03 12:32 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2011-12-03 12:32 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Tech-if03-port0 -> ../../ttyUSB3
```


I can connect to internet using wvdial, But without networkmanager connection, I can't experience Ubuntu completely. I think the device recognized and the drivers are loaded. I tried downgrading to
network-manager_0.9.0-0ubuntu1_i386.deb, but not working.

---

### Post by arundracula on 2012-01-02
My lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 046d:c31d Logitech, Inc. 
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 005 Device 004: ID 19d2:fffe ONDA Communication S.p.A. 

I tried this
sudo usb_modeswitch -v 0x19d2 -p fffe -V 0x19d2 -P fffe -R

Not working.
Please help. I can connect via wvdial but Ubuntu won't allow to change empathy statuses, not integrated to internet(I can browse but..).. No internet connection shown in update manager and software center.. nor I can install an application.

---

