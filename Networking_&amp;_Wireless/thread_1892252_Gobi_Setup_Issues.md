---
title: "Gobi Setup Issues"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by LordVaine on 2011-12-07
[http://ubuntuforums.org/showthread.php?p=11473572#post11473572](http://ubuntuforums.org/showthread.php?p=11473572#post11473572)

The link I posted is where We left off, the person was unable to fix my issue.

Basically I got the firmware loaded, however, when you goto to setup the 3g connection, Verizon is not on the list, so I tried to add my own, but it would not let me enter the plan number with special characters, please help.

---

### Post by alexfish on 2011-12-07
Hi from the modalias of the device
```
Module Alias: "usb:v05C6p9244[COLOR=Red]d000[/COLOR][COLOR=Black][COLOR=Red]2[/COLOR]dc00[/COLOR]dsc00dp00icFFiscFFipFF " 
```looks as if 3g type modem , but could be proved wrong , by this part of the modalias [COLOR=Red]d000[/COLOR][COLOR=Black][COLOR=Red]2..[/COLOR][/COLOR][COLOR=Red][/COLOR] if apn required then will have to contact your service provider , but also need to ask if there is a simcard in use , if that been case
then details will be in the sim card , possible that different dial command is required, normally can try *99# as the default with the apn loaded into
```
AT+CGDCONT=1,"IP","inetgsm.vzw3g.com
```" , or if apn is on the sim in another location, then can try dialing *99***1# for first location, can change the 1 to a 2 for second location , and so on' . this would generaly work if the device had been working on a windows machine,

alexfish

---

### Post by LordVaine on 2011-12-07
Lol. I dont understand where to put this code, I am new user. I did get the APN, but like I said, It wont let me add special characters in it. I need to know what to do with this module thing you talked about..I know howto access the terminal but I need a step by step way of doing it, Sorry. :)

Edit: Ok on the network icon when ya click on it, brings down a dropdown menu, says Mobile Boradband (greyed out) And then underneath it says (not registered)

As for special characters I mean the plus signs and equal signs and the commas are apparently not allowed to be ptut in the apn area, there has to be a workaround

> looks as if 3g type modem , but could be proved wrong , by this part of the modalias d0002.. if apn required then will have to contact your service provider , but also need to ask if there is a simcard in use , if that been case
then details will be in the sim card , possible that different dial command is required, normally can try *99# as the default with the apn loaded into

Yes there is a simcard

---

### Post by alexfish on 2011-12-07
hi 

going to use two terminals to find some info , open up first terminal and enter this code to monitor the device
```
tr -s "\n" < /dev/ttyUSB0
```open up second terminal and enter the following codes , not sure if the device will respond to all, verizon
sometimes have ther own AT commands
```

echo -e "AT\r" > /dev/ttyUSB0
```if response
```
OK
``` then asume the device is responding so can see if there are any APN's on the device
```
echo -e "AT+CGDCONT?\r" > /dev/ttyUSB0
``` to find the operator
```
echo -e "AT+COPS?\r" > /dev/ttyUSB0
``` to find mcc and mnc codes
```
echo -e "AT+COPS=0,2\r" > /dev/ttyUSB0
echo -e "AT+COPS?\r" > /dev/ttyUSB0
``` to find operators in area
```
echo -e "AT+COPS=?\r" > /dev/ttyUSB0 
```this will take time while it searches
be patient

can post results

alexfish

---

### Post by LordVaine on 2011-12-08
jeff@jeff-N150:~$ tr -s "\n" < /dev/ttyACM0
bash: /dev/ttyACM0: No such file or directory


Is what i got there....

I looked for this ACM0 file in the dev folder, there is no such thing :/

---

### Post by alexfish on 2011-12-08
Hi
oops forgot to check your other thread as regards the tty

 use ttyUSB0

but can check the tty ports with
```
lsusb -al /dev/serial/by-id
``` as indicated in other thread  			#[**1**]("http://ubuntuforums.org/showpost.php?p=11473572&postcount=1")

so for example
```
tr -s "\n" < /dev/ttyUSB0
```

alexfish

---

### Post by LordVaine on 2011-12-08
jeff@jeff-N150:~$ echo -e "AT\r" > /dev/ttyusb0
bash: /dev/ttyusb0: Permission denied

