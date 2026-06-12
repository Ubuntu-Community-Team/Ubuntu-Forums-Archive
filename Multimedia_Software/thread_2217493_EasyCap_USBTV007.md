---
title: "EasyCap USBTV007"
date: 2014-04-17
forum: Multimedia Software
---

### Post by suomalainen on 2014-04-17
Ubunteros!

I recently purchased an EasyCap USBTV007, of which there are four variants. This item takes your video stream via RCA and converts it to USB so you can record/view video streams on your PC/laptop. That said, the model I have was identified through this resource:

[http://www.linuxtv.org/wiki/index.php/Easycap](http://www.linuxtv.org/wiki/index.php/Easycap)

I use Ubuntu 12.04LTS PAE with Mate desktop. The kernel version is:

```
myname@myname:~$ uname -r
3.5.0-48-generic
```

When I run lsusb with the USBTV007 in place I get:

```
myname@myname:~$ lsusb
Bus 001 Device 002: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 006: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 006 Device 005: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 007 Device 002: ID 04d9:1400 Holtek Semiconductor, Inc. PS/2 keyboard + mouse controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c527 Logitech, Inc. 
myname@myname:~$
```

FYI- when the USBTV007 is inserted it does burn green.

The above suggests to me that I need a driver for the EasyCap USBTV007 to become recognized. Thus, I did a search for drivers and found this resource @:

[https://github.com/mwelchuk/usbtv](https://github.com/mwelchuk/usbtv)

This is a backported driver for the Fushicai USBTV007 Video Grabber, sold as one of the "EasyCAP" USB devices.

The initial code copied from v3.14-rc5-232-gb053940 and backported to the 3.2 kernel (as used in Ubuntu 12.04 LTS, which was the purpose for this backporting exercise).

Installation
------------

The driver can be built and installed using DKMS. The following commands can be used to install dkms, build and install the driver. Installing the module this way should cause the driver to be rebuilt and installed automatically when the kernel is updated.

Extract these sources into "/usr/src/usbtv-1.0". Run the follwoing commands:

```
$ sudo -i
# apt-get install dkms
# dkms add -m usbtv -v 1.0
# dkms build -m usbtv -v 1.0
# dkms install -m usbtv -v 1.0
# chkconfig dkms_autoinstaller on
```



What I'd like to know is this:

1. Would this backport be compatible with my kernel version?
2. Do I need an account to download from Github?'
3. When you look this github page there are 6 files. As I understand, I can download them to desktop but they must be extraced into the folder at /usr/src/usbtv-1.0.
4. I assume I need to create the directory "usbtv-1.0?
5. Is the code to make directory mkd /usr/src/usbtv-1.0?

I hope this is enough information for advice but if not just let me know.

Thank you!

---

### Post by suomalainen on 2014-04-21
I ran the code dmesg and received the following output from terminal:

```
[ 7536.350945] usb 8-1: New USB device found, idVendor=1b71, idProduct=3002
[ 7536.350952] usb 8-1: New USB device strings: Mfr=3, Product=4, SerialNumber=2
[ 7536.350957] usb 8-1: Product: usbtv007
[ 7536.350961] usb 8-1: Manufacturer: fushicai
[ 7536.350965] usb 8-1: SerialNumber: 300000000002
[ 7544.573743] usb 6-3: USB disconnect, device number 4
[ 7547.260046] usb 6-3: new low-speed USB device number 5 using ohci_hcd
[ 7547.469677] usb 6-3: New USB device found, idVendor=04d9, idProduct=1400
[ 7547.469686] usb 6-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 7547.484593] input: HID 04d9:1400 as /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/0000:03:00.0/usb6/6-3/6-3:1.0/input/input10
[ 7547.485058] hid-generic 0003:04D9:1400.0005: input,hidraw2: USB HID v1.10 Keyboard [HID 04d9:1400] on usb-0000:03:00.0-3/input0
[ 7547.503776] input: HID 04d9:1400 as /devices/pci0000:00/0000:00:1e.0/0000:02:01.0/0000:03:00.0/usb6/6-3/6-3:1.1/input/input11
[ 7547.504301] hid-generic 0003:04D9:1400.0006: input,hidraw3: USB HID v1.10 Mouse [HID 04d9:1400] on usb-0000:03:00.0-3/input1

```

Can someone tell me what the above means.

Thanks!

---

### Post by dannyboy79 on 2014-04-30
is there a device node within your /dev/ folder called video0? if you have /dev/video0 you can see if you get video from it by issuing something like this
```
cat /dev/video0 > video.ts
``` after a short time just hit ctrl+c to cancel the command, then you can see if it worked by playing the video file with vlc or your favorite video player.

I have an HD-PVR from Haugpauge that I use to capture my xbox 360 using the same command as above. good luck

---

### Post by suomalainen on 2014-05-01
The EasyCap USBTV007 does not create a "video0" file when it is plugged in via usb. A web cam on the other hand does create this file when plugged into usb.

---

### Post by suomalainen on 2014-05-01
Mission accomplished! I got my video working.

The solution is rather simple.

1. Go to the Github link above
2. Download the zip file into the directory as per instructions
3. Extract the zip file
4. Now run the terminal commands.

---

### Post by Dhinesh_Ramotharan on 2015-04-12
Good day..

I would like to ask, as i follow the below coding :

$ sudo -i
# apt-get install dkms
# dkms add -m usbtv -v 1.0
# dkms build -m usbtv -v 1.0
# dkms install -m usbtv -v 1.0
# chkconfig dkms_autoinstaller on

the "chconfig" is code is error..how to troubleshoot it..

---

