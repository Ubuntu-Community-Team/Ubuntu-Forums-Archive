---
title: "E173 on T-Mobile"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by holmez on 2011-03-18
Hi, I'm hoping someone can help me with this one. I know, from detailed google searching, and several threads on here, that a number of people have this mobile broadband modem, and have got it working. I'm running Ubuntu 10.04

I have got usb_modeswitch working, however, I'm not having any success when I do modprobe. (It seems that this fixes the problem for everybody else, but not me). It doesn't seem to be attaching any driver to the modem, see output below.

david@holmez:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 12d1:1c05 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
david@holmez:~$ sudo modprobe usbserial vendor=0x12d1 product=0x1c05
[sudo] password for david: 
david@holmez:~$ usb-devices


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c05 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=02(commc) Sub=02 Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=02(commc) Sub=02 Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


Any help would be much appreciated. Please bear in mind though that I have absolutely no internet from my Ubuntu, so I won't be able to do a sudo apt-get. I think I can get what I need from the packages.ubuntu website, except, I don't know what I might need, or where to go from here.

---

### Post by alexfish on 2011-03-19
hi
can have a look here
[How To : Mobile Broadband Connections [ Ubuntu  10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")
post #2
also solved.
[http://ubuntuforums.org/showthread.php?t=1705048](http://ubuntuforums.org/showthread.php?t=1705048)
take note of new usb_modeswitch rules,as regards Huawie devices,
see what happens 
if failing , what is the source of the installed usb_modeswitch


regards
alexfish

---

### Post by holmez on 2011-03-19
hello Alexfish, and thanks for your response.

I have seen both of those, and tried them (although I'll try rereading the first one - I seem to be going round in circles - and have spent over 3 weeks now trying, googling, trying, etc - and it seems that a lot of new problems, posts and solutions).

The problem is not with usb_modeswitch, but with the

sudo modprobe usbserial vendor=0x12d1 product=0x1c05

Even sudo modprobe option fails to load a driver. <Edit to add this comment>

---

### Post by alexfish on 2011-03-20
hi

thought that may be the case . but need to know if the usb_modeswitch is of Ubuntu repo or of debian, or from usb_modeswitch source
can also confirm the  contents of  /etc/usb_modeswitch.d/* , file for your device,the contents can be of importance as regards the correct switching
does the device have a sd card inserted, if so can try removing, see what happens

does anything show with the modprobe -v option (verbose) can post the results

can also confirm the listing of the commands , after the modprobe

```
ls -al /dev/usb*
```and

```
ls -al /dev/ttyUSB*
```

alexfish

---

### Post by holmez on 2011-03-20
Hi Alexfish.

The version of usb_modeswitch was downloaded from packages.ubuntu
I had originally started attempting to compile it from source, but failed because of dependencies.

As you'll see below, /etc/usb_modeswitch.d/* doesn't seem to exist. I'm  under the impression that when I do sudo usb_modeswitch manually, it  uses /etc/usb_modeswitch.conf (relevant contents attached below). Also,  there is no SD micro card installed (it does have the slot - but it's no  good to me, as I only use SD, and my laptop has its own SD slot)

/etc/usb_modeswitch.conf:
########################################################
# Huawei E220 (aka "Vodafone EasyBox II", aka "T-Mobile wnw Box Micro")
# Huawei E230
# Huawei E270
# Huawei E870
# and probably most other Huawei devices (just adapt product ID)
#
# Two options: 1. removal of "usb-storage"  2. the special control
# message found by Miroslav Bobovsky
#
# Contributor: Hans Kurent, Denis Sutter, Vincent Teoh

DefaultVendor=  0x12d1
DefaultProduct= 0x1c0b

TargetVendor=   0x12d1
TargetProduct=  0x1c05

# choose one of these:
;DetachStorageOnly=1
;HuaweiMode=1

MessageContent="55534243123456780000000000000011060000000000000000000000000000"


Terminal output:
david@holmez:~$ ls /etc/usb_modeswitch.d/*
ls: cannot access /etc/usb_modeswitch.d/*: No such file or directory
david@holmez:~$ sudo modprobe -v option
insmod /lib/modules/2.6.32-28-generic/kernel/drivers/usb/serial/option.ko 
david@holmez:~$ ls -al /dev/usb*
crw-rw---- 1 root root 252, 0 2011-03-20 15:38 /dev/usbmon0
crw-rw---- 1 root root 252, 1 2011-03-20 15:38 /dev/usbmon1
crw-rw---- 1 root root 252, 2 2011-03-20 15:38 /dev/usbmon2
crw-rw---- 1 root root 252, 3 2011-03-20 15:38 /dev/usbmon3
crw-rw---- 1 root root 252, 4 2011-03-20 15:38 /dev/usbmon4
crw-rw---- 1 root root 252, 5 2011-03-20 15:38 /dev/usbmon5
david@holmez:~$ ls -al /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory
david@holmez:~$

---

### Post by alexfish on 2011-03-20
hi 

looks as if the data package is missing , the data package contains udev rules and usb_modeswitch.d/files
the udev rules should  allocate the correct device class (this enables the driver to attach to the device):
Noted from : If#= 0 Alt= 0 #EPs= 3 [COLOR=Blue]Cls=02(commc) Sub=02 Prot=ff [/COLOR]Driver=(none)
although your device is not listed , if have read through the thread (solved) the MessageContent are different to the .conf on your system
and also has Message end point address
 
suggest installing usb_modeswitch datapackage

also latest usb_modeswitch and data packge is available from
 
[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)

ADDED [COLOR=Blue]the latest usb_modeswitch datapackage contains this device See foot of page[/COLOR]


(can put them on a usb stick) they should self install when in ubuntu

then need to make the file for the device
```
sudo gedit /etc/usb-modeswitch.d/12d1:1c0b
```copy and paste the below 
```
######### #########
# Huawei E173s # Huawei E173s

DefaultVendor= 0x12d1
DefaultProduct= 0x1c0b 

TargetVendor= 0x12d1
TargetProduct= 0x1c05

CheckSuccess = 20

MessageEndpoint= 0x0F
MessageContent="55534243000000000000000000000011060000000100000000000000000000"
```safe the file and exit

at present there is no udev rule, so will first try flipping the device from the terminal commands

plug the device in after boot and note the id of the device from lsusb command
```
lsusb
```then 
```
usb_modeswitch -c /etc/usb_modeswitch.d/12d1:1c0b
```note any change with the lsusb command

if the device id shows [COLOR=Blue]12d1:1c05[/COLOR] , send the modprobe command (note your device does not have an entry in the option module) so will have to see if the generic driver will work
```
sudo modprobe usbserial vendor=0x12d1 product=0x1c05
```see if the ports have configured
```
ls /dev/ttyUSB*
```if this a success then will proceed to write the udev rules to automate

**should not need the above** , latest data package contains this device, only thing is to check if the drivers are loading

here is the listing from the data package

```
#######################################################
# Huawei E173s

DefaultVendor= 0x12d1
DefaultProduct=0x1c0b

TargetVendor=  0x12d1
TargetProductList="1c05,1c08"

MessageContent="55534243123456780000000000000011062000000100000000000000000000"

CheckSuccess=20
```for reference the udev rules contain these lines

```
# This adds the device ID to the "option" driver after a warm boot
# in cases when the device is yet unknown to the driver
ATTR{bInterfaceClass}=="ff", ATTR{bInterfaceNumber}=="00", ATTRS{bNumConfigurations}=="*", RUN+="usb_modeswitch --driver-bind %p %s{idVendor} %s{idProduct} %E{PRODUCT}"
```So can suggest attaching the device prior to booting up / see what happens

---

### Post by holmez on 2011-03-21
> **alexfish said:**
> hi 

looks as if the data package is missing , the data package contains udev rules and usb_modeswitch.d/files
the udev rules should  allocate the correct device class (this enables the driver to attach to the device):
Noted from : If#= 0 Alt= 0 #EPs= 3 [COLOR=Blue]Cls=02(commc) Sub=02 Prot=ff [/COLOR]Driver=(none)
although your device is not listed , if have read through the thread (solved) the MessageContent are different to the .conf on your system
and also has Message end point address
 
suggest installing usb_modeswitch datapackage

also latest usb_modeswitch and data packge is available from
 
[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)



Think this is where everything has been going wrong for me. I'm getting dependency issues all over the place when I try and install usb-modeswitch or usb-modeswitch-data

Requires dpkg (>=1.15.7.2)

The only one I can see (currently) is 1.15.8.10, but that won't install because it breaks existing dependencies.

I think this is where everything was going wrong for me originally (I originally tried to compile it from source - but that failed because of dependencies).

I think this is where my noob status comes in, as I have no idea how to resolve the dependency issues (especially when I'm continually having to reboot into windoze to download the packages, then reboot into ubuntu to attempt to install it.)

I even tried using the 'squeeze' (1.1.4-2) version of usb-modeswitch, but still no luck.

---

### Post by holmez on 2011-03-22
I think I have made progress.

I uninstalled the usb_modeswitch that was originally installed.
Installed the usb-modeswitch-data_20100826-1+squeeze0_all.deb (the latest version wouldn't install because of dependency problems.)
Installed the usb-modeswitch_1.1.4.2_i386.deb (again, the latest wouldn't install)

The file /etc/usb_modeswitch.d/12d1:1c0b existed and the contents are

#######################################################
# Huawei E173s

DefaultVendor= 0x12d1
DefaultProduct=0x1c0b

TargetVendor=  0x12d1
TargetProduct= 0x1c05

MessageContent="55534243123456780000000000000011062000000100000000000000000000"

CheckSuccess=20


The command sudo usb_modeswitch -c /etc/usb_modeswitch.d/12d1:1c0b worked.

However, sudo modprobe usbserial vendor=0x12d1 product=0x1c05 still doesn't assign a driver. Nor does sudo modprobe option (which I have seen suggested elsewhere)

I'll go away now and try sudo modprobe -v option (which you suggested earlier) and post the results here.

---

### Post by alexfish on 2011-03-22
hi

MM! see what you mean , will have to take it from here

[http://packages.ubuntu.com/lucid/usb-modeswitch](http://packages.ubuntu.com/lucid/usb-modeswitch)

don't forget the data package

then can try setting up the rules as mentioned above

see what happens , 

**Just Noticed your post above (strange time delay ) .. May be no need for above**

can post the results of the 
```
usb-devices
```and 
```
usb_modeswitch -e
```and contents of udev rules
```
cat /lib/udev/rules.d/40-usb_modeswitch.rules
```alexfish

---

### Post by holmez on 2011-03-23
Hi Alexfish.

I've posted the relevant parts below (but I'll attach the full outputs, just in case it is relevant)


david@holmez:~$ sudo modprobe -v option
insmod /lib/modules/2.6.32-28-generic/kernel/drivers/usb/serial/option.ko 

david@holmez:~$ usb-devices
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c05 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

david@holmez:~$ usb_modeswitch -e
 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.4 (C) Josua Dietze 2010
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !


david@holmez:~$ cat /lib/udev/rules.d/40-usb_modeswitch.rules
# Part of usb-modeswitch-data, version 20100825
#
# This file is intended for USB_ModeSwitch version >= 1.1.4
# but will not break anything if used with versions >= 1.0.3
#

ACTION!="add", GOTO="modeswitch_rules_end"

# This adds a symlink "gsmmodem[n]" to ttyUSB ports with interrupt transfer;
# will work only with wrapper from 1.1.4 and above (otherwise ignored)
KERNEL=="ttyUSB*", DRIVERS=="option1|usbserial", PROGRAM="/usr/sbin/usb_modeswitch_dispatcher --symlink-name %p", SYMLINK="%c"


SUBSYSTEM!="usb", GOTO="modeswitch_rules_end"

# This adds the device ID to the "option" driver after a warm boot
# in cases when the device is yet unknown to the driver
ATTR{bInterfaceClass}=="ff", ATTR{bInterfaceNumber}=="00", RUN+="usb_modeswitch --driver-bind %p %s{idVendor} %s{idProduct} %E{PRODUCT}"

# Most known install partitions are on interface 0, one on 5, one on 9
ATTRS{bInterfaceNumber}!="0[059]", GOTO="modeswitch_rules_end"

# only storage class devices are handled; negative
# filtering here would exclude some quirky devices
ATTRS{bDeviceClass}=="08", GOTO="modeswitch_rules_begin"
ATTRS{bInterfaceClass}=="08", GOTO="modeswitch_rules_begin"
GOTO="modeswitch_rules_end"


LABEL="modeswitch_rules_begin"

# Huawei E630
ATTRS{idVendor}=="1033", ATTRS{idProduct}=="0035", RUN+="usb_modeswitch '%b/%k'"

# Huawei E169
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"

# Huawei E220, E230, E270, E870
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="usb_modeswitch '%b/%k'"

# Huawei U7510 / U7517
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="101e", RUN+="usb_modeswitch '%b/%k'"

# Huawei U8110 (Android smartphone)
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1031", RUN+="usb_modeswitch '%b/%k'"

# Huawei E180
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1414", RUN+="usb_modeswitch '%b/%k'"

# Huawei, newer modems
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (Huawei) K3806
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14ad", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (Huawei) K4605
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14c1", RUN+="usb_modeswitch '%b/%k'"

# Huawei K3765
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1520", RUN+="usb_modeswitch '%b/%k'"

# Huawei K4505
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1521", RUN+="usb_modeswitch '%b/%k'"

# Huawei R201
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1523", RUN+="usb_modeswitch '%b/%k'"

# Huawei E1553
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1553", RUN+="usb_modeswitch '%b/%k'"

# Huawei E173
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1557", RUN+="usb_modeswitch '%b/%k'"

# Huawei E173s
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="usb_modeswitch '%b/%k'"

LABEL="modeswitch_rules_end"


Best regards,
David

---

### Post by holmez on 2011-03-25
There's definitely something up with my linux setup, it's not the laptop.

I've just tried it on a clean ubuntu 10.04 install. Same version of usb_modeswitch_data and usb_modeswitch, and it works perfectly, first time.

But my usual one (ubuntu 10.04.2) doesn't assign the driver to the modem. I've just tried completely uninstalling usb-modeswitch and usb-modeswitch-data and reinstalling them again, but still no luck.

The only other option (which I certainly don't fancy) is to make the clean install my standard and setup everything on it (something I hoped I'd never have to do when I moved to ubuntu 2+ years ago)

David.

---

### Post by alexfish on 2011-03-26
hi

not sure what could be wrong , (udev rules or module problem ?)

can suggest trying to remove the option driver first (if loaded)  then see if the usbserial driver will load
```
sudo -r option
```then 
```
sudo modprobe -v usbserial vendor=0x12d1 product=0x1c05
```
if this fails will have to look further .

alexfish

---

### Post by holmez on 2011-03-27
> **alexfish said:**
> hi

not sure what could be wrong , (udev rules or module problem ?)

can suggest trying to remove the option driver first (if loaded)  then see if the usbserial driver will load
```
sudo modprobe -r option
```then 
```
sudo modprobe -v usbserial vendor=0x12d1 product=0x1c05
```if this fails will have to look further .

alexfish


Thank you so much for all of your help. That worked.

I think I can (attempt) to follow the instructions in the other threads on automating all of this.

Would there be anything I'd need to do to ensure that 'option' doesn't load on startup?

---

### Post by alexfish on 2011-03-27
hi

before finalizing other rules

can boot the computer up , then when in the state before removing the option driver

see if any rules in existence  , can post results of

```
 grep option /var/log/udev
```alexfish

if this does not show anything of the obvious will  look at the udevadm

---

### Post by holmez on 2011-03-28
> **alexfish said:**
> hi

before finalizing other rules

can boot the computer up , then when in the state before removing the option driver

see if any rules in existence  , can post results of

```
 grep option /var/log/udev
```alexfish

if this does not show anything of the obvious will  look at the udevadm

Hi,

It shows nothing.

david@holmez:~$ grep option /var/log/udev
david@holmez:~$

---

### Post by alexfish on 2011-03-28
hi

since the [COLOR=Blue]option driver appears to be loading[/COLOR] after connecting the device (and modeswitching). do not remove the option module

first check that the device has switched with the usb-devices command
should see line
> P: Vendor=12d1 ProdID=1c05 Rev=01.02then
see if the file [COLOR=Blue] new_id exists[/COLOR]
```
ls -al /sys/bus/usb-serial/drivers/option1/new_id
```if the file exist try this command
```
echo "0x12d1 0x1c05" > /sys/bus/usb-serial/drivers/option1/new_id
```if the file does not exist then try these commands
```
sudo modprobe -r option
sudo modprobe -a option
```then use the code 
```
echo "0x12d1 0x1c05" > /sys/bus/usb-serial/drivers/option1/new_id
```see what happens,
use the usb-devices command

if it fails will have to resort to generic driver

alexfish

---

### Post by holmez on 2011-03-30
Hello Alexfish

Attached is the output from your suggestions.

Regards,

David

---

### Post by alexfish on 2011-03-30
hi

can try run the commands as root

open up terminal then enter (root terminal)
```
sudo su
```then run the commands without the "sudo" command

see what happens

alexfish

---

### Post by holmez on 2011-03-31
That worked. It now shows "option" as the driver. I haven't included the output, because there wasn't any output to show.

Just out of interest, what's the difference between usb-serial and option for the driver?

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c05 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

---

### Post by alexfish on 2011-03-31
hi

option driver was specially developed to allow correct flow control structures for wwan devices

can have a look here to see the difference , although  a first reading may be not be obvious , reading through a few times helps,
[http://lxr.linux.no/#linux+v2.6.35/drivers/usb/serial/option.c](http://lxr.linux.no/#linux+v2.6.35/drivers/usb/serial/option.c)
[http://lxr.linux.no/#linux+v2.6.35/drivers/usb/serial/usb-serial.c](http://lxr.linux.no/#linux+v2.6.35/drivers/usb/serial/usb-serial.c)

note the lines at static struct and settings for the size of buffers

Now that the device can register with the option driver , do you need to write some rules ( + possible a script.sh to handle the commands been used )
 or are you comfortable using the terminal 

regards

alexfish

---

### Post by holmez on 2011-04-02
Hello Alexfish.

Thanks for all your help. I probably will need a little bit of help with writing some rules to automate this.

So far, I can tell you that /lib/udev/rules.d/40-usb_modeswitch.rules contains the line:
# Huawei E173s
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="usb_modeswitch '%b/%k'"

Regards,
David

---

### Post by alexfish on 2011-04-03
Hi

after  bit of debugging with udev rules and the new_id script found possible problem , other udev rules or the kernel  may have an effect on the script, or vice versa

so will avoid the udev rule for now and will use script only.

try the following:if a novice use copy and paste
```
sudo gedit /usr/bin/new_id:1c05
``` add the following code
```
#!/bin/bash
logger "new_id:1c05 Stage1: 19d2 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
modprobe -a option
logger "new_id:1c05 Stage2: 19d2 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
echo "19d2 1c05" > /sys/bus/usb-serial/drivers/option1/new_id
logger "new_id:1c05 Stage3: 19d2 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
```double check the code ,save and exit

enter root terminal and enter the following codes
```
sudo su 
cd /usr/bin
chmod 777 new_id:1c05
exit
```try the script
```
sudo new_id:1c05
```once run the application will log the activity in the "log file viewer > messages"

if everything OK , can edit the menus

right click Applications > Edit Menus

in Left panel click on "Internet" , or any part you want the menu entry in

right panel click "+New Item"

in the Create Launcher click "Browse"

in the Choose Application click "File System" , click on "usr"  > "bin" > "new_id:1c05"

in the Create Launcher "Name: box" , name the file new_id:1c05

if you want give it a description

click OK, the app should now be in the menus

ADDED:

The menu command will not work unless user and app is add in suders , so below is udev rule to try , 
```
sudo gedit /etc/udev/rules.d/new_id:1c05.rules
```add the following
```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="/usr/bin/new_id:1c05"
```if rule a problem at boot , remove the device and reboot, then connect
see what happens 

it will be interesting to see what the logger shows , in logfile viewer

**Added 4 April 2011:**
Have done further debugging , it appears the udev rules can be triggered by the number of interfaces the device has IE if 3 interface + the CD = udev rule may trigger 4 times, so have modified the rule to reduce the triggers
This rule will only trigger once by the interface number 03 and the Protocol "ff". at present can't prevent action of the CD, 
So can try this rule instead
```
SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:v12D1p1c0b*", ATTRS{bNumEndpoints}=="03", ATTRS{bInterfaceProtocol}=="ff", RUN+="/usr/bin//usr/bin/new_id:1c05"

```updated first rule (typo error " quote missing
alexfish

---

### Post by alexfish on 2011-04-03
Can also suggest trying Sakis3g
look at

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

if sakis3g installed can test by disabling the udev rules first
disable the udev rule by placing # at start of line
see what happens

alexfish

---

### Post by holmez on 2011-04-06
> **alexfish said:**
> Hi

after  bit of debugging with udev rules and the new_id script found possible problem , other udev rules or the kernel  may have an effect on the script, or vice versa

so will avoid the udev rule for now and will use script only.

try the following:if a novice use copy and paste
```
sudo gedit /usr/bin/new_id:1c05
``` add the following code
```
#!/bin/bash
logger "new_id:1c05 Stage1: 19d2 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
modprobe -a option
logger "new_id:1c05 Stage2: 19d2 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
echo "19d2 1c05" > /sys/bus/usb-serial/drivers/option1/new_id
logger "new_id:1c05 Stage3: 19d2 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
```double check the code ,save and exit

enter root terminal and enter the following codes
```
sudo su 
cd /usr/bin
chmod 777 new_id:1c05
exit
```try the script
```
sudo new_id:1c05
```once run the application will log the activity in the "log file viewer > messages"

if everything OK , can edit the menus

right click Applications > Edit Menus

in Left panel click on "Internet" , or any part you want the menu entry in

right panel click "+New Item"

in the Create Launcher click "Browse"

in the Choose Application click "File System" , click on "usr"  > "bin" > "new_id:1c05"

in the Create Launcher "Name: box" , name the file new_id:1c05

if you want give it a description

click OK, the app should now be in the menus

ADDED:

The menu command will not work unless user and app is add in suders , so below is udev rule to try , 
```
sudo gedit /etc/udev/rules.d/new_id:1c05.rules
```add the following
```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="/usr/bin/new_id:1c05"
```if rule a problem at boot , remove the device and reboot, then connect
see what happens 

it will be interesting to see what the logger shows , in logfile viewer

**Added 4 April 2011:**
Have done further debugging , it appears the udev rules can be triggered by the number of interfaces the device has IE if 3 interface + the CD = udev rule may trigger 4 times, so have modified the rule to reduce the triggers
This rule will only trigger once by the interface number 03 and the Protocol "ff". at present can't prevent action of the CD, 
So can try this rule instead
```
SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:v12D1p1c0b*", ATTRS{bNumEndpoints}=="03", ATTRS{bInterfaceProtocol}=="ff", RUN+="/usr/bin//usr/bin/new_id:1c05"

```updated first rule (typo error " quote missing
alexfish


It seems that the original rules suggestion worked, and worked automatically.

I only have to do the usb_modeswitch, then the sudo modprobe -r manually and then the rules would automatically trigger and the internet connection automatically connect (I've switched automatic connection on)

I'm trying your additions now.
I'm also assuming that this part of the code ```
RUN+="/usr/bin//usr/bin/new_id:1c05" 
``` was a slight error.

---

### Post by alexfish on 2011-04-06
appols, some typos had crept in , had been testing the rules with different devices + some of the scripts had system checking in place,(these where writen in tcl)
this script whould act as a wrapper , 
as mentioned it seems the udev rule can get triggered for every interface of the device , so had to try rules with which whould trigger once
yes there are some errors (well spotted), burnt to much midnight oil on the wrapper script (will post this one latter as this script can act for all option driven devices) , anyhow more about that later,

have noticed other comment

so assuming the option driver is already loaded it is a simple case to edit the script file

for now will use simple bash script and udev rule specific to one device: so here is a re write
```
sudo gedit /usr/bin/new_id:1c05
```the script:
```
#!/bin/bash
logger "new_id:1c05 Stage1: 12d1 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
# Option to load option driver
# modprobe -a option
logger "new_id:1c05 Stage2: 12d1 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
echo "12d1 1c05" > /sys/bus/usb-serial/drivers/option1/new_id
logger "new_id:1c05 Stage3: 12d1 1c05 > /sys/bus/usb-serial/drivers/option1/new_id"
```double check the code ,save and exit

enter root terminal and enter the following codes
```
sudo su 
cd /usr/bin
chmod 777 new_id:1c05
exit
```try the script
```
sudo new_id:1c05
```can look in the logfile viewer to note the activity
everthing working ,edit the rules
```
sudo gedit /etc/udev/rules.d/new_id:1c05.rules
```
the rule
```
SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:v12D1p1c0b*", ATTRS{bNumEndpoints}=="03", ATTRS{bInterfaceProtocol}=="ff", RUN+="/usr/bin/usr/bin/new_id:1c05"
```

also mentioned
> I only have to do the usb_modeswitch (from previous post mention rule)
> So far, I can tell you that /lib/udev/rules.d/40-usb_modeswitch.rules contains the line:
# Huawei E173s
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="usb_modeswitch '%b/%k'"

is this rule working , or still manually calling modeswitch from the terminal

alexfish

---

### Post by holmez on 2011-04-07
> **alexfish said:**
> 

is this rule working , or still manually calling modeswitch from the terminal

alexfish

I'm still manually calling modeswitch from the terminal. The rule is there, (it was listed in post #10) and I've attached it (almost) as is (I've had to take a copy of it, and rename the copy to get round the restriction on the forum)

Also, I'm not sure if the change to loading the option driver will work. Even though the driver is loaded, I don't think it's loading properly (maybe? bare in mind I am still a newbie about some of these things). Because I still have to unload it first (modprobe -r).

<Added> The modeswitch rule doesn't seem to trigger even if I remove and reinsert the modem stick.

---

### Post by alexfish on 2011-04-27
hi appls for late reply 

have been looking through the post to see what may be different  , other posts (same device) indicate that option driver is loading and registering on the bus , this device  on this system is not registering on bus side

yet after removal and reloading of the option driver , the registering of the bus side does occur

long and short need more info , let the device settle after (manually modeswitching)

can post results of this command from the terminal
```
ls /sys/module/option/drivers/usb-serial:*/new_id
```then will look further as regards the modeswitching rules (for automating the modeswitching)

Added: for the modeswitching can post the results of
```
ls -al /usr/sbin/usb_modeswitch*
```


regards

alexfish

---

### Post by holmez on 2011-05-08
> **alexfish said:**
> hi appls for late reply 

have been looking through the post to see what may be different  , other posts (same device) indicate that option driver is loading and registering on the bus , this device  on this system is not registering on bus side

yet after removal and reloading of the option driver , the registering of the bus side does occur

long and short need more info , let the device settle after (manually modeswitching)

can post results of this command from the terminal
```
ls /sys/module/option/drivers/usb-serial:*/new_id
```then will look further as regards the modeswitching rules (for automating the modeswitching)

Added: for the modeswitching can post the results of
```
ls -al /usr/sbin/usb_modeswitch*
```
regards

alexfish

Hello alexfish. No worries about the late reply.

The terminal results are:

```

david@holmez:~$ ls /sys/module/option/drivers/usb-serial:*/new_id
/sys/module/option/drivers/usb-serial:option1/new_id
david@holmez:~$ ls -al /usr/sbin/usb_modeswitch*
-rwxr-xr-x 1 root root 35056 2010-11-11 15:10 /usr/sbin/usb_modeswitch
-rwxr-xr-x 1 root root 20394 2010-11-11 15:10 /usr/sbin/usb_modeswitch_dispatcher
david@holmez:~$ 

```

I hope this helps.

David

---

