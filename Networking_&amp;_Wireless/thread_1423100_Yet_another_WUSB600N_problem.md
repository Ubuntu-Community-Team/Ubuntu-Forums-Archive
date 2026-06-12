---
title: "Yet another WUSB600N problem"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by TheConsaw on 2010-03-06
hi guys, sorry for yet another n00b thread on the infamous wusb600n, i have tried to follow other threads instructions but i get lost, novice here

so i have downloaded the RT3572 driver from railink and put it in my home folder
executed the following then: ```
bunzip2 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar.bz2
```
```
tar -xvf 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar
```
no problems here

 I have modified the 2 files as instructed:
 > 4) add the device and vendor id "{USB_DEVICE(0x1737,0x0079)}" between the "#ifdef RT35xx" and "#endif // RT35xx //" in the file "common/rtusb_dev_id.c"
5) modify the "os/linux/config.mk" like I described in my previous message
no problems here

next step according to all instructions :
sudo make and
sudo make install, trips me up, i get "no targets specified and no makefile found"

probably a basic mistake somewhere here, but my knowledge of the command line is zilch

thanks in advance  :KS

---

### Post by chili555 on 2010-03-06
Are you in the same directory as the Makefile? After you extracted the tar.bz2, and it created a directory, did you change directories to that folder?```
cd 2009_1222_RT3572_LinuxSTA_V2.3.0.0
```And if you list the contents of the directory:```
ls
```Do you see Makefile as one of the items? If so, please continue with sudo make, etc.

---

### Post by chili555 on 2010-03-06
By the way, when you run:```
lsusb
```Is the usb.id of your device actually (1737:0079)?> add the device and vendor id "{USB_DEVICE(0x[COLOR="Blue"]1737[/COLOR],0x[COLOR="Blue"]0079[/COLOR])}"I have seen (1737:0071) for this device, but not 0079.

Please check before you go to a lot of trouble for a less than satisfactory result. Moreover, if there is another device out there, we wireless geeks would be interested to know.

---

### Post by TheConsaw on 2010-03-06
thanks for your reply chili,
I was able make install with your instructions :p
and you were right about > I have seen (1737:0071) for this device, but not 0079.
so i changed that also, thanks

my problem still persists tho, I can see my network but cant connect, i used to be able connect out of the box in 9.04, currently i cant on 9.10 or 10.04a2

any other ideas, thanks a lot
appreciated

i'm on acer aspire x3200 desktop
my laptop works no problems, everything out of the box !

---

### Post by chili555 on 2010-03-06
So you verified the usb.id? If you have (1737:0071), then your solution might be here:  [http://ubuntuforums.org/showthread.php?t=1420984](http://ubuntuforums.org/showthread.php?t=1420984)

See post #4 and 5.

---

### Post by TheConsaw on 2010-03-06
hi, output is ??

```
bobby@bobby-desktop-ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1737:0071 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bobby@bobby-desktop-ubuntu:~$ dmesg | grep rt2
[    9.888072] Registered led device: rt2800usb-phy0::radio
[    9.888095] Registered led device: rt2800usb-phy0::assoc
[    9.888108] Registered led device: rt2800usb-phy0::quality
[    9.888615] usbcore: registered new interface driver rt2800usb
[    9.893035] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.897855] usbcore: registered new interface driver rt2870
[   10.168644] Error: Driver 'rt2870' is already registered, aborting...
[   10.168695] usbcore: error -16 registering interface 	driver rt2870
[   10.177064] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
[   10.196758] Error: Driver 'rt2870' is already registered, aborting...
[   10.196809] usbcore: error -16 registering interface 	driver rt2870
bobby@bobby-desktop-ubuntu:~$ 


```it might as well be written in Chinese to me !!

---

### Post by chili555 on 2010-03-06
It verifies that* both *rt2800usb *and* rt2870sta are loading. The only thing worse than no driver is two conflicting drivers fighting each other. Even better, for you, it means you don't have to compile a driver, the correct driver is already there!

Let's try to fix it:```
sudo gedit /etc/modprobe.d/blacklist.conf

```
Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot. Is your wireless working?

---

### Post by TheConsaw on 2010-03-06
Mate you are an absolute legend
that worked,

thanks so much !!!

will mark solved !!

---

### Post by fubofo on 2011-04-24
Hey, I still cannot seem to get this damned adaptor working!

I too have been through all sorts of threads and instructions.
I am now at the stage where I have the adaptor installed (using RaLink 2.5.0.0 on Ubuntu 10.10 x86) and it will detect my wireless networks but just will not connect to anything at all, regardless of security preference.

```
kaipee@kaipee-ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a4:2000 Ortek Technology, Inc. WKB-2000 Wireless Keyboard with Touchpad
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 001 Device 006: ID 172f:0500 Waltop International Corp. 
Bus 001 Device 005: ID 1737:0079 Linksys WUSB600N Wireless-N USB Network Adapter with Dual-Band ver. 2
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 18e3:9102 Fitipower Integrated Technology Inc Multi car reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kaipee@kaipee-ubuntu:~$ dmesg | grep rt2
[    5.185241] rtusb init rt2870 --->
[    5.186083] usbcore: registered new interface driver rt2870
[   10.652096] <==== rt28xx_init, Status=0
[   11.655717] <==== rt28xx_init, Status=0
kaipee@kaipee-ubuntu:~$ 

```

Can anyone give me some help on this?
I'm currently accessing internet by using USB tethering through my Android device.

---

### Post by fubofo on 2011-04-24
Forget it.
I managed to get it working myself now.

Turns out there is a serious problem the drivers after v2.3.0.0 in Ubuntu. For some reason the only thing that will work is v2.3.0.0

So here goes for anybody else who is having major issues with WUSB600N v2 in Ubuntu:

**Install WUSB600N v2**

```
1) download the RT3572 module source from " http://download.modem-help.co.uk/mfcs-R/Ralink/Reference-Designs/RT3000UD/Drivers/Linux-k2-4/v2-3-0-0/2009-1222-RT3572-LinuxSTA-V2-1-.3.0.0.tar.bz2.php?showFile= " or " http://www.megaupload.com/?d=E90M6K3F "
(filename: 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar.bz2)
2) execute the command "bunzip2 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar.bz2"
3) execute the command "tar -xvf 2009_1222_RT3572_LinuxSTA_V2.3.0.0.tar"
4) add the device and vendor id "{USB_DEVICE(0x1737,0x0079)}" between the "#ifdef RT35xx" and "#endif // RT35xx //" in the file "common/rtusb_dev_id.c"
5) modify the "os/linux/config.mk" like I described in my previous message
6) execute the command "sudo make"
7) execute the command "sudo make install"
8) execute the command "sudo modprobe rt3572sta"

Keep the directory safe somewhere, you will need it to perform make install when you update Ubuntu kernel
```

**Load WUSB600N v2 at boot**

```
sudo gedit /etc/modules

add

rt3572sta
alias ra0 rt3572sta
```

**Update WUSB600N v2 with new kernel**

```
cd to RaLink v2.3.0.0 directory (for me this is ~/build)

sudo su
make clean
make 
make install
modprobe rt3572sta
```

NOTE: for some reason it still disconnects randomly, unplugging and re-inserting it should be fine

---

