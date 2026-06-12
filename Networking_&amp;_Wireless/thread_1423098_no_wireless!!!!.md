---
title: "no wireless???!!!!"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by freesom on 2010-03-06
hi
this is my first thread 
i have problem in usb wirless card
my system is ubuntu 9.04
the system dosent detect the usb card
after i install update give me that the driver is rt2800
but cant detect the chipset 
whe i try on windows it give me the name of usb adapter is 802.11 wireless adapter just only
the name of the wireless adapter is WUA-315 11g wireless usb adapter
plz help me to find the correct driver for this usb adapter and how to install it on ubuntu 9.04

---

### Post by chili555 on 2010-03-06
Please open Applications -> Accessories -> Terminal and do:```
lsusb
dmesg | grep rt2
```Post the result and we'll proceed.

---

### Post by freesom on 2010-03-06
i do as you told me
and whe i post lsusb give me
Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp
but wireless network doesnt appear

---

### Post by chili555 on 2010-03-06
And how about the second command?```
dmesg | grep rt2
```If this produces no output, please do:```
sudo modprobe rt2800usb
iwconfig
```Thanks.

---

### Post by freesom on 2010-03-06
when i put second commad nothing appear

dmesg | grep rt2
and when i put iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by wojox on 2010-03-06
May try:

```
lspci | grep -i net
```

May show maybe not. That's an old adapter, huh?

---

### Post by chili555 on 2010-03-06
> **wojox said:**
> May try:

```
lspci | grep -i net
```

May show maybe not. That's an old adapter, huh?Don't we already know what his adapter is?> Bus 001 Device 003: ID 148f:2070 Ralink Technology, Corp

---

### Post by chili555 on 2010-03-06
Please try these two commands in exact order:```
sudo modprobe rt2800usb
dmesg | grep rt2
```There must be some sign that, at least, the module loaded.

Even on my system, which doesn't have your device, I get:> $ sudo modprobe rt2800usb
[sudo] password for chili: 
$ dmesg | grep rt2
[ 7090.480905] usbcore: registered new interface driver rt2800usbIn your case, the driver ought to do more than appear, it ought to create an interface, ra0, perhaps. The output from *dmesg* will tell us whats going on inside the system and why, if not, your wireless is not starting up.

---

