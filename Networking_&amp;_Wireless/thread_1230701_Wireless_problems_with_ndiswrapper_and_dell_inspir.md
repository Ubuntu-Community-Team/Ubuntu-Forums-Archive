---
title: "Wireless problems with ndiswrapper and dell inspiron 1300"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by themusicalduck on 2009-08-03
I'm trying to setup wireless on a a dell inspiron 1300, but can't persuade the wireless to work. I've tried following a number of howtos on making this particular card work but they don't seem to make much difference. It seems like most of the information available on this card is outdated.

ndiswrapper -l comes up with this :

```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'ssb'
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)

```

/etc/modprobe.d/blacklist.conf says this:

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

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

#broadcom native driver
blacklist bcm43xx

#wireless driver
ssb
```

/etc/modprobe.conf says this:

```
alias wlan0 ndiswrapper
```

Under network manager it used to say 'Device not ready' or something similar. Now it says nothing, but doesn't list any wireless networks as available.

---

### Post by themusicalduck on 2009-08-03
bump

---

### Post by themusicalduck on 2009-08-05
final bump. ANY suggestions on how to make this work? It would suck if I had to reinstall windows for this since everything else works so well :(

---

### Post by Kevoc on 2009-08-13
Not sure if this will help, but looking at your blacklist.conf, you seem to have left out 'blacklist' before ssb.
So:
#wireless driver
ssb
Should be: 
#wireless driver
blacklist ssb
I guess. I'm having all sorts of problems with wireless drivers too at the moment.

---