---

### Post by alexfish on 2011-12-08
Looks like permission problems

can use sudo su command for each terminal before entering the modem commands

```
sudo su 
``` then enter the codes

or check the case of

 echo -e "AT\r" > /dev/ttyusb0 should be echo -e "AT\r" > /dev/ttyUSB0

---

### Post by LordVaine on 2011-12-08
Ok. Permissions worked, however when i put in the commands witht he modified ttyusb0 at the end, nothing happens, It just opens up a new command line..So now we are at the point where verizon has their own codes

---

### Post by alexfish on 2011-12-09
Need to see the results from the terminals

have edited the post               #[**4**]("http://ubuntuforums.org/showpost.php?p=11521420&postcount=4")  to USB0 

first enter this code in the terminal

```
ls -al /dev/serial/by-id
``` post the results this will show any tty* associated with the device and the permisions

then go to post               #[**4**]("http://ubuntuforums.org/showpost.php?p=11521420&postcount=4")  and follow exactly as is ensure to use two terminals 

am surprised this is not working[FONT=monospace] in the second terminal , use the sudo su command if necessary
[/FONT]```
echo -e "AT\r" > /dev/ttyACM0 
```always post results of any commands entered in the terminals , use copy and paste commands from mouse right click menus

---

### Post by LordVaine on 2011-12-09
root@jeff-N150:/home/jeff# ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-12-07 18:58 .
drwxr-xr-x 4 root root 80 2011-12-07 18:58 ..
lrwxrwxrwx 1 root root 13 2011-12-07 18:58 usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-12-07 18:58 usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if02-port0 -> ../../ttyUSB1
root@jeff-N150:/home/jeff# 

[COLOR=Red]here is the result from the other terminal, I hit enter and it opens a new line of code[/COLOR]

root@jeff-N150:/home/jeff# echo -e "AT\r" > /dev/ttyusb0
root@jeff-N150:/home/jeff# 


[COLOR=Red]Second terminal shows nothing, just a blinking line with no line to enter codes...here are the results from the other codes....[/COLOR]

root@jeff-N150:/home/jeff# lsusb -al /dev/serial/by-id
lsusb: invalid option -- 'a'
lsusb: invalid option -- 'l'
Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program
root@jeff-N150:/home/jeff# echo -e "AT+CGDCONT?\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff# echo -e "AT+COPS?\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff# echo -e "AT+COPS=0,2\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff# echo -e "AT+COPS?\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff# echo -e "AT+COPS=?\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff#

---

### Post by alexfish on 2011-12-10
> **LordVaine said:**
> root@jeff-N150:/home/jeff# ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-12-07 18:58 .
drwxr-xr-x 4 root root 80 2011-12-07 18:58 ..
lrwxrwxrwx 1 root root 13 2011-12-07 18:58 usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-12-07 18:58 usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if02-port0 -> ../../ttyUSB1
root@jeff-N150:/home/jeff# 

[COLOR=Red]here is the result from the other terminal, I hit enter and it opens a new line of code[/COLOR]

root@jeff-N150:/home/jeff# echo -e "AT\r" > /dev/ttyusb0
root@jeff-N150:/home/jeff# 


[COLOR=Red]Second terminal shows nothing, just a blinking line with no line to enter codes...here are the results from the other codes....[/COLOR]

root@jeff-N150:/home/jeff# lsusb -al /dev/serial/by-id
lsusb: invalid option -- 'a'
lsusb: invalid option -- 'l'
Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program
root@jeff-N150:/home/jeff# echo -e "AT+CGDCONT?\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff# echo -e "AT+COPS?\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff# echo -e "AT+COPS=0,2\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff# echo -e "AT+COPS?\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff# echo -e "AT+COPS=?\r" > /dev/ttyUSB0
root@jeff-N150:/home/jeff#

Note from the above
root@jeff-N150:/home/jeff# echo -e "AT\r" > [COLOR=Blue]/dev/ttyusb0[/COLOR]

had asked to look at the Typecase upper and lower case

should be  echo -e "AT\r" > [COLOR=Blue]/dev/ttyUSB0

[COLOR=Black]can try again . but forget about the "lsub" command for now this was a typo , [/COLOR]
[/COLOR]

---

