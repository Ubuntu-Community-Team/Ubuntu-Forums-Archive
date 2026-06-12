---
title: "Huawei k3771"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by uncleBez on 2011-08-16
3g usb stick from vodafone australia not connecting. not recognised by network manager.
MODEL K3771
UBUNTU 10.04 LTS

unmounted by right clicking and 'safely removing' device, network manager still doesn't see it.

installed usb_modeswitch was from repository and restarted, key still mounts as cdrom, and after safely removing network manager doesn't see it.

purged usb_modeswitch and installed
Sakis3G
 $./sakis3g --interactive 
choose connect > usb > select my vodafone device..
connection fails.

upgrading to 10.10 made no difference.. 
attempting upgrade to 11.04

$ lsusb
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 12d1:14c4 Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


currently running upgrade to ubuntu 10.10.. see what happens.

anyone else have experience with this device?

---

### Post by alexfish on 2011-08-16
Hi
can visit

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

check the listing in the device_reference.text 

update the usb_modeswitch.d folder. also check the usb_modeswitch rules

as detailed **Natty,known bugs,and fixes** Post   			#[**30**]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")

Start from .**If the device is not switching: **

alexfish

---

### Post by pdc on 2011-08-16
the companies continually issue new variants;

I see from this 

[http://article.gmane.org/gmane.linux.kernel/1179341](http://article.gmane.org/gmane.linux.kernel/1179341)

> Andrew Bird (4):
      USB: option driver: add PID for Vodafone-Huawei K3770
      USB: option driver: add PID for Vodafone-Huawei K3771
      USB: option driver: add PID for Vodafone-Huawei K4510
      USB: option driver: add PID for Vodafone-Huawei K4511

that it will be written into the 3.1 kernel; but that is months (2-4) away

seems the ID when switched should be

> 12d1:14ca Huawei Technologies Co., Ltd. 

this is from here

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4935&sid=c31db942411c5c644e603db55b05bce8](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=4935&sid=c31db942411c5c644e603db55b05bce8)

all I can suggest is installing the latest usb_modeswitch; and its data package from here

[http://packages.debian.org/sid/usb-modeswitch-data](http://packages.debian.org/sid/usb-modeswitch-data)      data package

and here

[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch) for the programme

.......choose the appropriate version for your processor at the bottom of the page

---

### Post by pdc on 2011-08-16
so this device has been investigated recently

> +# Vodafone (Huawei) K3771

+ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14c4", RUN+="usb_modeswitch '%b/%k'"

this is from here

[https://github.com/andrewbird/usb-modeswitch-data/commit/b3a793ef9091eab1043253903debe422c43e4c70](https://github.com/andrewbird/usb-modeswitch-data/commit/b3a793ef9091eab1043253903debe422c43e4c70)

so one could add this I think to an existing usb_modeswitch by 

> sudo gedit /etc/udev/rules.d/K3771.rules
 

you will be asked for your sudo password; enter it; hit the ENTER key;

that will open up gedit, a text editor, and an empty file

if you copy and paste the above into it

ie 

> +# Vodafone (Huawei) K3771

+ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14c4", RUN+="usb_modeswitch '%b/%k'"

and **SAVE** and **CLOSE**

if you reboot, we would hope the ID for the Huawei would now be

> 12d1:14ca

---

### Post by almightyolive on 2011-09-15
Thanks to everyone who posted in this thread. All the guides helped me, including the link to Git Hub.

I have written a guide on my website that goes through the process of adding a new device to usb_modeswitch that hopefully can be used for ANY new device (as long as you know the target product idea). The detailed guide can be accessed at [https://sites.google.com/site/thealmightyolive/testimonials-1/troubleshootingusbmobileinternetubuntu](https://sites.google.com/site/thealmightyolive/testimonials-1/troubleshootingusbmobileinternetubuntu)

A quick and dirty version (this does not go through WHY we are doing the steps, only what to do. If you want to understand the thought processes look to the guide on my site):

[LIST=1]
[*]The ID of a device can be  split into two parts; the first part (12d1) is the vendor code, and the  second part (14c4) is the product code. We need  to manually tell the system to switch over to the mobile broadband part  (this is what the installer does automatically for Windows and Mac). To  do this we run the following command:
```
sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
``` Either add to the end of the file or do a search to find  similar devices and add:
```
# Vodafone (Huawei) K3771 (edit the following to your devices id)
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14c4", RUN+="usb_modeswitch '%b/%k'
```[SIZE=1][FONT=courier new]"[/FONT][/SIZE]
[*]The mobile broadband device has it's own  product id that we must link to the installer product id. This is where it gets  tricky; you need to figure out what this id is and at this stage I have  no other advice other than to Google and pray. Luckily for me I know  that my device id is 12d1:14ca. Now we need to create a custom  usb_modeswitch rule.....

Navigate to the directory **/usr/share/usb_modeswitch/** by running the following command in a terminal:
```
cd /usr/share/usb_modeswitch/
```If you perform an **ls** you will see that this directory contains a  file called configPack.tar.gz. This file contains all the switching  rules; we need to edit it to add our device. First back up the file  through:
```
sudo cp configPack.tar.gz configPack-ORIGINAL.tar.gz
```Now we will extract the scripts through running:
```
sudo mkdir configPack/; sudo tar xzf configPack.tar.gz -C configPack/
```Run the command to open a text file for our new rule (replace the 12d1:14c4 part with the id of your device):
```
sudo gedit configPack/12d1\:14c4 

```This will open a completely blank document. Add the following text (remember to customise for your particular device!):
```
########################################################
# Vodafone (Huawei) K3771 (again, this is just a comment)
#
# Our settings discovered by lsusb (the '0x' part just
# tells the system how to interpret the number
DefaultVendor= 0x12d1
DefaultProduct=0x14c4
#
# Our target product that we will switch to
TargetVendor=  0x12d1
TargetProduct= 0x14ca
#
# Some misc values that I don't really understand and am
# not game enough to change...
CheckSuccess=20
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
```Now we need to repack the rules and clean up our mess:
```
cd configPack/; sudo tar -czf ../configPack.tar.gz *; cd ../; sudo rm -rf configPack/
```You can check the contents of the file by running the following command:
```
sudo file-roller configPack.tar.gz

```
[*][SIZE=1][FONT=courier new][SIZE=2][FONT=arial]Now restart[/FONT][FONT=arial] your machine and, fingers crossed, the system will now correctly detect your device![/FONT][/SIZE][/FONT][/SIZE]
[/LIST]

---

### Post by kareempharmacist on 2011-10-14
vodafone k3770 usb stick works perfectly and out-of-the-box on ubuntu 11.10 .....tried..all u have to do is to upgrade.
it works also on debian and any debian-based distribution.
may this one work too

---

