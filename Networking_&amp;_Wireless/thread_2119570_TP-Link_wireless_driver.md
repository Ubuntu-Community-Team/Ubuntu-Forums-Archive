---
title: "TP-Link wireless driver"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by HuSoft on 2013-02-24
Hello people,
My problem is that my TP-Link USB wireless adapter TL-WN7200ND won't work on my Ubuntu 10.04, although it's perfectly working on windows 7. Do I need any drivers to get it work? Any suggestions?

EDIT:


**** rfkill ****

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


**** lsusb ****

```
Bus 005 Device 002: ID 15d9:0a4c Dexon 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 14cd:125c Super Top 
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


**** blacklist.conf ****

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

---

### Post by chili555 on 2013-02-24
> Do I need any drivers to get it work? Possibly. Please run and post:```
lsusb
```Thanks.

---

### Post by HuSoft on 2013-02-24
> **chili555 said:**
> Possibly. Please run and post:```
lsusb
```Thanks.


```


husam@Husam-PC:~$ lsusb
Bus 005 Device 002: ID 15d9:0a4c Dexon 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 14cd:125c Super Top 
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by chili555 on 2013-02-24
> My problem is that my TP-Link USB wireless adapter TL-WN7200ND won't work on my Ubuntu 10.04We could turn ourselves inside out, write a few conf files, trial and error and get it working...maybe...partially in 10.04; or you could install 12.04 LTS and it would work immediately. Which do you prefer?

---