### Post by LordVaine on 2011-12-10
Still Nothing even with the capital USB0. Same thing as before

---

### Post by alexfish on 2011-12-11
can try same codes with ttyUSB1

if there are no responses then will have to look further , need to find port that responds to basic AT command  , if no response , will have to look further.

can also post this command from the terminal
```
usb-devices
```

Do you have alternate method of connecting to the network?

alexfish

---

### Post by LordVaine on 2011-12-12
root@jeff-N150:/home/jeff# usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-13-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  9 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05c6 ProdID=9245 Rev=00.02
S:  Manufacturer=Qualcomm Incorporated
S:  Product=Qualcomm Gobi 2000
C:  #Ifs= 3 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0ac8 ProdID=c33f Rev=01.00
S:  Manufacturer=Namuga.
S:  Product=WebCam SCB-0340N
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=128mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-13-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-13-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-13-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=219b Rev=03.43
S:  Manufacturer=Broadcom Corp
S:  Product=Broadcom Bluetooth 2.1 Device
S:  SerialNumber=506313AE8E8E
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-13-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


Nothing on ttyUSB1. Yes the netboolk is hooked up to the wireless network

---

### Post by alexfish on 2011-12-13
have done some searching (googling) , not sure if the device has configured correctly , info indicates 2 ports
, usb-devices confirms the serial driver has bound to 2 parts of the device , all pointers are : the device should show 3 ports ttyUSB0, ttyUSB1, ttyUSB2 , not sure if this would prevent a connection , 

indications are the device needs to have firmware installed on the ubuntu system , they are closed source, (Bah), this may be needed to reset or switch the actual device on , you mention having installed the hardware detector , have you installed the firmware,  these should be available in the software center ,

if you have installed from other sources post results of
```
l /lib/firmware/gobi
```

---

### Post by LordVaine on 2011-12-14
Yes the firmware locations were from other sides from the previous thread I have linked you..

root@jeff-n150:/home/jeff# l/lib/firmware/gobi
amss.mbn apps.mbn UQCN.nbn

---

### Post by alexfish on 2011-12-14
can confirm that the gobi loader has been installed via the Sofware Centre, if not done : Install gobi loader

once done may have to add udev rule for the device , more on this later , 

can only try , don't know if it will be a success 

alexfish

---

### Post by LordVaine on 2011-12-15
how do you set a udev rule?

---

### Post by alexfish on 2011-12-15
Gobi info, the device should have two usb ID's

from info posted it is not possible to see what is happening , have read reports of modem-manager preventing gobi-loader working
[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/686418](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/686418)
but not sure if this is applicable here but may be a starting point

First going to blacklist the device with modem manager to see what happens

```
sudo gedit /lib/udev/rules.d/77-mm-usb-device-blacklist.rules
```added these lines 
```
# Qualcomm Gobi 2000 QDL
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9245", ENV{ID_MM_DEVICE_IGNORE}="1"
```below
> ENV{DEVTYPE}!="usb_device",  GOTO="mm_usb_device_blacklist_end"to look like
```

# do not edit this file, it will be overwritten on update

ACTION!="add|change", GOTO="mm_usb_device_blacklist_end"
SUBSYSTEM!="usb", GOTO="mm_usb_device_blacklist_end"
ENV{DEVTYPE}!="usb_device",  GOTO="mm_usb_device_blacklist_end"

# Qualcomm Gobi 2000 QDL
 ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9245", ENV{ID_MM_DEVICE_IGNORE}="1"
```reboot then list the devices with
```
usb-devices
```Post the results

once got the state of the device and the ID's can then look at the gobi udev rules.. will have to take this a step at a time .

alexfish

---

### Post by LordVaine on 2011-12-18
here is the whole blacklist

# do not edit this file, it will be overwritten on update

ACTION!="add|change", GOTO="mm_usb_device_blacklist_end"
SUBSYSTEM!="usb", GOTO="mm_usb_device_blacklist_end"
ENV{DEVTYPE}!="usb_device",  GOTO="mm_usb_device_blacklist_end"

# APC UPS devices
ATTRS{idVendor}=="051d", ENV{ID_MM_DEVICE_IGNORE}="1"

# Sweex 1000VA
ATTRS{idVendor}=="0925", ATTRS{idProduct}=="1234", ENV{ID_MM_DEVICE_IGNORE}="1"

