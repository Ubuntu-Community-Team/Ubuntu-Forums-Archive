---
title: "wvdial:  Cannot Open ..ttyUSB0..no such File or Direcotory"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by alecodd on 2011-01-23
Hi! 
im running a wireless modem under ubuntu (10.10) now, when i first plug in the modem, and run the command wvdial everything is OK.
BUT if i plug out the modem and try to plug in again and run the 'wvdial' command i can the error:
```
"wvdial: cannot open ttyUSB0: no such file or directory.
```

any help please!

---

### Post by alexfish on 2011-01-23
hi

can post details of these command from the terminal

```
usb-devices
```

```
ls al /dev/serial/by-id
```

if you get device and a "[COLOR=Blue]....tty[/COLOR]*" listing

```
pidof modem-manager
```

if the modem-manager is running then try

```
sudo killall modem-manager
```

then try the wvdial

alexfish

---

### Post by alecodd on 2011-01-26
here is the output for `ls -al /dev/serial/by-id' when the modem is recognized:
```

total 0
12127 0 drwxr-xr-x 2 root root 100 2011-01-26 15:41 ./
12219 0 lrwxrwxrwx 1 root root  13 2011-01-26 15:41 usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
12119 0 drwxr-xr-x 4 root root  80 2011-01-26 15:41 ../
12128 0 lrwxrwxrwx 1 root root  13 2011-01-26 15:41 usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
12129 0 lrwxrwxrwx 1 root root  13 2011-01-26 15:41 usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if03-port0 -> ../../ttyUSB2

```after i plug-out and plug-in again the modem i get:
```

no such file or directory..

```here is the output for `usb-devices', when everything is still OK:
```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b1be Rev=20.58
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=USB2.0 0.3M UVC WebCam
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0031 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Technologies MSM
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

```and here is the output after i plug-out and plug-in again the modem.

```

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b1be Rev=20.58
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=USB2.0 0.3M UVC WebCam
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=2000 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Technologies MSM
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=05 Prot=50 Driver=(none)
    
```

---

### Post by alecodd on 2011-01-26
and this is the output for `tail -f /var/log/messages' when i plug-out and again plug-in the modem:
```

Jan 26 16:52:48 computername kernel: [ 2000.544778] usb 2-1.3: USB disconnect, address 5
Jan 26 16:52:48 computername kernel: [ 2000.544987] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jan 26 16:52:48 computername kernel: [ 2000.545010] option 2-1.3:1.0: device disconnected
Jan 26 16:52:48 computername kernel: [ 2000.545115] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jan 26 16:52:48 computername kernel: [ 2000.545136] option 2-1.3:1.1: device disconnected
Jan 26 16:52:48 computername pppd[1870]: Modem hangup
Jan 26 16:52:48 computername pppd[1870]: Connect time 31.7 minutes.
Jan 26 16:52:48 computername pppd[1870]: Sent 459840 bytes, received 2213606 bytes.
Jan 26 16:52:48 computername kernel: [ 2000.555479] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jan 26 16:52:48 computername kernel: [ 2000.555506] option 2-1.3:1.3: device disconnected
Jan 26 16:52:48 computername pppd[1870]: Connection terminated.
Jan 26 16:52:48 computername pppd[1870]: Exit.
Jan 26 16:52:57 computername kernel: [ 2009.946779] usb 2-1.3: new high speed USB device using ehci_hcd and address 6
Jan 26 16:52:57 computername kernel: [ 2010.052645] scsi7 : usb-storage 2-1.3:1.0
Jan 26 16:52:58 computername usb_modeswitch: switching 19d2:2000 (ZTE, Incorporated: ZTE CDMA Technologies MSM)

```

---

### Post by alexfish on 2011-01-26
hi

think it is a system configuration problem as logfile shows modeswitch use
can check if usb_modeswitch is in use 

```
pidof usb_modeswitch
```if pid show  : could reason to guess the problem:

can make a little script to try :called switch<my:id> or any name you prefer 

```
sudo gedit /usr/bin/switch19d2:2000
```and enter
```
#!/bin/sh
usb_modeswitch /etc/usb_modeswitch -c /etc/usb_modeswitch.d/19d2:2000
```save and exit

next time not switching open up the terminal

and enter

```
switch19d2:2000
```see what happens

alexfish

---

### Post by alecodd on 2011-01-26
pidof usb_modeswitch shows NOTHING.
what is wrong?

thanks

---

### Post by alexfish on 2011-01-26
looks as if the device is been recognised or switched by another process , then usb_modeswitch is kicking in / out of sequence and possibly  reseting the device


can ask if any vm ware on system

possible fixes 

the script as mentioned . see if it works 

or try disable modeswitch

```
sudo gedit /etc/usb_modeswitch.conf
```

edit the line 

DisableSwitching=0

to

DisableSwitching=1

disabling the switching may prevent other devices from switching

Another way of influencing the kernel behavior 
is the parameter "delay_use" of "usb-storage" which sets the time in seconds after plugging 
when the storage device will actually be used (and probably automounted). The default value is 5; 
this might affect the switching result under certain conditions.
To change the default add in /etc/modprobe.conf:

```
options usb-storage delay_use=1 
```

> (or 10, or other)

see what happens

alexfish

---

