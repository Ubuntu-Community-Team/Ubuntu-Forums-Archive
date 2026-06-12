---
title: "Gsm Network suddenly disconnected on 3G ZTE modem"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by oliveer on 2011-04-30
Hey all .My problem is exactly the same as the one which faced [nikhilbuwa]("http://ubuntuforums.org/member.php?u=1174483") in his post in the last month 

[CENTER][SIZE=4][COLOR=Magenta][http://ubuntuforums.org/showthread.php?t=1714540](http://ubuntuforums.org/showthread.php?t=1714540)
[/COLOR][/SIZE][/CENTER]

[COLOR=Orange]First[/COLOR] of all here is some useful info about my issue 
OS:Ubuntu 11.04 Final version 32 bit 
Modem used : ZTE 3G USB modem  
Network manager : Default one (BCM not installed)
Previously OS used without problems :Windows 7 Sp1 64 it on Toshiba L500 laptop 
ISP: (Internet service provider):Zain (Telecommunications company at Kuwait )

[COLOR=Orange]Secondly[/COLOR] some events which happened about the issue :
1-Connection lost (Modem disconnects after a period of time while it is connected to the Internet )
2-Nothing worked when I tried to unplug the modem and then replug it 
3-the effective solution was restarting the whole system so the modem can be shown again 

[COLOR=Orange]Thirdly[/COLOR] some results after executing the following command in [SIZE=4][COLOR=SeaGreen]first[/COLOR][/SIZE] Terminal :
1-
```
tr -s "\n" < /dev/ttyUSB2
```This is the [SIZE=4][COLOR=Green]second[/COLOR] [/SIZE]Terminal :
2-
```
echo -e "AT+COPS=3,2\r" > /dev/ttyUSB2
```> Result: OK3-
```
echo -e "AT+COPS?\r" > /dev/ttyUSB2
```> Result:+COPS: 0,2,"41902",2

OK4-
```
echo -e "AT+CGDCONT?\r" > /dev/ttyUSB2
```> Result:+CGDCONT: 1,"IP","hspps","0.0.0.0",0,0
+CGDCONT: 2,"IP","HSPPS","0.0.0.0",0,0

OK5-
```
ls -al /dev/serial/by-id/*
```> Result: 
lrwxrwxrwx 1 root root 13 2011-04-30 08:09 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673A3ZTED010000-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-04-30 08:09 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673A3ZTED010000-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2011-04-30 08:09 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673A3ZTED010000-if03-port0 -> ../../ttyUSB26-
```
usb-devicesResult:
```> T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0031 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=P673A3ZTED010000
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15ca ProdID=00c3 Rev=05.12
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub[SIZE=4][COLOR=Red]Very important note : I am so so so new to Ubuntu and Linux systems so please be easy with me[/COLOR][/SIZE]

---

### Post by oliveer on 2011-04-30
Some info taken from the system log :

> Apr 30 07:56:18 ollivierre-desktop modem-manager[19287]: <warn>  Could not acquire the org.freedesktop.ModemManager service.#012  Message: 'Connection ":1.235" is not allowed to own the service "org.freedesktop.ModemManager" due to security policies in the configuration file'
Apr 30 08:09:39 ollivierre-desktop modem-manager[734]: <info>  (ttyUSB0) closing serial port...
Apr 30 08:09:39 ollivierre-desktop modem-manager[734]: <info>  (ttyUSB0) serial port closed
Apr 30 08:09:39 ollivierre-desktop modem-manager[734]: <info>  (ttyUSB0) opening serial port...
Apr 30 08:09:42 ollivierre-desktop modem-manager[734]: <info>  (ttyUSB0) closing serial port...
Apr 30 08:09:42 ollivierre-desktop modem-manager[734]: <info>  (ttyUSB0) serial port closed
Apr 30 08:09:42 ollivierre-desktop modem-manager[734]: <info>  (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1 claimed port ttyUSB0
Apr 30 08:09:42 ollivierre-desktop NetworkManager[728]: <warn> (ttyUSB2): failed to look up interface index
Apr 30 08:09:42 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): new GSM device (driver: 'option1' ifindex: -1)
Apr 30 08:09:42 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 30 08:09:42 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): now managed
Apr 30 08:09:42 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): device state change: 1 -> 2 (reason 2)
Apr 30 08:09:42 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): deactivating device (reason: 2).
Apr 30 08:09:42 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): device state change: 2 -> 3 (reason 0)
Apr 30 08:12:46 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) starting connection 'Zain connection'
Apr 30 08:12:46 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): device state change: 3 -> 4 (reason 0)
Apr 30 08:12:46 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Apr 30 08:12:46 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Apr 30 08:12:46 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): device state change: 4 -> 6 (reason 0)
Apr 30 08:12:46 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): device state change: 6 -> 4 (reason 0)
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Apr 30 08:13:09 ollivierre-desktop modem-manager[734]: <info>  (ttyUSB2) opening serial port...
Apr 30 08:13:09 ollivierre-desktop modem-manager[734]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Apr 30 08:13:09 ollivierre-desktop modem-manager[734]: <info>  (ttyUSB1) opening serial port...
Apr 30 08:13:09 ollivierre-desktop modem-manager[734]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> WWAN now enabled by management service
Apr 30 08:13:09 ollivierre-desktop modem-manager[734]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Apr 30 08:13:09 ollivierre-desktop modem-manager[734]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Apr 30 08:13:09 ollivierre-desktop modem-manager[734]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) scheduled...
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) starting...
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): device state change: 4 -> 5 (reason 0)
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) successful.
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) complete.
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) started...
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): device state change: 5 -> 7 (reason 0)
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> starting PPP connection
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> pppd started with pid 1550
Apr 30 08:13:09 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) complete.
Apr 30 08:13:09 ollivierre-desktop pppd[1550]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Apr 30 08:13:09 ollivierre-desktop pppd[1550]: pppd 2.4.5 started by root, uid 0
Apr 30 08:13:10 ollivierre-desktop NetworkManager[728]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Apr 30 08:13:10 ollivierre-desktop NetworkManager[728]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Apr 30 08:13:10 ollivierre-desktop pppd[1550]: Using interface ppp0
Apr 30 08:13:10 ollivierre-desktop pppd[1550]: Connect: ppp0 <--> /dev/ttyUSB2
Apr 30 08:13:10 ollivierre-desktop pppd[1550]: CHAP authentication succeeded
Apr 30 08:13:10 ollivierre-desktop pppd[1550]: CHAP authentication succeeded
Apr 30 08:13:10 ollivierre-desktop kernel: [  272.597576] PPP BSD Compression module registered
Apr 30 08:13:10 ollivierre-desktop kernel: [  272.645210] PPP Deflate Compression module registered
Apr 30 08:13:12 ollivierre-desktop pppd[1550]: Could not determine remote IP address: defaulting to 
Apr 30 08:13:12 ollivierre-desktop pppd[1550]: local  IP address 
Apr 30 08:13:12 ollivierre-desktop pppd[1550]: remote IP address 
Apr 30 08:13:12 ollivierre-desktop pppd[1550]: primary   DNS address 
Apr 30 08:13:12 ollivierre-desktop pppd[1550]: secondary DNS address 
Apr 30 08:13:12 ollivierre-desktop NetworkManager[728]: <info> PPP manager(IP Config Get) reply received.
Apr 30 08:13:12 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr 30 08:13:12 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 4 of 5 (IP4 Configure Get) started...
Apr 30 08:13:12 ollivierre-desktop NetworkManager[728]: <info> Scheduling stage 5
Apr 30 08:13:12 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr 30 08:13:12 ollivierre-desktop NetworkManager[728]: <info> Done scheduling stage 5
Apr 30 08:13:12 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 4 of 5 (IP4 Configure Get) complete.
Apr 30 08:13:12 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) started...
Apr 30 08:13:13 ollivierre-desktop NetworkManager[728]: <info> (ttyUSB2): device state change: 7 -> 8 (reason 0)
Apr 30 08:13:13 ollivierre-desktop NetworkManager[728]: <info> Policy set 'Zain connection' (ppp0) as default for IPv4 routing and DNS.
Apr 30 08:13:13 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) successful, device activated.
Apr 30 08:13:13 ollivierre-desktop NetworkManager[728]: <info> Activation (ttyUSB2) Stage 5 of 5 (IP Configure Commit) complete.
Apr 30 08:13:30 ollivierre-desktop ntpdate[1624]: step time server 91.189.94.4 offset 1.323226 sec


---

### Post by oliveer on 2011-04-30
Any help????!!!!

---

### Post by alexfish on 2011-04-30
Hi oliveer , welcome to the Forum

have looked through the info.

as regards the device and the Linux system , all seems to be OK

here are some areas to look at as regards Network Manager and Modem Manager

1. In Network Manager PPP Settings > Configure methods , disabling some of the  
 Authentication Methods , also try selecting Echo Send PPP echo packets 

 you will monitor the effects to see if there is any improvement

2. When a disconnection occurs and the Network Manager can't connect ,do not unplug the device. open up the terminal and enter the following code
```
ls -al /dev/serial/by-id/*
```post the results 
if the device is still listed try this command
```
sudo killall modem-manager
```
wait a few moments see what happens



alexfish

---

### Post by oliveer on 2011-04-30
Thanks alot I will monitor the issue since my modem did not disconnect for the last 14 hours :D

Sure, i will try the commands you listed if the problem occur in the next few days

---