# Agiler UPS
ATTRS{idVendor}=="05b8", ATTRS{idProduct}=="0000", ENV{ID_MM_DEVICE_IGNORE}="1"

# Krauler UP-M500VA
ATTRS{idVendor}=="0001", ATTRS{idProduct}=="0000", ENV{ID_MM_DEVICE_IGNORE}="1"

# Ablerex 625L USB
ATTRS{idVendor}=="ffff", ATTRS{idProduct}=="0000", ENV{ID_MM_DEVICE_IGNORE}="1"

# Belkin F6C1200-UNV
ATTRS{idVendor}=="0665", ATTRS{idProduct}=="5161", ENV{ID_MM_DEVICE_IGNORE}="1"

# Various Liebert and Phoenixtec Power devices
ATTRS{idVendor}=="06da", ENV{ID_MM_DEVICE_IGNORE}="1"

# Unitek Alpha 1200Sx
ATTRS{idVendor}=="0f03", ATTRS{idProduct}=="0001", ENV{ID_MM_DEVICE_IGNORE}="1"

# Various Tripplite devices
ATTRS{idVendor}=="09ae", ENV{ID_MM_DEVICE_IGNORE}="1"

# Various MGE Office Protection Systems devices
ATTRS{idVendor}=="0463", ATTRS{idProduct}=="0001", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="0463", ATTRS{idProduct}=="ffff", ENV{ID_MM_DEVICE_IGNORE}="1"

# CyberPower 900AVR/BC900D
ATTRS{idVendor}=="0764", ATTRS{idProduct}=="0005", ENV{ID_MM_DEVICE_IGNORE}="1"
# CyberPower CP1200AVR/BC1200D
ATTRS{idVendor}=="0764", ATTRS{idProduct}=="0501", ENV{ID_MM_DEVICE_IGNORE}="1"

# Various Belkin devices
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0980", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0900", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0910", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0912", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0551", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0751", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0375", ENV{ID_MM_DEVICE_IGNORE}="1"
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="1100", ENV{ID_MM_DEVICE_IGNORE}="1"

# HP R/T 2200 INTL (like SMART2200RMXL2U)
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="1f0a", ENV{ID_MM_DEVICE_IGNORE}="1"

# Powerware devices
ATTRS{idVendor}=="0592", ATTRS{idProduct}=="0002", ENV{ID_MM_DEVICE_IGNORE}="1"

# Palm Treo 700/900/etc
# Shouldn't be probed themselves, but you can install programs like
# "MobileStream USB Modem" which changes the USB PID of the device to something
# that isn't blacklisted.
ATTRS{idVendor}=="0830", ATTRS{idProduct}=="0061", ENV{ID_MM_DEVICE_IGNORE}="1"

# Belkin F5U183 Serial Adapter (unlikely to have a modem behind it)
ATTRS{idVendor}=="050d", ATTRS{idProduct}=="0103", ENV{ID_MM_DEVICE_IGNORE}="1"

# ATEN Intl UC-232A (Prolific)
ATTRS{idVendor}=="0557", ATTRS{idProduct}=="2008", ENV{ID_MM_DEVICE_IGNORE}="1"

# Prolific Technology, Inc. PL2303 Serial Port
ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", ENV{ID_MM_DEVICE_IGNORE}="1"

# Cygnal Integrated Products, Inc. CP210x
ATTRS{idVendor}=="10c4", ATTRS{idProduct}=="ea60", ENV{ID_MM_DEVICE_IGNORE}="1"

# QinHeng Electronics HL-340
ATTRS{idVendor}=="1a86", ATTRS{idProduct}=="7523", ENV{ID_MM_DEVICE_IGNORE}="1"

# Samsung Gobi 2000 QDL device (VL176)
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9244", ENV{ID_MM_DEVICE_IGNORE}="1"

# Qualcomm Gobi 2000 QDL
 ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9245", ENV{ID_MM_DEVICE_IGNORE}="1"

LABEL="mm_usb_device_blacklist_end"










Here is the other part




