---
title: "Webcam help?"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by Revfisk on 2007-11-08
Hello.  Newb here.

I have a webcam and the drivers came with a Cd.  I installed it using wine and I can get the program to work, but cannot get it to recognize the webcam.  Nor can I get Camorama to connect.  Any thoughts.  It's definitely a cheap product, but I was hoping to make some use of it.  Any thoughts?

---

### Post by Sef on 2007-11-08
What Webcam make and model do you have?

How did you download Camorama?

---

### Post by Revfisk on 2007-11-08
I'm not sure how I got camerama.  It either came with Ubunut Gutsy, or I pulled it off of the Gutsy add/remove menu.  

I'm actually unsure what make and model camera I have.  The box says:

Digital Product
PC Camera

It's about as non-brand name as you get.

---

### Post by Revfisk on 2007-11-09
Any thoughts?

---

### Post by wsuetholz on 2007-11-09
I assume this is an USB device?

You should probably run two commands and post some of the output.

1) sudo lsusb

2) sudu dmesg

The dmesg will print out a lot of information, and might be more helpful if you were unplug the webcam and replug it back in before running that command.  Then you might be able to get away with just posting the last 20-30 lines of output.  lsusb lists the USB devices that the system thinks are plugged in, and the dmesg command lists out kernel messages.

Hope this helps..

---

### Post by Revfisk on 2007-11-09
1) sudo lsusb:


Bus 005 Device 012: ID 045e:00e1 Microsoft Corp. 
Bus 005 Device 011: ID 0ac8:307b Z-Star Microelectronics Corp. 
Bus 005 Device 008: ID 05e3:0606 Genesys Logic, Inc. 
Bus 005 Device 002: ID 04fc:0c25 Sunplus Technology Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 002: ID 0a5c:201e Broadcom Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

sudo dmesg: (only the most recent entries - I connected the device just a few minutes before running this)

