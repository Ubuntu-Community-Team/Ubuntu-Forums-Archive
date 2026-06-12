---
title: "Acer crystal eye webcam stopped"
date: 2013-04-26
forum: Multimedia Software
---

### Post by k290 on 2013-04-26
Hi I hope someone can help me resolve this issue,

At some point, my Acer Crystal Eye has stopped working. It used to work. 

In Cheese Webcam Booth it shows a black screen. The little camera light next to the webcam isn't switched on.

 In Edit -> Preferences-> Webcam in the Device dropdown it has "Acer Crystal Eye Webcam(/dev/video0)" but the dropdown is disabled and greyed out.

Im on Ubuntu 12.04.2, on an Acer Travelmate 5320

Please help, 
Thanks.

---

### Post by k290 on 2013-04-27
Bump

---

### Post by tgalati4 on 2013-04-27
Start with the basics, open a terminal:

```
lsusb
```

It should look something like:

tgalati4@Mint14-Extensa ~ $ lsusb
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And:

```
cd /var/log
grep webcam dmesg*
```

tgalati4@Mint14-Extensa /var/log $ grep webcam dmesg*
dmesg:[    1.569008] usb 1-1: Product: Acer CrystalEye webcam
dmesg:[   26.502332] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
dmesg:[   26.509613] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input4
dmesg.0:[    1.281266] usb 1-1: Product: Acer CrystalEye webcam
dmesg.0:[   28.561473] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
dmesg.0:[   28.564232] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input4

If the kernel doesn't see it, it won't be used.  Could be a bad cable that runs through the hinge.

---

### Post by k290 on 2013-04-28
Thanks for the handy reply.Here's the results

```
matthew@matthew-Travelmate5320:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0105 Acer, Inc 
Bus 002 Device 002: ID 12d1:140c Huawei Technologies Co., Ltd. 
Bus 007 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. Optical Mouse
```

  Not sure what "Acer, Inc" is..

```
matthew@matthew-Travelmate5320:/var/log$ grep webcam dmesg*
dmesg:[   27.234010] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (5986:0105)
dmesg:[   27.295492] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input5
dmesg.0:[   27.132769] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (5986:0105)
dmesg.0:[   27.243793] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input5

```



By the way I dual-boot another OS now and then,  and its working there.

---

### Post by k290 on 2013-04-30
Bump

---

