---
title: "config. Huawie E1550"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by m3asmi on 2009-12-18
[SIZE=4]Hi..
I have a modem huawai E1550 but I can not connect with him
He launched this as a normal usb![/SIZE]

[SIZE=4]**$>*lsusb***[/SIZE]
```


Bus 001 Device 007: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 163f:1611  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```[SIZE=4]and I added to* /etc/usb_modeswitch.conf*[/SIZE]
 ```
# Huawei E1550
#
# Contributor: Anders Blomdell, Ahmed Soliman

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1446

;TargetVendor=   0x12d1
;TargetProduct=  0x1001

# only for reference and 0.x versions
# MessageEndpoint=0x01

;MessageContent="55534243123456780000000000000011060000000000000000000000000000"
```[SIZE=4]but it not work Oncore !!...[/SIZE] :(

---

### Post by m3asmi on 2009-12-20
hi
eny openion please

---

### Post by pdc on 2009-12-20
If you think this modem need usb_modeswitch,  you need to activate the section relevant to you: (I believe)

so I think it needs to look like this

> # Huawei E1550
#
# Contributor: Anders Blomdell, Ahmed Soliman

DefaultVendor=  0x12d1
DefaultProduct= 0x1446

TargetVendor=   0x12d1
TargetProduct=  0x1001

# only for reference and 0.x versions
MessageEndpoint=0x01

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

let us know if that helps you

---

### Post by alexfish on 2009-12-27
> **m3asmi said:**
> [SIZE=4]Hi..
I have a modem huawai E1550 but I can not connect with him
He launched this as a normal usb![/SIZE]

[SIZE=4]**$>*lsusb***[/SIZE]
```


Bus 001 Device 007: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 163f:1611  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```[SIZE=4]and I added to* /etc/usb_modeswitch.conf*[/SIZE]
 ```
# Huawei E1550
#
# Contributor: Anders Blomdell, Ahmed Soliman

;DefaultVendor=  0x12d1
;DefaultProduct= 0x1446

;TargetVendor=   0x12d1
;TargetProduct=  0x1001

# only for reference and 0.x versions
# MessageEndpoint=0x01

;MessageContent="55534243123456780000000000000011060000000000000000000000000000"
```[SIZE=4]but it not work Oncore !!...[/SIZE] :(


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>> >>>>>>>>>>>>>>

HOW TO :ACTIVATE THE USB-Modeswitch

open up the the terminal type in

sudo gedit /etc/usb_modeswitch.conf

un comment the lines to look like below


########################################################
# Huawei E1550
# Huawei E1750
#
# Contributor: Anders Blomdell, Ahmed Soliman

DefaultVendor=  0x12d1
DefaultProduct= 0x1446

TargetVendor=   0x12d1
TargetProduct=  0x1001

# only for reference and 0.x versions
# MessageEndpoint=0x01

MessageContent="55534243123456780000000000000011060000000000000000000000000000"





save the file


To activate the usb mode switch   open up the terminal Type or Copy this Code

Code

sudo usb_modeswitch

Exit and reboot

if not working try removing The   #  From    #MessageEndpoint=0x01  it will depend on your version

Also have a look here  Esp Page 2 Worth Reading All

[SIZE=3][COLOR=Navy]RE:Ubuntu linux on the move { Guide look at page 2}[/COLOR][/SIZE]

                         [Mobile Broadband  can't connect]("http://ubuntuforums.org/showthread.php?t=1331317")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331317") [2]("http://ubuntuforums.org/showthread.php?t=1331317&page=2"))

---

### Post by alexfish on 2009-12-28
Up date listing of usb_mode switch

[http://www.draisberghof.de/usb_modes...odeswitch.conf]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf")


The Site  [ Worth Reading ]  

[CENTER][http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
[/CENTER]

---

### Post by m3asmi on 2010-01-02
thinks Mr [COLOR=Blue]***alexfish***[/COLOR]

---