upsd"
[   33.032000] IBM machine detected. Enabling interrupts during APM calls.
[   33.032000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.032000] apm: overridden by ACPI.
[   33.340000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   33.340000] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   33.340000] thinkpad_acpi: ThinkPad EC firmware 75HT18WW-1.00
[   33.348000] thinkpad_acpi: acpi_bus_get_device(bay) failed: -19
[   33.348000] thinkpad_acpi: disabling subdriver bay
[   33.760000] Failure registering capabilities with primary security module.
[   86.240000] NET: Registered protocol family 17
[  183.256000] usb 2-2: USB disconnect, address 3
[  191.972000] usb 5-4: new high speed USB device using ehci_hcd and address 6
[  192.108000] usb 5-4: configuration #1 chosen from 1 choice
[  192.108000] scsi3 : SCSI emulation for USB Mass Storage devices
[  192.108000] usb-storage: device found at 6
[  192.108000] usb-storage: waiting for device to settle before scanning
[  197.108000] usb-storage: device scan complete
[  197.112000] scsi 3:0:0:0: CD-ROM            Memorex  52MAXX 3252AJ1   4WS2 PQ: 0 ANSI: 0
[  197.112000] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[  197.380000] sr0: scsi3-mmc drive: 223x/52x writer cd/rw xa/form2 cdda tray
[  197.380000] Uniform CD-ROM driver Revision: 3.20
[  197.380000] sr 3:0:0:0: Attached scsi CD-ROM sr0
[  227.900000] usb 5-4: USB disconnect, address 6
[  230.316000] usb 5-4: new high speed USB device using ehci_hcd and address 7
[  230.448000] usb 5-4: configuration #1 chosen from 1 choice
[  230.448000] scsi4 : SCSI emulation for USB Mass Storage devices
[  230.448000] usb-storage: device found at 7
[  230.448000] usb-storage: waiting for device to settle before scanning
[  235.448000] usb-storage: device scan complete
[  235.448000] scsi 4:0:0:0: CD-ROM            Memorex  52MAXX 3252AJ1   4WS2 PQ: 0 ANSI: 0
[  235.452000] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[  235.452000] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  235.452000] sr 4:0:0:0: Attached scsi generic sg2 type 5
[  238.564000] cdrom: sr0: mrw address space DMA selected
[  238.656000] cdrom: sr0: mrw address space DMA selected
[  238.696000] UDF-fs: No VRS found
[  238.708000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  238.708000] ISOFS: changing to secondary root
[  450.264000] NET: Registered protocol family 10
[  450.264000] lo: Disabled Privacy Extensions
[  450.264000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  450.264000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[  467.816000] usb 5-4: USB disconnect, address 7
[  478.372000] usb 5-4: new high speed USB device using ehci_hcd and address 8
[  478.504000] usb 5-4: configuration #1 chosen from 1 choice
[  478.504000] hub 5-4:1.0: USB hub found
[  478.504000] hub 5-4:1.0: 4 ports detected
[  499.668000] usb 5-4.3: new low speed USB device using ehci_hcd and address 9
[  499.768000] usb 5-4.3: configuration #1 chosen from 1 choice
[  499.780000] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /class/input/input8
[  499.780000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.7-4.3
[  504.564000] usb 5-4.4: new high speed USB device using ehci_hcd and address 10
[  504.656000] usb 5-4.4: configuration #1 chosen from 1 choice
[  504.656000] scsi5 : SCSI emulation for USB Mass Storage devices
[  504.656000] usb-storage: device found at 10
[  504.656000] usb-storage: waiting for device to settle before scanning
[  509.656000] usb-storage: device scan complete
[  509.656000] scsi 5:0:0:0: CD-ROM            Memorex  52MAXX 3252AJ1   4WS2 PQ: 0 ANSI: 0
[  509.660000] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[  509.660000] sr 5:0:0:0: Attached scsi CD-ROM sr0
[  509.660000] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  510.888000] usb 5-4.4: reset high speed USB device using ehci_hcd and address 10
[  516.228000] usb 5-4.4: reset high speed USB device using ehci_hcd and address 10
[  521.872000] usb 5-4.4: reset high speed USB device using ehci_hcd and address 10
[  527.152000] usb 5-4.4: reset high speed USB device using ehci_hcd and address 10
[  527.244000] sr 5:0:0:0: [sr0] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  527.244000] end_request: I/O error, dev sr0, sector 64
[  527.244000] Buffer I/O error on device sr0, logical block 8
[  529.252000] usb 5-4.4: USB disconnect, address 10
[  529.252000] scsi 5:0:0:0: [sr0] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  529.252000] end_request: I/O error, dev sr0, sector 64
[  529.252000] Buffer I/O error on device sr0, logical block 8
[  529.348000] scsi 5:0:0:0: rejecting I/O to dead device
[  529.348000] scsi 5:0:0:0: rejecting I/O to dead device
[  529.348000] scsi 5:0:0:0: rejecting I/O to dead device
[  529.412000] scsi 5:0:0:0: rejecting I/O to dead device
[  529.412000] scsi 5:0:0:0: rejecting I/O to dead device
[  529.412000] scsi 5:0:0:0: rejecting I/O to dead device
[  560.232000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  578.084000] ath0: no IPv6 routers present
[ 1246.836000] usb 5-4.1: new full speed USB device using ehci_hcd and address 11
[ 1246.928000] usb 5-4.1: configuration #1 chosen from 1 choice
[ 1246.928000] usb 5-4.3: USB disconnect, address 9
[ 1247.132000] usb 5-4.3: new low speed USB device using ehci_hcd and address 12
[ 1247.232000] usb 5-4.3: configuration #1 chosen from 1 choice
[ 1247.244000] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /class/input/input9
[ 1247.244000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.7-4.3

If I disconnect my usb hub and connect only the device, then dmsg reads:

[ 1246.928000] usb 5-4.1: configuration #1 chosen from 1 choice
[ 1246.928000] usb 5-4.3: USB disconnect, address 9
[ 1247.132000] usb 5-4.3: new low speed USB device using ehci_hcd and address 12
[ 1247.232000] usb 5-4.3: configuration #1 chosen from 1 choice
[ 1247.244000] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /class/input/input9
[ 1247.244000] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.7-4.3
[ 1502.100000] usb 5-4: USB disconnect, address 8
[ 1502.100000] usb 5-4.1: USB disconnect, address 11
[ 1502.100000] usb 5-4.3: USB disconnect, address 12
[ 1509.800000] usb 2-2: new full speed USB device using uhci_hcd and address 4
[ 1509.996000] usb 2-2: configuration #1 chosen from 1 choice


Any gurus out there to tackle this one!  ](*,)

---

### Post by Revfisk on 2007-11-09
Help help help!:popcorn:

---

### Post by jbcola on 2007-11-10
Hi, i think i've got a Z-Star webcam too,  ID 0ac8:307b

I've downloaded the GSPCA kernel module drivers sources from [http://mxhaard.free.fr/](http://mxhaard.free.fr/)
I've searched the source code and found that the 0ac8:305b Webcam was supported.


After duplicating the source code for the 307b webcam, i've compiled the kernel module and instaled it.

It now detects the webcam, but once i want to use is, i receive an error:

(Module loaded with this command: "sudo modprobe gspca debug=10")

Maybe someone knows what has to be changed in the module source...

The log is attached

---

