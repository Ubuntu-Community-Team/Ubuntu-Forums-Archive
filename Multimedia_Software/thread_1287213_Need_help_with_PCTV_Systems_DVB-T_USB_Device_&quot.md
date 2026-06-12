---
title: "Need help with PCTV Systems DVB-T USB Device &quot;PCTV 73e SE&quot;"
date: 2009-10-09
forum: Multimedia Software
---

### Post by PrivateLifeOfPlants on 2009-10-09
Hi,

Its a "PCTV 73e SE". Branded "pctv systems" which I think used to be pinnacle.

I just cant get it to work! Ive tried installing the firmware for the pinnacle PCTV 73e, compiled v4l, installed modules & kaffeine etc no luck.

Ubuntu just wont recognize it apart from dmesg says this:

[ 2143.696045] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 2143.829353] usb 1-6: configuration #1 chosen from 1 choice



Is this device even supported???

Please somebody help me! :(

---

### Post by PrivateLifeOfPlants on 2009-10-13
Nobody?

---

### Post by telegraphRoad on 2009-10-18
I have the same problem.

I think that the device is too new, and it is not recognized by the unerlying DVB drivers... any idea?

---

### Post by egdev on 2009-10-19
Hi,
I found the problem.
It is a wrong vendorID.
You must compile v4l-dvb with the following changes :
file: linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h
You must add the following line :
#define USB_VID_PINNACLE                        0x2304
#define USB_VID_PINNACLE_2                        0x2013

file :  linux/drivers/media/dvb/dvb-usb/dib0700_devices.c
find the line : 
{ USB_DEVICE(USB_VID_PINNACLE,  USB_PID_PINNACLE_PCTV73ESE) },

change by :
{ USB_DEVICE(USB_VID_PINNACLE_2,  USB_PID_PINNACLE_PCTV73ESE) },
After make && sudo make install && depmod -a

---

### Post by PrivateLifeOfPlants on 2009-10-19
YAY!! Thank you!! You have made me a very happy chappy!:)

---

### Post by egdev on 2009-10-20
You're welcome, it's a pleasure.

PS : sorry for my very bad english, I am french

---

