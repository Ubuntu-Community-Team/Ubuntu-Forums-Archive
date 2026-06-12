---
title: "problem connecting with usb 3g modem"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by Smarty_T2 on 2011-02-25
Hello Everyone
I am using Ubuntu 10.10. I have Micromax MMX 310G USB Modem with a bsnl 3G SIM Card. When I plug-in my device in my PC and open network connections, I tried creating a new mobile broadband connection and my device is not shown there.
 
Now, when i opened "computer", i found two things there A "Floppy Drive" and a "Modem". "Modem" is of unreadable format(though it works on windows and is the modem installation disc) while floppy drive must be the memory card reader thats built in the device.
I right clicked on the modem->open and nothing happens. But after doing that, when i go to network connections again and create a connection, i find my device there. I selected that device and created a cellone connection with "north india" as my plan But it just keeps on trying to connect for 5-10 min and then says disconnected. It is just not able to connect.
 
Is anybody having any idea about how to connnect through that modem. If you are using it, what did you do to make it work on your system.
 
Thank You
-Jayant

---

### Post by kareempharmacist on 2011-02-25
try huewai e153 modem or any huewai modem for vodafone .....they are easier
huewai e153 will connect automatically without any problems 
get one of them and then post a reply and we will guide you

---

### Post by alexfish on 2011-02-25
Hi
check to see if recognized by Network Manager 

check with nm-tool from the terminal

```
nm-tool
```if see a message like

> - Device: ttyUSB3 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option
  State:             disconnected
  Default:           no

Capabilities: then it has been recognized , the tty* may be different,leaving only the correct data been entered.

if nothing shows
first try and eject the device , don't do this from opening  "computer" if the only option is safely remove;

open up the Disk Utility from System/Administration/Disk Utilty

click on the device look at the options in right hand pane select eject

note any change with the nm-tool

can also monitor any changes of the device id's with the lsusb command
use this before the eject command , then after the eject command
```
lsusb
```see what happens , also post the results of the two lsusb commands

alexfish

---

### Post by Smarty_T2 on 2011-02-25
Thank you both for replying...
@kareempharmacist: I have already purchased this modem and cannot buy a new one now.
@alexfish:
I connected my usb moedm and after it's light went green, i tried the nm-tool command and heres the result.
>  
jayant@jayant-System-Product-Name:~$ nm-tool
NetworkManager Tool
State: disconnected
- Device: eth1 -----------------------------------------------------------------
Type: Wired
Driver: sc92031
State: unavailable
Default: no
HW Address: 00:E0:20:80:2B:E7
Capabilities:
Carrier Detect: yes
Speed: 10 Mb/s
Wired Properties
Carrier: off
 
jayant@jayant-System-Product-Name:~$ 

Got no tty stuff...
Then i opened the disk utility. There were 2 devices there, a floppy drive and a modem disk. The only options for the modem were to safely remove and other i dont remember and that other one was also the only option for floppy drive. I tried safley remove for modem and got an error.
Then again i ran the nm-tool command at the terminal and got this...
> 
NetworkManager Tool
State: disconnected
- Device: eth1 -----------------------------------------------------------------
Type: Wired
Driver: sc92031
State: unavailable
Default: no
HW Address: 00:E0:20:80:2B:E7
Capabilities:
Carrier Detect: yes
Speed: 10 Mb/s
Wired Properties
Carrier: off
 
- Device: ttyUSB3 --------------------------------------------------------------
Type: Mobile Broadband (GSM)
Driver: option1
State: disconnected
Default: no
Capabilities:
 

Got this tty this time and there was option to connect in the network connections. I clicked on it and waited for 12 minutes and it didnt connect so i just plugged out my device.
 
And i didn't understood the use of lsusb command... :(
 
Thank you

---

### Post by alexfish on 2011-02-25
hi

lsusb ' gives the ids, and type of device,

use from the terminal

```
lsusb
```

from this info it will list ID's of the device + type or product

can also post the results of
```
ls -al /dev/serial/by-id
```

this is is now important as this will indicate if the correct ttyport is been identified by the
network manager

also need to Know which version of Ubuntu been used
ie ubuntu 9.04 , 9.10, 10.04  etc

alexfish

---

### Post by Smarty_T2 on 2011-02-25
hi,
THank you for all your help..
 
Heres the output of lsusb
 
> 
[EMAIL="jayant@jayant-System-Product-Name:~$"]jayant@jayant-System-Product-Name:~$[/EMAIL] lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1c9e:9605  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[EMAIL="jayant@jayant-System-Product-Name:~$"]jayant@jayant-System-Product-Name:~$[/EMAIL] 

 
and heres o/p of ls -al /dev/serial/by-id
 
> 
[EMAIL="jayant@jayant-System-Product-Name:~$"]jayant@jayant-System-Product-Name:~$[/EMAIL] ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 120 2011-02-26 02:07 .
drwxr-xr-x 4 root root  80 2011-02-26 02:07 ..
lrwxrwxrwx 1 root root  13 2011-02-26 02:07 usb-USB_Modem_Modem_Configuration_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root  13 2011-02-26 02:07 usb-USB_Modem_Modem_Configuration_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root  13 2011-02-26 02:07 usb-USB_Modem_Modem_Configuration_1234567890ABCDEF-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root  13 2011-02-26 02:07 usb-USB_Modem_Modem_Configuration_1234567890ABCDEF-if03-port0 -> ../../ttyUSB3
[EMAIL="jayant@jayant-System-Product-Name:~$"]jayant@jayant-System-Product-Name:~$[/EMAIL] 

 
Thanks!

