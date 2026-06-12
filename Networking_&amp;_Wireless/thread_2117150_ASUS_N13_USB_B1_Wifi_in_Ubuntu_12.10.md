---
title: "ASUS N13 USB B1 Wifi in Ubuntu 12.10"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by Bad70sbchevy on 2013-02-17
Hi everybody,

I am having a lot of trouble trying to get the Realtek drivers to work on Ubuntu 12.10.  I'm running the kernel 3.0.63 on an Odroid-U2. Just don't know where to start. Thanks in advance!

---

### Post by Bad70sbchevy on 2013-02-17
bump

---

### Post by varunendra on 2013-02-21
*Thread moved to **Networking & Wireless**.*

------------------------

Never dealt with a *droid, so not entirely sure what I'm talking about, but is it the normal Ubuntu 12.10?

What have you tried so far? Please also post the outputs of -
```
lsusb
usb-devices
```
while the USB adapter is plugged in.

---

### Post by Bad70sbchevy on 2013-04-12
No, its the Linaro version of Ubuntu 12.10 since it is an ARM processor. Here is what I got:

ldconfig deferred processing now taking place
linaro@linaro-ubuntu-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0424:9730 Standard Microsystems Corp. 
Bus 001 Device 003: ID 0424:3503 Standard Microsystems Corp. 
Bus 001 Device 006: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 001 Device 005: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
linaro@linaro-ubuntu-desktop:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.63-odroidu2 ehci_hcd
S:  Product=S5P EHCI Host Controller
S:  SerialNumber=s5p-ehci
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=9730 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=ff Driver=smsc95xx

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=3503 Rev=a1.a0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=03 Port=00 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0b05 ProdID=17ab Rev=02.00
S:  Manufacturer=Realtek
S:  Product=802.11n WLAN Adapter
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

T:  Bus=01 Lev=02 Prnt=03 Port=02 Cnt=02 Dev#=  5 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=413c ProdID=2105 Rev=03.51
S:  Manufacturer=Dell
S:  Product=Dell USB Keyboard
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=70mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 3
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.63-odroidu2 ohci_hcd
S:  Product=s5p OHCI
S:  SerialNumber=s5p-ohci
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by varunendra on 2013-04-12
> **Bad70sbchevy said:**
> Bus 001 Device 006: ID **0b05:17ab** ASUSTek Computer, Inc.
..
..
P:  Vendor=**0b05** ProdID=**17ab** Rev=02.00
S:  Manufacturer=**Realtek**
S:  Product=802.11n WLAN Adapter
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=ff Prot=ff** Driver=(none)**
Please try -
```
sudo modprobe -v rtl8192cu
```
.. and see if it brings up the wireless.

If it returns any errors, post back the error, plus the following-
```
uname -mr
lsb_release -d
dmesg | grep 8192
locate 8192
```

---

