---
title: "Gobi-loader on Ubuntu 12.10 64  bit"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by abishur on 2013-03-22
I'm trying to get a gobi 2000 Wireless modem card on my Dell Precision M4500 to work.  I've seen a lot of talk on how to do this using older versions of Ubuntu but nothing more recent.

Things I've done:

Installed gobi-loader (most recent from apt-get) 

Copied apps.mbn and amss.mbn and UQCN.mbn from a working windows 7 x64 install (located in C:\Program Files (x86)\QUALCOM\Images\Dell\1), I am using Verizon which is why I chose the 1 directory.

Did a complete shutdown and turned it back on, with no results.

Tried modifying /lib/udev/rules.d/60-gobi.rules and changed KERNEL=="ttyUSB*" to DEVNAME=="ttyUSB*" and even tried explicitly stating it should be USB0, did a full shutdown after each change with no results.

Tried modifying /lib/udev/rules.d/77-mm-usb-device-blacklist.rules and adding 

```
# Qualcomm Gobi 2000 QDL
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="8185", ENV{ID_MM_DEVICE_IGNORE}="1"
```

which should be right based of my lsusb

```

Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
Bus 001 Device 004: ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
Bus 001 Device 005: ID 05ca:1814 Ricoh Co., Ltd HD Webcam
Bus 002 Device 003: ID 054c:05bf Sony Corp. 
Bus 002 Device 004: ID 413c:8185 Dell Computer Corp. Gobi 2000 Wireless Modem (QDL mode)
Bus 002 Device 007: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 006: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor

```

I've also done an md5sum to confirm that my .mbn files match the working windows files

I've also checked lsmod | grep qcserial

```

qcserial               12766  0 
usb_wwan               20098  1 qcserial
usbserial              42355  2 qcserial,usb_wwan

```

which shows that nothing is trying to use the qcserial on boot.

On one of the (many, many, MANY) sites I read via google someone  mentioned you might need to modify one of the .mbn files to match your  USB information, but they did not mention which file or how to modify  them.

Can anyone help me figure out why nothing is happening?  Or has anyone actually gotten this thing to work on Ubuntu 12.10?

---

### Post by abishur on 2013-03-22
side note, whenever I try to manually run gobi-loader with the command

```
/lib/udev/gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi
```

It just hangs.  When I read about that it lead me to editting /lib/udev/rules.d/77-mm-usb-device-blacklist.rules, but it has had no effect on my system

---

### Post by gordintoronto on 2013-03-22
[http://securit.se/en/2012/03/guide-sa-har-far-du-gobi-2000-wireless-modem-att-fungera-ubuntu-12-04/](http://securit.se/en/2012/03/guide-sa-har-far-du-gobi-2000-wireless-modem-att-fungera-ubuntu-12-04/)

---

### Post by abishur on 2013-03-25
Thanks Gordin, I've actually followed the instructions in that link before.  It does successfully recognize my modem (90% of the time at any rate), but it won't let me connect to my plan.  I'm not certain if this is because I live in the US and the driver package is... well I'm not sure where support.ts would be, but my guess is Europe or Asia as it doesn't give me the option to connect to the US CDMA network.

---

### Post by abishur on 2013-08-06
I was never able to get this issue worked out, but it turns out that this is a well known issue that's been busted ever since 12.04.  One of the interesting things about this problem is that if I load my computer into windows first and then reboot it into Ubuntu it then the device is recognized just fine.  But that's a bit of a hassle, has anyone ever been able to get the card working within a VM?  It would be a lot easier to boot up a VM long enough for the firmware to get loaded and then reattach the device to the host computer.

Well to be honest it would be better if whatever was broken back in the kernel was fixed, but it's been a long time, it's a well known issue, and it's just not going to happen :p

---

### Post by abishur on 2013-08-19
I was finally able to get this working on Ubuntu 13.04 using the gobi_loader in the repository (sudo apt-get install gobi_loader).  The issue ended up being with the firmware.  If you use the latest firmware then it fails to load properly.  I suspect this was done dilibertly to prevent use in Linux :mad: as at the same time Dell changed their installation package such that you can't unpack the file in linux.  When a co-worker who had the same computer told me he had the modem working I got his "outdated" firmware files and using them with gobi_loader had everything working perfectly.  I'll try to find an old version of the installation package through dell or lenovo or someone and post a link to it if I can find it.  In the mean time, here's the md5sum from the three files I used.  I'm using Verizon so they came from the "1" directory

51aa00c43b7eab331e6da1a422e37ff3  amss.mbn
4f46a856fcceb197943d0cf3257c3621  apps.mbn
6e05582f7997f9385e0edab431a4814c  UQCN.mbn

---