### Post by ghostcrab on 2007-11-10
I have a $19 dollar web cam I got from wal-mart I olny use it to mess with people 
I have a FBI hat and a CIA hat LOL

anyway I use camorama also XawTV is good you can get them useing synaptic

---

### Post by Revfisk on 2007-11-10
Camerarm does not detect my webcam.  I'll look into Xawtv.  What I really need is a guru.  There is no way I can start compiling kerne#-o:biggrin:ls!

---

### Post by ghostcrab on 2007-11-11
hey I like say cheese better it's in add remove too. try that if that don't detect it you may have to dig

---

### Post by hx129 on 2008-02-17
This webcam is supported by the newest gspca driver released on 12/24/2007.
Just download and install this kernel module(be sure to remove the old one) and you should be fine. 
I have tested it with kopete.

---

### Post by hieund on 2008-02-18
I have the same webcam, and I've successfully installedl gspca 2007.12.24. but my computer still don't detect webcam:

lsusb:
Bus 001 Device 013: ID 0ac8:307b Z-Star Microelectronics Corp. 

> modprobe gspca
dmesg | tail
[ 2987.904000] usb 1-2: USB disconnect, address 10
[ 2990.184000] usb 1-2: new full speed USB device using uhci_hcd and address 11
[ 2990.380000] usb 1-2: configuration #1 chosen from 1 choice
[ 2996.696000] usb 1-2: USB disconnect, address 11
[ 2998.740000] usb 1-2: new full speed USB device using uhci_hcd and address 12
[ 2998.936000] usb 1-2: configuration #1 chosen from 1 choice
[ 3013.312000] usb 1-2: USB disconnect, address 12
[ 3015.772000] usb 1-2: new full speed USB device using uhci_hcd and address 13
[ 3015.968000] usb 1-2: configuration #1 chosen from 1 choice

> v4l-info
open /dev/video0: No such file or directory

then I tried to create /dev/video0:
> mknod c 81 0 /dev/video0
mknod: invalid device type `81'

can anyone help?

---

### Post by baucha_linux on 2008-02-23
i also got the same webacm type as hieund and hav installed latest gspca driver 22071224. My system recognizes the cam type but when i use any webcam apps like camorama, kopete, skype or cheese the app just freezes and there is no display. Can anyone help us pls.

> dmesg
[14910.736000] usb 5-1: new full speed USB device using uhci_hcd and address 2
[14910.988000] usb 5-1: configuration #1 chosen from 1 choice
[14911.220000] Linux video capture interface: v2.00
[14911.284000] /home/baucha/Documents/gspcav1-20071224/gspca_core.c: USB GSPCA camera found.(ZC3XX)
[14911.284000] /home/baucha/Documents/gspcav1-20071224/gspca_core.c: [spca5xx_probe:4275] Camera type JPEG
[14911.284000] /home/baucha/Documents/gspcav1-20071224/Vimicro/zc3xx.h: [zc3xx_config:591]  Sensor OV7620
[14911.288000] /home/baucha/Documents/gspcav1-20071224/gspca_core.c: [spca5xx_getcapability:1249] maxw 640 maxh 480 minw 160 minh 120
[14911.288000] usbcore: registered new interface driver gspca
[14911.288000] /home/baucha/Documents/gspcav1-20071224/gspca_core.c: gspca driver 01.00.20 registered

Please help us so that we dont hav to rely on windows to use our webcam.

After I use those apps i get following in the dmesg

> [15343.932000] /home/baucha/Documents/gspcav1-20071224/gspca_core.c: [gspca_set_isoc_ep:945] ISO EndPoint found 0x81 AlternateSet 7

I have been trying to find the solution since last 2-3 days, full day i had been in net but no success so far. so pls help

---

### Post by baucha_linux on 2008-02-24
Bump! 
](*,)

---

### Post by baucha_linux on 2008-02-25
It seems for timebeing no one has solution for problem like mine. I googled for 2-3 days n found out that the developers are discussing on this issue... including Michel Xhaard. All of those who have this problem lets stay with our fingers crossed and hope they will be able to find the solution soon. I really appreciate everyone's effort in making linux better.

[http://article.gmane.org/gmane.linux.drivers.spca50x.devel/2761](http://article.gmane.org/gmane.linux.drivers.spca50x.devel/2761)

---

### Post by boballen55 on 2008-06-17
So has anyone made any progress on this?  I just got the same 0ac8:307b camera.  I think I got the /dev/video* thing to show up right but the camera won't work.

---

### Post by jbcola on 2008-06-23
No, even with the Ubuntu Hardy release, no change.

The cam is detected, but doesn't work.

Best regards,
JL

---

