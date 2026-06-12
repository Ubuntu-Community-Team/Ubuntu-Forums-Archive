---
title: "AF9035 USB DVB-T Karmic 64bit install problem"
date: 2009-12-25
forum: Multimedia Software
---

### Post by baldrick222 on 2009-12-25
I am hoping some one is able to help me to get a AF9035 USB DVB-T working in Karmic 64bit on a Asrock Ion330

I have spent a month attempting this following the instructions provided in the files sent to me by the device manuf and then the chip manuf , and then many instructions scattered around , but none of them have produced any joy.

files I have recieved are available here - including I think source from the chip manuf

[http://www.linux-cam.com/downloads/MiniTV_For_Linux.rar](http://www.linux-cam.com/downloads/MiniTV_For_Linux.rar)

[http://www.linux-cam.com/downloads/9035.linux.PC.dvb-tV9.07.10.1.zip](http://www.linux-cam.com/downloads/9035.linux.PC.dvb-tV9.07.10.1.zip)

a photo of the internals is here showing the 9035B chip and the FC011

[http://www.linux-cam.com/downloads/EzTV_USB_DVB-T_internals_3243.jpg](http://www.linux-cam.com/downloads/EzTV_USB_DVB-T_internals_3243.jpg)


I have followed tutorials instructing me to install and compile mecurial , v4l , gcc , linux-headers dvb-apps , but still do not get any success.

I have seen some mention saying that the problem is the device being recognised as a USB HID v1.01 Keyboard and that the loading of the module for this in modprobe needs to be disabled via a quirk command , but I have not tried this yet as I am not sure I understand exactly what is required to be done.

lsusb output

> 
mumarae@mumarae-desktop:~$ lsusb
Bus 002 Device 010: ID 0a5c:2100 Broadcom Corp. Bluetooth 2.0+eDR dongle
Bus 002 Device 009: ID 0ac8:301b Z-Star Microelectronics Corp. ZC0301 Webcam
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp.
Bus 002 Device 003: ID 045e:00cb Microsoft Corp.
Bus 002 Device 002: ID 045e:0750 Microsoft Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 15a4:1001
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mumarae@mumarae-desktop:~$
dmesg 

> 
[ 1040.200042] usb 1-4: new high speed USB device using ehci_hcd and address 7
[ 1040.357187] usb 1-4: configuration #1 chosen from 1 choice
[ 1040.362195] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:04.1/usb1/1-4/1-4:1.1/input/input6
[ 1040.362393] generic-usb 0003:15A4:1001.0004: input,hidraw3: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:04.1-4/input1

when following the instructions from the readme/user guide in the MiniTV_For_linux.rar the output is as follows

> 
mumarae@mumarae-desktop:~$ cd v9.08.14.1/
mumarae@mumarae-desktop:~/v9.08.14.1$ ls
EZTV Linux TV User Guide.doc  ITE-Linux-AF903x-v9.08.14.1.sh  ReadMe.txt
mumarae@mumarae-desktop:~/v9.08.14.1$ sudo sh ITE-Linux-AF903x-v9.08.14.1.sh
[sudo] password for mumarae:
ITE-Linux-AF903x-v9.08.14.1.sh: 21: [[: not found
ITE-Linux-AF903x-v9.08.14.1.sh: 30: [[: not found
ITE-Linux-AF903x-v9.08.14.1.sh: 38: [[: not found
1. Install ITEtech AF9035 Driver
2. Remove  ITEtech AF9035 Driver
Please Input Your Choise:
1
Please wait a minute
cp: cannot stat `api/.*.o.cmd': No such file or directory
make -C /lib/modules/2.6.31-17-generic/build SUBDIRS=/tmp/ite-install/installer/AF903x_SRC modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /tmp/ite-install/installer/AF903x_SRC/af903x-core.o
In file included from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/af903x.h:15:21: error: dvb-usb.h: No such file or directory
In file included from /tmp/ite-install/installer/AF903x_SRC/type.h:4,
                 from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/userdef.h:11:1: warning: "NULL" redefined
In file included from include/linux/kernel.h:12,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:6,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
include/linux/stddef.h:10:1: warning: this is the location of the previous definition
In file included from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/type.h:6:1: warning: "IN" redefined
In file included from /tmp/ite-install/installer/AF903x_SRC/type.h:4,
                 from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/userdef.h:21:1: warning: this is the location of the previous definition
In file included from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/type.h:7:1: warning: "OUT" redefined
In file included from /tmp/ite-install/installer/AF903x_SRC/type.h:4,
                 from /tmp/ite-install/installer/AF903x_SRC/demodulator.h:5,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x.h:17,
                 from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/userdef.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/ite-install/installer/AF903x_SRC/af903x-core.c:1:
/tmp/ite-install/installer/AF903x_SRC/af903x.h:201: error: array type has incomplete element type
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:5: warning: data definition has no type or storage class
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:5: warning: type defaults to âintâ in declaration of âDVB_DEFINE_MOD_OPT_ADAPTER_NRâ
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:5: warning: parameter names (without types) in function declaration
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c: In function âaf903x_probeâ:
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:34: error: implicit declaration of function âdvb_usb_device_initâ
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:34: error: âadapter_nrâ undeclared (first use in this function)
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:34: error: (Each undeclared identifier is reported only once
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:34: error: for each function it appears in.)
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c: In function âaf903x_suspendâ:
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:51: warning: passing argument 2 of âDL_CheckTunerInitedâ from incompatible pointer type
/tmp/ite-install/installer/AF903x_SRC/af903x.h:218: note: expected âenum Bool *â but argument is of type âbool *â
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:52: warning: passing argument 2 of âDL_CheckTunerInitedâ from incompatible pointer type
/tmp/ite-install/installer/AF903x_SRC/af903x.h:218: note: expected âenum Bool *â but argument is of type âbool *â
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c: At top level:
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:94: error: âdvb_usb_device_exitâ undeclared here (not in a function)
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c: In function âaf903x_module_initâ:
/tmp/ite-install/installer/AF903x_SRC/af903x-core.c:104: error: implicit declaration of function âinfoâ
make[2]: *** [/tmp/ite-install/installer/AF903x_SRC/af903x-core.o] Error 1
make[1]: *** [_module_/tmp/ite-install/installer/AF903x_SRC] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [default] Error 2
make error
mumarae@mumarae-desktop:~/v9.08.14.1$
the result of following the directions in the 9035.linux.PC.dvb-tV9.07.10.1.zip files


> 
[EMAIL="mumarae@mumarae-desktop:%7E/9035.linux.PC.dvb"]mumarae@mumarae-desktop:~/9035.linux.PC.dvb[/EMAIL]-tV9.07.10.1/64bit/AF903x_SRC$ sudo make clean
[EMAIL="mumarae@mumarae-desktop:%7E/9035.linux.PC.dvb"]mumarae@mumarae-desktop:~/9035.linux.PC.dvb[/EMAIL]-tV9.07.10.1/64bit/AF903x_SRC$ sudo make
cp: cannot stat `api/.*.o.cmd': No such file or directory
make -C /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.o
In file included from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:1:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:15:21: error: dvb-usb.h: No such file or directory
In file included from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/type.h:4,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/demodulator.h:5,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:17,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:1:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/userdef.h:11:1: warning: "NULL" redefined
In file included from include/linux/kernel.h:12,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:6,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:1:
include/linux/stddef.h:10:1: warning: this is the location of the previous definition
In file included from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/demodulator.h:5,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:17,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:1:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/type.h:6:1: warning: "IN" redefined
In file included from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/type.h:4,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/demodulator.h:5,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:17,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:1:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/userdef.h:21:1: warning: this is the location of the previous definition
In file included from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/demodulator.h:5,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:17,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:1:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/type.h:7:1: warning: "OUT" redefined
In file included from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/type.h:4,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/demodulator.h:5,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:17,
                 from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:1:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/userdef.h:22:1: warning: this is the location of the previous definition
In file included from /home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:1:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:201: error: array type has incomplete element type
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:5: warning: data definition has no type or storage class
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:5: warning: type defaults to âintâ in declaration of âDVB_DEFINE_MOD_OPT_ADAPTER_NRâ
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:5: warning: parameter names (without types) in function declaration
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c: In function âaf903x_probeâ:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:34: error: implicit declaration of function âdvb_usb_device_initâ
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:34: error: âadapter_nrâ undeclared (first use in this function)
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:34: error: (Each undeclared identifier is reported only once
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:34: error: for each function it appears in.)
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c: In function âaf903x_suspendâ:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:51: warning: passing argument 2 of âDL_CheckTunerInitedâ from incompatible pointer type
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:218: note: expected âenum Bool *â but argument is of type âbool *â
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:52: warning: passing argument 2 of âDL_CheckTunerInitedâ from incompatible pointer type
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x.h:218: note: expected âenum Bool *â but argument is of type âbool *â
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c: At top level:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:94: error: âdvb_usb_device_exitâ undeclared here (not in a function)
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c: In function âaf903x_module_initâ:
/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.c:104: error: implicit declaration of function âinfoâ
make[2]: *** [/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC/af903x-core.o] Error 1
make[1]: *** [_module_/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [default] Error 2
[EMAIL="mumarae@mumarae-desktop:%7E/9035.linux.PC.dvb"]mumarae@mumarae-desktop:~/9035.linux.PC.dvb[/EMAIL]-tV9.07.10.1/64bit/AF903x_SRC$ sudo make install
make[1]: Entering directory `/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC'
echo -e "\nRemoving old /lib/modules/2.6.31-17-generic/kernel/drivers/media/dvb/dvb-usb/ files:"
-e
Removing old /lib/modules/2.6.31-17-generic/kernel/drivers/media/dvb/dvb-usb/ files:


make[1]: Leaving directory `/home/mumarae/9035.linux.PC.dvb-tV9.07.10.1/64bit/AF903x_SRC'

/sbin/depmod -a
af35irtbl.bin
[EMAIL="mumarae@mumarae-desktop:%7E/9035.linux.PC.dvb"]mumarae@mumarae-desktop:~/9035.linux.PC.dvb[/EMAIL]-tV9.07.10.1/64bit/AF903x_SRC$


any assistance would be appreciated - thanks

---

### Post by jimmers on 2009-12-26
[B]
Greetings
[/B] 			 			 		   		 		 		I had problems running a usb dvb t on Jaunty, it is an  AVerTv Digi Volar X, after searching many forums,, I found the following, so  I opened a Terminal and  typed:

sudo apt-get install dvbscan
sudo apt-get install w-scan

I then opened  Kaffeine selected channels - scan, and it got me 40 TV Stations and 26 radio.
It may not  work for you, but its worth a try at least.

jimmers

---

### Post by Fitzcarraldo on 2009-12-26
*baldrick222*, I too have the same device as you. Well, at least it is from the same manufacturer and has the same driver as the one you posted. I bought it a couple of days ago. Mine in an ezcap USB 2.0 DVB-T Stick model number EZTV860, manufactured November 2009. The manufacturer is a Chinese company named Forward Video Co. Ltd. Their Web site is [http://www.szforwardvideo.com/](http://www.szforwardvideo.com/) and the e-mail for support is **support at szforwardvideo dot com**.

The CD that came with the device has the same folder as the one that you attached to you post, namely v9.08.14.1, which contains a Bash script to install the driver. Interestingly, the Bash script has a binary tarball incorporated into it (non-ASCII in a section following the ASCII Bash commands): when you run the script it parses itself, strips out the binary part to create a temporary tarball, extracts the contents and issues a make command to compile the driver. I suppose the manufacturer has done it this way to make it difficult for the user to get his hands on the source code. The installation script failed when I ran it.

To investigate what was happening I hacked the installation script. I worked out how to extract from it the binary part and convert it to a tarball, from which I could then extract the driver source code and makefiles. From these I discovered that the latest version of the driver (written in August 2009) is only written for Linux kernels up to 2.6.29. I hacked the make scripts and added instructions for the 2.6.30 and 2.6.31 kernels, but it still will not build. I have therefore sent an e-mail to the Forward Video support team. I'm not holding my breath, though.

Regarding the problem of the usbhid driver recognising the DVB-T stick as a keyboard, you need to stop the usbhid driver from doing this as follows:

If the usbhid driver is a kernel module (CONFIG_USB_HID=m in the kernel config) then the way to tell the usbhid driver to ignore this specific device, as it has its own driver, would be to pass an option to the usbhid driver by putting the following line in the file /etc/modprobe.d/usbhid.conf (create the file if it does not already exist):

```
options usbhid quirks=0x15a4:0x1001:0x0004
```


where 0x15a4 is the Vendor ID and 0x1001 is the Product ID, both obtained by looking at the output of either the dmesg or lsusb commands, and the 0x0004 flag is HID_QUIRK_IGNORE, which tells the usbhid driver to ignore the device.

However, if the usbhid driver is not a module but is instead built into the kernel (CONFIG_USB_HID=y in the kernel config), the way to tell the usbhid driver to ignore this specific device, as it has its own driver, would be to pass the option to the usbhid as a boot parameter, by editing /boot/grub/menu.lst (grub.conf) and adding the following boot parameter to the end of the kernel boot line:

```
usbhid.quirks=0x15a4:0x1001:0x0004
```


Then when I reboot I see the following for the DVB-T stick in the dmesg output:

```
[  196.322403] usb 1-1.4: new high speed USB device using ehci_hcd and address 13
    [  196.414896] usb 1-1.4: New USB device found, idVendor=15a4, idProduct=1001
    [  196.414903] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
    [  196.414909] usb 1-1.4: Product: AF9035A USB Device
    [  196.414913] usb 1-1.4: Manufacturer: Afa Technologies Inc.
    [  196.414917] usb 1-1.4: SerialNumber: AF0102020700001
    [  196.415183] usb 1-1.4: configuration #1 chosen from 1 choice
```


Compare the new dmesg output above with the old dmesg output below. You can see that the usbhid driver now ignores the DVB-T stick and it is no longer listed as a keyboard.

```
[  824.424054] usb 1-4: new high speed USB device using ehci_hcd and address 4
[  824.544491] usb 1-4: New USB device found, idVendor=15a4, idProduct=1001
[  824.544494] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  824.544496] usb 1-4: Product: AF9035A USB Device
[  824.544498] usb 1-4: Manufacturer: Afa Technologies Inc.
[  824.544500] usb 1-4: SerialNumber: AF0102020700001
[  824.544644] usb 1-4: configuration #1 chosen from 1 choice
[  824.548975] input: Afa Technologies Inc. AF9035A USB Device as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.1/input/input9
[  824.549123] generic-usb 0003:15A4:1001.0001: input,hidraw0: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:1d.7-4/input1
```

Now, if only we could compile the driver!

---

### Post by Fitzcarraldo on 2009-12-26
OK, I did some more hacking and got the driver to install in Sabayon Linux, but it still does not work.

Here's what I did:

1. Edited v9.08.14.1/installer/AF903x_SRC/Makefile and changed "lib" to "lib64" in the path of the environment variables KDIR, KDIR26 and DEST.

2. Edited v9.08.14.1/installer/AF903x_SRC/Makefile and added:

```
ifneq (,$(findstring 2.6.30,$(CURRENT)))
        @cp -f v4l/kernel-2.6.30/* ./   
endif                                   
ifneq (,$(findstring 2.6.31,$(CURRENT)))
        @cp -f v4l/kernel-2.6.31/* ./   
endif                                   
ifneq (,$(findstring 2.6.32,$(CURRENT)))
        @cp -f v4l/kernel-2.6.32/* ./   
endif
```
after
```
ifneq (,$(findstring 2.6.29,$(CURRENT)))
        @cp -f v4l/kernel-2.6.29/* ./   
endif 
```

3. Repeated Steps 1 and 2 on v9.08.14.1/installer/AF903x_SRC/Makefile.release

4. Copied v9.08.14.1/installer/AF903x_SRC/v4l/kernel-2.6.29/ and its contents to create new directories v9.08.14.1/installer/AF903x_SRC/v4l/kernel-2.6.30/, v9.08.14.1/installer/AF903x_SRC/v4l/kernel-2.6.31/ and v9.08.14.1/installer/AF903x_SRC/v4l/kernel-2.6.32/

5. Edited /usr/src/linux/include/linux/firmware.h and added the line:

```
#define FIRMWARE_NAME_MAX 30
```
before the line:
```
#define FW_ACTION_NOHOTPLUG 0
```

6. Edited v9.08.14.1/installer/AF903x_SRC/api/driver_tua9001.c and commented out (added "//" in front of) the lines:

```
//#elif defined(CRYSTAL_19.2_MHZ)   /*  Frequency 19.2 MHz */
//  i2cseq[0] = 0x01;
//  i2cseq[1] = 0xA0;
//  i2cBusWrite (TUNERs_TUA9001_DEVADDR, 0x1d, i2cseq, 2);
//  /* Note: Insert optimised register values for 0x40 / 0x41 for used crystal */
//  /* contact application support for further information */
//#elif defined(CRYSTAL_20.48_MHZ)   /*  Frequency 20,48 MHz */
//  i2cseq[0] = 0x01;
//  i2cseq[1] = 0xA8;
//  i2cBusWrite (TUNERs_TUA9001_DEVADDR, 0x1d, i2cseq, 2);
//  /* Note: Insert optimised register values for 0x40 / 0x41 for used crystal */
//  /* contact application support for further information */
```

7. Ran the installer script as root user:
```
cd /home/fitzcarraldo/Desktop/v9.08.14.1/installer
sh installer.sh
```
It runs to completion.

The module is now loaded if I plug the device in:

```
lsmod | grep dvb
dvb_usb_af903x       1088768  0
dvb_usb                14096  1 dvb_usb_af903x
dvb_core               88246  1 dvb_usb
i2c_core               21012  6 dvb_usb,radeon,drm,i2c_algo_bit,videodev,i2c_i801
```
but dmesg shows a problem of some kind with the loading of the module:
```
[  156.413401] usb 1-1.4: new high speed USB device using ehci_hcd and address 12
[  156.505885] usb 1-1.4: New USB device found, idVendor=15a4, idProduct=1001
[  156.505892] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  156.505898] usb 1-1.4: Product: AF9035A USB Device
[  156.505902] usb 1-1.4: Manufacturer: Afa Technologies Inc.
[  156.505906] usb 1-1.4: SerialNumber: AF0102020700001
[  156.506812] usb 1-1.4: configuration #1 chosen from 1 choice
[  156.507416]         DRIVER_RELEASE_VERSION : v9.08.14.1
[  156.507421]         FW_RELEASE_VERSION     : v8_8_63_0
[  156.507425]         API_RELEASE_VERSION    : 200.20090402.0
[  156.920879] [Device_init] Error 1
[  156.920914] dvb_usb_af903x: probe of 1-1.4:1.0 failed with error -12
```

---

### Post by baldrick222 on 2009-12-27
thanks for sharing your effort Fitzcarraldo

I created the usbhid.conf file but I am not seeing a change in dmesg yet - do I have to chmod the file ?

```

grep USB_HID /boot/config-2.6.31-17-generic

```gave me

```

CONFIG_USB_HID=m
CONFIG_USB_HIDDEV=y

```

hopefully this device can be made to work with karmic

---

### Post by Fitzcarraldo on 2009-12-27
The dmesg output became different in the case of Sabayon Linux simply by rebooting, but perhaps you have to do something extra in Ubuntu. I googled and found the following post: **[Windows mode solution](http://glidetv.com/forums/glidetv-software/linux/1000168#comment-1000249)**, which states that you also need to do the following as root user:

```
update-initramfs -u
```
so give that a try.

By the way, if you want to look at the make files and the source code for the driver, and perform the changes that I described in my previous post, I extracted the directory /home/fitzcarraldo/Desktop/v9.08.14.1/installer/ from the composite ASCII-binary script /home/fitzcarraldo/Desktop/v9.08.14.1/ITE-Linux-AF903x-v9.08.14.1.sh by entering the following command:

```
tail -n +52 /home/fitzcarraldo/Desktop/v9.08.14.1/ITE-Linux-AF903x-v9.08.14.1.sh | tar zxf - >/dev/null 2>.err
```

---

### Post by Fitzcarraldo on 2009-12-28
I have just tried to install the DVB-T stick driver in an x86, rather than x86_64/amd64, edition of Linux, and with an earlier kernel. I used an old version of Sabayon Linux (4.0-r1 x86 edition, upgraded to the 2.6.28 kernel). I used the stick manufacturer's Linux software from the CD without making any changes. The driver installation was successful.

I launched the installer as the root user:
```
sh ITE-Linux-AF903x-v9.08.14.1.sh
```
and the Bash script ran to completion.

When I then inserted the stick, the output for it in dmesg is:
```
[  559.166036] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  559.286786] usb 1-1: configuration #1 chosen from 1 choice
[  559.291390] input: Afa Technologies Inc. AF9035A USB Device as /class/input/input10
[  559.291777] generic-usb 0003:15A4:1001.0001: input,hidraw0: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:10.3-1/input1
[  560.053878] AF903X: af903x_module_init
[  560.053920]         DRIVER_RELEASE_VERSION : v9.08.14.1
[  560.053923]         FW_RELEASE_VERSION     : v8_8_63_0
[  560.053926]         API_RELEASE_VERSION    : 200.20090402.0
[  560.204187] X:6352 conflicting memory types d8000000-e0000000 write-combining<->uncached-minus
[  560.204194] reserve_memtype failed 0xd8000000-0xe0000000, track write-combining, req write-combining
[  560.307695] X:8456 freeing invalid memtype d8000000-e0000000
[  560.561410] dvb-usb: found a 'ITEtech USB2.0 DVB-T Recevier' in warm state.
[  560.636945] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  560.637707] DVB: registering new adapter (ITEtech USB2.0 DVB-T Recevier)
[  560.638991] DVB: registering adapter 0 frontend 0 (AF903X USB DVB-T)...
[  560.650559] dvb-usb: ITEtech USB2.0 DVB-T Recevier successfully initialized and connected.
[  560.650599] usbcore: registered new interface driver dvb_usb_af903x
```
and the module was loaded:
```
sabayonx86 v9.08.14.1 # lsmod | grep dvb
dvb_usb_af903x        795464  0
dvb_usb                20364  1 dvb_usb_af903x
i2c_core               22804  2 dvb_usb,i2c_viapro
```

So I made the usbhid driver ignore the stick using the same method as before, and now the output in dmesg for the stick is:

```
[  179.574052] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  179.694812] usb 1-1: configuration #1 chosen from 1 choice
[  179.700704] input: Afa Technologies Inc. AF9035A USB Device as /class/input/input10
[  179.701482] generic-usb 0003:15A4:1001.0001: input,hidraw0: USB HID v1.01 Keyboard [Afa Technologies Inc. AF9035A USB Device] on usb-0000:00:10.3-1/input1
[  179.907450] X:6440 conflicting memory types d8000000-e0000000 write-combining<->uncached-minus
[  179.907457] reserve_memtype failed 0xd8000000-0xe0000000, track write-combining, req write-combining
[  179.913166] X:7315 freeing invalid memtype d8000000-e0000000
[  179.995511] AF903X: af903x_module_init
[  179.995576]         DRIVER_RELEASE_VERSION : v9.08.14.1
[  179.995578]         FW_RELEASE_VERSION     : v8_8_63_0
[  179.995581]         API_RELEASE_VERSION    : 200.20090402.0
[  180.538287] dvb-usb: found a 'ITEtech USB2.0 DVB-T Recevier' in warm state.
[  180.614566] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  180.615552] DVB: registering new adapter (ITEtech USB2.0 DVB-T Recevier)
[  180.616507] DVB: registering adapter 0 frontend 0 (AF903X USB DVB-T)...
[  180.627684] dvb-usb: ITEtech USB2.0 DVB-T Recevier successfully initialized and connected.
[  180.627727] usbcore: registered new interface driver dvb_usb_af903x
```
As you can see from the dmesg output, the stick is in the 'warm state', successfully initialised and connected. However for some reason usbhid still sees the device as a keyboard. Perhaps I would need to do something else in the case of a 2.6.28 kernel. Anyway, the stick's driver seems to be working, and it is now detected by Tvheadend, the DVB receiver and live TV streaming server that I wish to use.

I wonder if the hacks for later versions of the kernel that I gave in an earlier post would work in an x86 (32-bit) edition of Linux with the 2.6.30 to 2.6.32 versions of the kernel.

---

### Post by baldrick222 on 2009-12-28
I had been wondering about that

I was waiting for a power supply for p4 I have spare ( due in the next couple of days ) and was going to load a vanilla version of ubuntu 9.04 on it and see what the result was.

I have still not had success in getting the HID ignored even after the ramfs was updated.

---

### Post by xc3RnbFO8P on 2009-12-28
Did you try:
> options usbhid quirks=15a4:1001:0x0004

> > Which would be something like this:
> options usbhid quirks=15a4:1001:0x0004
> in your case.

Yeah, that'd be it. Can also slap an 0x in front of the device ID
components too, seems that's not a requirement though.

> Not totally sure about the 0x0004 though.

The 0x0004 flag is HID_QUIRK_IGNORE, which tells the usbhid driver to
ignore the device.
[http://www.linuxtv.org/pipermail/linux-dvb/2008-December/030942.html]("http://www.linuxtv.org/pipermail/linux-dvb/2008-December/030942.html")

---

### Post by Fitzcarraldo on 2009-12-28
It would be worth trying *Ringi*'s suggestion, in case Ubuntu behaves differently to the distribution that I am using. In my case, before making my first post in this thread I had tried the suggestion from the post that *Ringi* quoted but it did not work as the distribution I use needs all three fields to be in the full 6-digit hexadecimal format that I gave in my first post. But perhaps Ubuntu behaves differently.

The other thing you could try is to tell the usbhid driver to ignore the stick immediately until the next reboot, to see if that works:

```
modprobe usbhid quirks=0x15a4:0x1001:0x0004
```

---

### Post by baldrick222 on 2009-12-28
yes - below is my usbhid.conf file

```
desktop:~$ nano /etc/modprobe.d/usbhid.conf
  GNU nano 2.0.9        File: /etc/modprobe.d/usbhid.conf

options usbhid quirks=0x15a4:0x1001:0x0004
```

I am interested to see the result when I try the USB DVB-T on 32bit plain installs of ubuntu - but I have to wait for a power supply to arrive .

---

### Post by Fitzcarraldo on 2009-12-28
For the sake of completeness I also tried to install the stick's driver in my x86_64 Linux installation (2.6.32 kernel) without changing "lib" to "lib64" in the make files v9.08.14.1/installer/AF903x_SRC/Makefile and v9.08.14.1/installer/AF903x_SRC/Makefile.release (see Steps 1 and 3 in my second post) but still making the other changes listed in my second post. It made no discernible difference; the installation script still ran to completion and the console output from the dmesg and lsmod commands were identical to my earlier attempt.

The "error -12" in the error message "dvb_usb_af903x: probe of 1-1.4:1.0 failed with error -12" displayed by dmesg apparently indicates an ENOMEM error, which means that there was insufficient kernel memory. So it looks like the driver module built under a 64-bit Linux distribution and a 2.6.32 kernel has a memory leak. I don't know whether this is due to building the driver in a 64-bit distribution or whether it is due to building it under a 2.6.32 kernel using the hacks listed in my second post.

There appears to be a contradiction in the ReadMe.txt file in the v9.08.14.1 directory on the manufacturer's CD: In Section 1 (Release note for this specific version of the manufacturer's software) it states "This release supports x86 32bit and 64bit CPU families in Linux" but in Section 7 (Known problems & limitations) it states "Currently only x86 architecture is supported". Unfortunately I don't have a spare x86_64 PC on which to install a 64-bit distribution with a 2.6.29 or lower kernel in order to see if the driver would install correctly, so I still do not know if my success installing it in a 32-bit Linux installation with a 2.6.28 kernel was down to the 32-bit installation or to the version of the kernel.

Anyway, I await with interest the outcome of your experiment with a 32-bit edition of Ubuntu and a version of the kernel greater than 2.6.29. You'll almost certainly still have to apply at least my hacks in Steps 2 and 4 of my second post, as the manufacturer's make files and v4l directories only cover up to kernel 2.6.29.

EDIT (29.12.09 16:06 UTC): Actually, the more I look into it, the more I think it is not a problem of using an x86_64 distribution but rather the version of the kernel. I don't think my hack of using the 2.6.29 kernel af903x driver source code files for the 2.6.30 to 2.6.32 kernel is valid. I don't have a spare PC to install an x86_64 edition of Linux and a 2.6.29 kernel (the stick manufacturer's CD has driver source code for kernels up to 2.6.29), but I would not be surprised if the driver installer worked with that combination.

---

### Post by baldrick222 on 2010-01-09
just a quick update so you don't think I have given up :D

I have just been having no end of problems with my spare P4 unit and it is now sittinng on the table with just psu mobo cpu ram cd and hd running seatools from ubcd4.1.1.

hopefully I can find the problem I am having with it soon and get a 32bit 8.04.2 installed on it to continue looking for the USB DVB-T solution

---

### Post by baldrick222 on 2010-01-28
p4 problem seemed to be the speed the default bios settings were setting for the RAM on Auto. system running 32bit 8.04.02 , hair on my head less :D

unrared the files and in a terminal
```

sh ITE-Linux-AF903x-v9.08.14.1.sh

```

it ran to the end , but spat out a lot of errors - but lsmod | more showed the AF903x DVB-T modules.

I then installed Kaffeine , when told me it could not detect a DVB-T device.

I restarted the machine , and then Kaffiene detected the DVB-T device and I have been able to scan channels.

dmesg output is

```

[   47.585771] dvb-usb: found a 'ITEtech USB2.0 DVB-T Recevier' in warm state.
[   47.681588] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   47.682132] DVB: registering new adapter (ITEtech USB2.0 DVB-T Recevier)
[   47.682480] DVB: registering frontend 0 (AF903X USB DVB-T)...
[   47.694822] dvb-usb: ITEtech USB2.0 DVB-T Recevier successfully initialized and connected.
[   47.694856] usbcore: registered new interface driver dvb_usb_af903x

```

lsmod | more

```

dvb_usb_af903x        821864  1
dvb_usb                19852  1 dvb_usb_af903x
dvb_core               81404  1 dvb_usb
i2c_core               24832  2 dvb_usb,i2c_sis96x
usbcore               146412  6 dvb_usb_af903x,dvb_usb,usbhid,ehci_hcd,ohci_hcd

```


I am just scanning channels at the moment and thinking about trying a 9.10 32 bit installation.

---

### Post by baldrick222 on 2010-01-29
I installed 9.10 32bit with the same results as 64bit

it does seem to be the kernal version that causes the problem

in the readme for the 9035.linux.PC.dvb-tV9.07.10.1  , the revision history says

(3) Support kernel 2.6.29.

it is a bit of a paiin that upgrading the kernal causes there issues


any suggestions , I am willing to try as I have the P4 I can load with anything.

I had thought to tru mythbuntu 9.10 , but I assume it will have the same issues because of its kernal version

---

### Post by Fitzcarraldo on 2010-03-10
The driver's lack of support for the 2.6.30 and upwards kernels is definitely the problem. I gave up waiting for a reply from the manufacturer's support team to my e-mail. I called it a day for that model and bought an AVerTV Volar Black HD A850, which works with Linux kernel 2.6.30 and upwards. There is no mention of Linux in either the installation guide or the CD that came with the HD A850 stick. However, I googled the missing firmware file name "dvb-usb-af9015.fw" and found a link to the firmware file on the linuxtv.org Wiki site. I dowloaded dvb-usb-af9015.fw from the link given on the page [http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices) and copied it to /lib64/firmware/ and everything works the way it should. I'll find a good home for the EZTV860 with a Windows user. :icon_frown:

---

### Post by kimme on 2010-04-23
I have ordered [this device from DealExtreme]("https://www.dealextreme.com/details.dx/sku.8325#open%20full%20view") and was hoping it would work with my Ubuntu HTPC. Thanks for this thread...

---

### Post by emptybody on 2010-11-14
Hi, have someone files from 
[http://www.linux-cam.com/](http://www.linux-cam.com/)
?
this page is down and i didnt find this files in another place :/

---

### Post by Gizmonty on 2010-11-18
I also need the file ```
9035.linux.PC.dvb-tV9.07.10.1.zip
```. If anyone has this can they please put a link up and post it online. I think this file is in danger of extinction!

---

### Post by malakudi on 2010-11-29
I am attaching driver v9.08.14.1 for anyone interested. I got the driver after sending email to ITE support department. It is the latest available driver.

---

### Post by malakudi on 2010-11-29
Above attached file can be extracted with the following command:

```

tail -n +52 ITE-Linux-AF903x-v9.08.14.1.sh | tar -xzvf -

```

---

### Post by nmaraujo on 2011-01-24
hi,

did you manage to scan channels? i've got this error using scan:

scan /usr/share/dvb/dvb-t/pt-Lisbon 
scanning /usr/share/dvb/dvb-t/pt-Lisbon
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 842000000 0 2 1 3 1 3 0
>>> tune to: 842000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.

and this with dvbscan:
dvbscan /usr/share/dvb/dvb-t/pt-Lisbon 
Unable to query frontend status

with w_scan also didn't work.

can somebody help me?

thanks

---

### Post by aguiar.rafa on 2011-11-22
> **malakudi said:**
> I am attaching driver v9.08.14.1 for anyone interested. I got the driver after sending email to ITE support department. It is the latest available driver.

Hi, 

Thanks for the help so far, I'm trying to get my Asus DVB stick working but that's what I get. Can you please help?


[   13.517267] AF903X: af903x_module_init
[   13.517285]         DRIVER_RELEASE_VERSION : v9.08.14.1
[   13.517287]         FW_RELEASE_VERSION     : v8_8_63_0
[   13.517288]         API_RELEASE_VERSION    : 200.20090402.0
[   13.647557] [Device_init] Error 1
[   13.647561] dvb-usb: found a 'Asus U3100MINI_PLUS/T/RC Receiver' in warm state.
[   13.736680] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.736979] DVB: registering new adapter (Asus U3100MINI_PLUS/T/RC Receiver)
[   13.737205] DVB: registering adapter 0 frontend 0 (AF903X USB DVB-T)...
[   13.737223] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.737936] DVB: registering new adapter (Asus U3100MINI_PLUS/T/RC Receiver)
[   13.738153] DVB: registering adapter 1 frontend 0 (AF903X USB DVB-T)...
[   13.748805] dvb-usb: Asus U3100MINI_PLUS/T/RC Receiver successfully initialized and connected.
[   13.748819]         DRIVER_RELEASE_VERSION : v9.08.14.1
[   13.748820]         FW_RELEASE_VERSION     : v8_8_63_0
[   13.748822]         API_RELEASE_VERSION    : 200.20090402.0
[   13.851924] [Device_init] Error 1
[   13.851927] dvb-usb: found a 'Asus U3100MINI_PLUS/T/RC Receiver' in warm state.
[   13.940921] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.941221] DVB: registering new adapter (Asus U3100MINI_PLUS/T/RC Receiver)
[   13.941437] DVB: registering adapter 2 frontend 0 (AF903X USB DVB-T)...
[   13.941455] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.942171] DVB: registering new adapter (Asus U3100MINI_PLUS/T/RC Receiver)
[   13.942389] DVB: registering adapter 3 frontend 0 (AF903X USB DVB-T)...
[   13.953170] dvb-usb: Asus U3100MINI_PLUS/T/RC Receiver successfully initialized and connected.
[   13.953206] usbcore: registered new interface driver dvb_usb_af903x

---