---

### Post by tanmoykrthakur on 2011-03-01
Go [http://www.sakis3g.org](http://www.sakis3g.org) & download sakis3g, copy it to home folder, allow executing file as program, run it & use it.
[B]
[/B]

---

### Post by Smarty_T2 on 2011-03-13
@tanmoykrthakur: thanks for the reply. I have downloaded it. Will give it a try soon and post here asap !

---

### Post by Smarty_T2 on 2011-03-15
The sakis 3g script works. Thanks a lot !!

---

### Post by xlearner on 2011-11-27
Hello All,

I am visiting this thread after sometime. I am having the same problem. I am using Ubuntu 10.10. I have Micromax MMX 310G USB Modem with a bsnl 3G SIM Card. I created a new mobile broadband connection. When I try to plug-in the device, it is not showing a new network connection. 
I downloaded Sakis 3G utility. Unfortunately, it did not work as well. It is failing after when "switching to the modem". I was getting the error message, "Failed to Connect". 
Then I looked into 'more options'. There when I click on 'Only switch modem' option, it returns successfully with the message "Modem switched to 1c9e:f000". But when I click on 'Only setup modem (Switch + Load Module + Setup tty)', it fails with the message "Failed to setup modem". 

So can anyone help me or give me some advice?

Thanks
Sathya

---

### Post by alexfish on 2011-12-04
> **xlearner said:**
> Hello All,

I am visiting this thread after sometime. I am having the same problem. I am using Ubuntu 10.10. I have Micromax MMX 310G USB Modem with a bsnl 3G SIM Card. I created a new mobile broadband connection. When I try to plug-in the device, it is not showing a new network connection. 
I downloaded Sakis 3G utility. Unfortunately, it did not work as well. It is failing after when "switching to the modem". I was getting the error message, "Failed to Connect". 
Then I looked into 'more options'. There when I click on 'Only switch modem' option, it returns successfully with the message "Modem switched to 1c9e:f000". But when I click on 'Only setup modem (Switch + Load Module + Setup tty)', it fails with the message "Failed to setup modem". 

So can anyone help me or give me some advice?

Thanks
Sathya
if using sakis3g will have to add the file for device
open up text editor
```
sudo gedit /etc/usb_modeswitch.d/1c9e:f000
```Add the following code
```
######################################################## 
# MobiData MBD-200HU and others

DefaultVendor= 0x1c9e
DefaultProduct=0xf000

TargetVendor=  0x1c9e
TargetProductList="9000,9603,9605,9607"

CheckSuccess=20

MessageContent="55534243123456788000000080000606f50402527000000000000000000000"
```save and exit , now try sakis3g

Added appols for file; the above rectified; noted you say switched , nothing in usb modeswitch data to indicate it has switch

can also post details of this command from the terminal
usb-devices

alexfish

---

### Post by xlearner on 2011-12-10
Dear Alexfish,

Thanks a lot for your reply. I am responding back somewhat late though. 

So as you have suggested, I have copied & pasted the code the code that you gave. (Actually this file was already there with almost the same code).

But when I again tried sakis3G, it was still failing. So I must try something different. 

As you have suggested, I am giving the output of usb-devices: 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-31-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a5c ProdID=4500 Rev=01.00
S:  Manufacturer=Broadcom
S:  Product=BCM2046B1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=94mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=03 Prnt=03 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=413c ProdID=8161 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid

T:  Bus=01 Lev=03 Prnt=03 Port=01 Cnt=02 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=413c ProdID=8162 Rev=01.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)

T:  Bus=01 Lev=03 Prnt=03 Port=02 Cnt=03 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=413c ProdID=8160 Rev=01.73
S:  Manufacturer=Dell Computer Corp
S:  Product=Dell Wireless 365 Bluetooth Module
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=00 Driver=(none)

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-31-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=00dd Rev=01.73
S:  Manufacturer=Microsoft
S:  Product=Comfort Curve Keyboard 2000
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=093a ProdID=2510 Rev=01.00
S:  Manufacturer=PIXART
S:  Product=USB OPTICAL MOUSE
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=04 Cnt=03 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c9e ProdID=f000 Rev=00.00
S:  Manufacturer=USB Modem
S:  Product=USB Modem
S:  SerialNumber=000000000000
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)

T:  Bus=02 Lev=02 Prnt=02 Port=07 Cnt=04 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=6450 Rev=9c.31
S:  Manufacturer=Sonix Technology Co., Ltd.
S:  Product=Laptop_Integrated_Webcam_2M
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=168mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

---

### Post by alexfish on 2011-12-11
Hi

according to the info the device is not switching, may be your device has different target ID's ,

can go to Re: How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10] Post  			#[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61") 

there is script, it will test the SR bit of the device , if the device has the correct info the script will notify if device is in ejectable state , but not fool proof , some devices can configure just by applying the eject command,

post any results , if using the script

, if this does not work can try usb_modeswitch using message only.

---

### Post by xlearner on 2011-12-13
Dear Alexfish,

Thanks a lot for your reply. I am trying to understand the other posts of yours. Once I understand them well, I will try all the suggestions given there and update you about it. 

Thanks

---

### Post by alexfish on 2011-12-13
can also look to usb_modeswitch forum for help , the site is listed in the How To

as mentioned (the script) should prove if the device is in a switched or un-switched mode,(think says he)
 would be interested in the results .

thanks in advance ,

if interested in reason . In process of finalizing a front end application for such devices, hopefully avoiding terminal commands  , ( it does most of what you see in the How To)

regards 

alexfish

---

