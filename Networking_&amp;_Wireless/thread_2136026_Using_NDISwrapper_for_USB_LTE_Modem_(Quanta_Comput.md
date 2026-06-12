---
title: "Using NDISwrapper for USB LTE Modem (Quanta Computer - Mobily Connect 4G)"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by hishmaj on 2013-04-16
I am trying to connect to the internet using a Quanta Computer USB LTE modem (Mobily Connect 4G). While trying to the install the Windows driver on Ubuntu using NDISwrapper, I managed to get it installed and it even detects the driver and device when I try > ndiswrapper -l for which I get the output:
> qntbulk : driver installed
device (0408:EA25) present

This is where I get stuck. I don't know what to do after loading the new driver using > [I]
sudo depmod -a [/I][I]
sudo modprobe ndiswrapper[/I]

When I try > iwconfig
I get
> lo      no wireless extensions.
wlan0 IEEE 802.11bg ESSID: off/any ...
eth0 no wireless extensions.

How do I go about connecting via the USB modem, after this? Any help will be greatly appreciated!

---

### Post by hishmaj on 2013-04-16
FYI, the modem that I am trying to connect is listed here:
[http://www.4gltemall.com/mobily-connect-4g-usb-modem-1k3m-unlocked.html](http://www.4gltemall.com/mobily-connect-4g-usb-modem-1k3m-unlocked.html)

---

### Post by sanderj on 2013-04-16
I can't help with NDISwrapper, but I have a question: why are you trying the NDISwarpper-path, and not native support? I would do this:

Get 13.04 dialy built, write it to USB-stick or CD, and boot from it.
Type "lsusb"
Plugin the usb-modem
Type "lsusb" again, and find the new device. Then google the USB id on Google.

---

### Post by hishmaj on 2013-04-16
> **sanderj said:**
> I can't help with NDISwrapper, but I have a question: why are you trying the NDISwarpper-path, and not native support? I would do this:

Get 13.04 dialy built, write it to USB-stick or CD, and boot from it.
Type "lsusb"
Plugin the usb-modem
Type "lsusb" again, and find the new device. Then google the USB id on Google.

I am currently on 12.04 LTS, where there is no native support for this model of LTE USB modem. When I plug-in, "lsusb" detects it, but when I try to make a new connection under network tools, there is no sign of any USB modem. Here is the output for "lsusb":
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. Digital Media Card Reader
Bus 001 Device 006: ID 19d2:0117 ZTE WCDMA Technologies MSM 
**Bus 002 Device 004: ID 0408:ea25 Quanta Computer, Inc.** 



The Device 004 in bold, is the modem I am trying to connect. The ZTE modem in the list is a 3G dongle, and it works fine.

So do you think I can work it natively on 13.04? Not sure why you want me to go that route.

---

### Post by sanderj on 2013-04-16
You could try with your current Ubuntu version. Which Ubuntu version do you use?

EDIT:

I now remember why I adviced you Ubuntu 13.04 ... apparantly your current Ubuntu version is not recognizing your USB-3g/4g-dongle ... :P

---

### Post by hishmaj on 2013-04-16
> **sanderj said:**
> You could try with your current Ubuntu version. Which Ubuntu version do you use?

EDIT:

I now remember why I adviced you Ubuntu 13.04 ... apparantly your current Ubuntu version is not recognizing your USB-3g/4g-dongle ... :P

I am using Ubuntu 12.04 and ofcourse I tried it before using ndiswrapper.

---

### Post by bmork on 2013-04-18
> **hishmaj said:**
> I am currently on 12.04 LTS, where there is no native support for this model of LTE USB modem. When I plug-in, "lsusb" detects it, but when I try to make a new connection under network tools, there is no sign of any USB modem. Here is the output for "lsusb":

The Device 004 in bold, is the modem I am trying to connect. The ZTE modem in the list is a 3G dongle, and it works fine.

So do you think I can work it natively on 13.04? Not sure why you want me to go that route.

I don't think that modem is supported just yet. But if you're lucky, adding the support shouldn't take long.  Could you start with posting the output of
```
lsusb -vd 0408:ea25 
```
?

And if that shows only usb-storage interfaces, then you need to try switching it to modem mode.  There is one modem with the same vendor ID in the usb_modeswitch database - 0408:f000 - you should probably try a similar config first:

```
# Yota Router (Quanta 1QDLZZZ0ST2)

TargetVendor=  0x0408
TargetProduct= 0xd009

MessageContent="5553424312345678000000000000061b004600000000000000000000000000"

```

But let's first see if this is necessary.  Awating the lsusb output.

---