jeff@jeff-N150:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05c6 ProdID=9245 Rev=00.02
S:  Manufacturer=Qualcomm Incorporated
S:  Product=Qualcomm Gobi 2000
C:  #Ifs= 3 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0ac8 ProdID=c33f Rev=01.00
S:  Manufacturer=Namuga.
S:  Product=WebCam SCB-0340N
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=128mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=219b Rev=03.43
S:  Manufacturer=Broadcom Corp
S:  Product=Broadcom Bluetooth 2.1 Device
S:  SerialNumber=506313AE8E8E
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
jeff@jeff-N150:~$

---

### Post by alexfish on 2011-12-18
Looking at the rules, possible the device is already listed, from research a qdl device changes id when enabled.
Indications are it will go to an ID one up from the original IE: if product ID = 9244 then it will change to 9245.

only thing which will happen is modem-manager will ignore the device ,if the two id's for device are
> # Samsung Gobi 2000 QDL device (VL176)
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9244", ENV{ID_MM_DEVICE_IGNORE}="1"

# Qualcomm Gobi 2000 QDL
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9245", ENV{ID_MM_DEVICE_IGNORE}="1"so what we looking at from the usb-devices part of the device does not have a driver
> T: Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#= 2 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=05c6 ProdID=9245 Rev=00.02
S: Manufacturer=Qualcomm Incorporated
S: Product=Qualcomm Gobi 2000
C: #Ifs= 3 Cfg#= 1 Atr=e0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I: If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial
I: If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserialso need to find the modalias of the device
```
grep usb /sys/bus/usb/devices/*/modalias
```Post the results

need to look at gobi loader
```
l /lib/udev/rules.d
``` Can confirm "gobi_loader" is in the listing Yes or No

```
cat /lib/udev/rules.d/60-gobi-loader.rules
```Post the results

