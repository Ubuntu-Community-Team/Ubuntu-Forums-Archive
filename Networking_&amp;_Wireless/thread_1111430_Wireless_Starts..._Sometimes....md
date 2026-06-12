---
title: "Wireless Starts... Sometimes..."
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by mikedmor on 2009-03-30
when i type 'lspci' here is what comes up for my network card:

Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

I have had problems with this card since i started using ubuntu. From the very first time i booted up it cause my pc to freeze. This was fixed by grabbing the drivers from my cd and using ndiswrapper. But sometimes when i boot my wireless card CANNOT connect to any network no matter what i do until i reboot my pc (sometimes i have to reboot up to 10 times). At first i though it was the ath9k drivers so i blacklisted them. I still feel this may be the problem because when i run 'ndiswrapper -l' it returns this:

```
netathw : driver installed
	device (168C:0023) present (alternate driver: ath9k)
```

here is a copy of my blacklist:

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

#remove the ath9k driver because of freezing problem
blacklist ath9k

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

If you have any suggestions or need anymore information please ask me or let me know what you think! I really wanna fix this problem

Thank you

-Mike

---