ADDED: note from your posts RE: the link [http://ubuntuforums.org/showthread.php?p=11473572#post11473572](http://ubuntuforums.org/showthread.php?p=11473572#post11473572) 
the device has Changed ID's from [COLOR=Red]"9244 to 9245" ,[/COLOR] so there for the i[COLOR=Blue]ndications are the device is ready[/COLOR]:
ONCE the ALL info is posted will give a link to a script to test the device ,

---

### Post by alexfish on 2011-12-18
can also test modem-manager , see if the device will list with this command

```
dbus-send --system --print-reply --dest=org.freedesktop.ModemManager /org/freedesktop/ModemManager org.freedesktop.ModemManager.EnumerateDevices
```

alexfish

---

### Post by LordVaine on 2011-12-18
jeff@jeff-N150:~$ grep usb /sys/bus/usb/devices/*/modalias
/sys/bus/usb/devices/1-0:1.0/modalias:usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/1-4:1.0/modalias:usb:v05C6p9245d0002dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-4:1.1/modalias:usb:v05C6p9245d0002dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-4:1.2/modalias:usb:v05C6p9245d0002dc00dsc00dp00icFFiscFFipFF
/sys/bus/usb/devices/1-7:1.0/modalias:usb:v0718p0441d0110dc00dsc00dp00ic08isc06ip50
/sys/bus/usb/devices/1-8:1.0/modalias:usb:v0AC8pC33Fd0100dcEFdsc02dp01ic0Eisc01ip00
/sys/bus/usb/devices/1-8:1.1/modalias:usb:v0AC8pC33Fd0100dcEFdsc02dp01ic0Eisc02ip00
/sys/bus/usb/devices/2-0:1.0/modalias:usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/3-0:1.0/modalias:usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/4-0:1.0/modalias:usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/4-2:1.0/modalias:usb:v0A5Cp219Bd0343dcE0dsc01dp01icE0isc01ip01
/sys/bus/usb/devices/4-2:1.1/modalias:usb:v0A5Cp219Bd0343dcE0dsc01dp01icE0isc01ip01
/sys/bus/usb/devices/4-2:1.2/modalias:usb:v0A5Cp219Bd0343dcE0dsc01dp01icFFiscFFipFF
/sys/bus/usb/devices/4-2:1.3/modalias:usb:v0A5Cp219Bd0343dcE0dsc01dp01icFEisc01ip01
/sys/bus/usb/devices/5-0:1.0/modalias:usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00
jeff@jeff-N150:~$ 


jeff@jeff-N150:~$ l /lib/udev/rules.d
39-libmtp.rules                    75-tty-description.rules
40-fuse-utils.rules                77-mm-ericsson-mbm.rules
40-gnupg.rules                     77-mm-longcheer-port-types.rules
40-hplip.rules                     77-mm-pcmcia-device-blacklist.rules
40-ia64.rules                      77-mm-platform-serial-whitelist.rules
40-inputattach.rules               77-mm-qdl-device-blacklist.rules
40-libgphoto2-2.rules              77-mm-simtech-port-types.rules
40-libsane.rules                   77-mm-usb-device-blacklist.rules
40-ppc.rules                       77-mm-usb-device-blacklist.rules~
40-usb-media-players.rules         77-mm-x22x-port-types.rules
40-usb_modeswitch.rules            77-mm-zte-port-types.rules
40-xdiagnose.rules                 77-nm-olpc-mesh.rules
40-xserver-xorg-video-intel.rules  78-graphics-card.rules
42-qemu-usb.rules                  78-sound-card.rules
45-fuse.rules                      80-drivers.rules
50-firmware.rules                  80-mm-candidate.rules
50-udev-default.rules              80-udisks.rules
55-dm.rules                        85-brltty.rules
56-hpmud_support.rules             85-hdparm.rules
60-cdrom_id.rules                  85-hplj10xx.rules
60-gobi.rules*                     85-keyboard-configuration.rules
60-persistent-alsa.rules           85-pcmcia.rules
60-persistent-input.rules          85-regulatory.rules
60-persistent-serial.rules         85-usbmuxd.rules
60-persistent-storage-dm.rules     90-alsa-restore.rules
60-persistent-storage.rules        90-alsa-ucm.rules
60-persistent-storage-tape.rules   90-libgpod.rules
60-persistent-v4l.rules            90-pulseaudio.rules
61-accelerometer.rules             95-cd-devices.rules
61-gnome-bluetooth-rfkill.rules    95-keyboard-force-release.rules
62-bluez-hid2hci.rules             95-keymap.rules
64-xorg-xkb.rules                  95-udev-late.rules
66-xorg-synaptics-quirks.rules     95-upower-battery-recall-dell.rules
69-cd-sensors.rules                95-upower-battery-recall-fujitsu.rules
69-xorg-vmmouse.rules              95-upower-battery-recall-gateway.rules
69-xserver-xorg-input-wacom.rules  95-upower-battery-recall-ibm.rules
70-printers.rules                  95-upower-battery-recall-lenovo.rules
70-udev-acl.rules                  95-upower-battery-recall-toshiba.rules
75-cd-aliases-generator.rules      95-upower-csr.rules
75-net-description.rules           95-upower-hid.rules
75-persistent-net-generator.rules  95-upower-wup.rules
75-probe_mtd.rules                 README
jeff@jeff-N150:~$ 


jeff@jeff-N150:~$ cat /lib/udev/rules.d/60-gobi-loader.rules
cat: /lib/udev/rules.d/60-gobi-loader.rules: No such file or directory
jeff@jeff-N150:~$

---

### Post by alexfish on 2011-12-18
your listing shows
60-gobi.rules*
not what had expected from ( gobi_loader Ubuntu version)

looking at the module
grep -i v05C6 /lib/modules/*/modules.alias
shows these lines , as you can see the qcserial loads for the two device ID's
as is with most of these devices in the kernel module
> /lib/modules/3.0.0-12-generic/modules.alias:alias usb:v05C6p9245d*dc*dsc*dp*ic*isc*ip* qcserial
/lib/modules/3.0.0-12-generic/modules.alias:alias usb:v05C6p9244d*dc*dsc*dp*ic*isc*ip* qcserialfrom info looks as if the device has configured with the exception of correct driver binding (will leave your set up for gobi as is)

looking at the modalias, all the device ports have the same modalias,  would have assumed seeing qcserial attached to all the ports . if the device ID = 9244 then possible the qcserial is loading at wrong time for the device
need to try and load the qcserial when ID = 9245
> jeff@jeff-N150:~$ grep usb /sys/bus/usb/devices/*/modalias
/sys/bus/usb/devices/1-4:1.0/modalias:usb:v05C6p9245d0002dc00dsc00dp00icFFiscFF ipFF
/sys/bus/usb/devices/1-4:1.1/modalias:usb:v05C6p9245d0002dc00dsc00dp00icFFiscFF ipFF
/sys/bus/usb/devices/1-4:1.2/modalias:usb:v05C6p9245d0002dc00dsc00dp00icFFiscFF ipFFcan try these commands from the terminal

```
sudo modprobe -r qcserial
``````
sudo modprobe qcserial
```then list the device with
```
ls -al /dev/serial/by-id
```and
```
usb-devices
```locate the lines which indicate the device and POST only those lines
alexfish

---

### Post by LordVaine on 2011-12-18
jeff@jeff-N150:~$ sudo modprobe -r qcserial
[sudo] password for jeff: 
jeff@jeff-N150:~$ sudo modprobe -r qcserial
jeff@jeff-N150:~$ sudo modprobe qcserial
jeff@jeff-N150:~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 80 2011-12-18 20:45 .
drwxr-xr-x 4 root root 80 2011-12-18 20:45 ..
lrwxrwxrwx 1 root root 13 2011-12-18 20:45 usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-12-18 20:45 usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if02-port0 -> ../../ttyUSB1
jeff@jeff-N150:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05c6 ProdID=9245 Rev=00.02
S:  Manufacturer=Qualcomm Incorporated
S:  Product=Qualcomm Gobi 2000
C:  #Ifs= 3 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0ac8 ProdID=c33f Rev=01.00
S:  Manufacturer=Namuga.
S:  Product=WebCam SCB-0340N
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=128mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=219b Rev=03.43
S:  Manufacturer=Broadcom Corp
S:  Product=Broadcom Bluetooth 2.1 Device
S:  SerialNumber=506313AE8E8E
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.00
S:  Manufacturer=Linux 3.0.0-14-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
jeff@jeff-N150:~$ 



[COLOR="Red"]The Probe codes did nothing...[/COLOR]

---

### Post by alexfish on 2011-12-19
mm!.

need to go to this link

Re: How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10] POST #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61")

copy the script using gedit (text editor) save the file in home directory save as eject.tcl
although the script was written for external devices the part of the script that is usefull is the arg tty.

once the file is saved in the home directory use the following command
```
 ./eject.tcl tty
``` post the results

as said not sure if this device is correctly configured , from the driver side , comments indicate modem-manager has the necessary to communicate with the device, but not sure which port is used for communicating will need to research further

from info
> ttyUSB0  ;; could be "if 0"
ttyUSB1  ;; could be "if 1"
ttyUSB2  ;; could be "if 2"your device
> ttyUSB0  ;; could be "if 1"
ttyUSB1  ;; could be "if 2"the info from the script will allow comparison of the tty*> udev and the struct of the driver, but not the bit without driver.

So still not sure what is happening with the device (the installed version of gobi loader) 

alexfish

---

### Post by alexfish on 2011-12-20
Just had a look at Ubuntu 11.10
Looks if package tcl , not installed at default so the scripts.tcl will not run:(

but should run on Ubuntu upto 11.04

---

### Post by LordVaine on 2011-12-22
is there anything else we can do?

---

### Post by alexfish on 2011-12-23
have been looking at the default serial apps or tools in 11.10 only thing available is pyserial , would need to write a script to give what is required (no time at present) , since most of debgugging is easier in tclsh (my personnal favorite programing tool for this area) and also for many other Linux users , think missing tclsh not a good move, (enough said). hopping to see it back if Ubuntu goes to DVD install
Ok can suggest downloading freewrap version of tclsh , since your fortunate to have alternate internet connection from here.

[COLOR=Blue][http://en.sourceforge.jp/projects/sfnet_freewrap/downloads/freewrap/freeWrap%206.51/freewrapTCLSH651.tar.gz/](http://en.sourceforge.jp/projects/sfnet_freewrap/downloads/freewrap/freeWrap%206.51/freewrapTCLSH651.tar.gz/)[/COLOR]

once downloaded unpack the file, locate the freewrap TCLSH , copy it ,
paste it in the home directory , rename the to tclsh

to run a tcl script from the home directory

```
./tclsh ./your script
```IE if the script is named eject.tcl using the argv tty
```
./tclsh ./eject tty
```alexfish

PS thanks for the prompt what next.. cos tcl serial is used in the script , 
also has reminded me to compile tcl into some programs .:confused:

---

