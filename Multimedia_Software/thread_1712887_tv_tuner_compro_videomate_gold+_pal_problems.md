---
title: "tv tuner compro videomate gold+ pal problems"
date: 2011-03-23
forum: Multimedia Software
---

### Post by konsta82 on 2011-03-23
I'm trying to set up this card on maverick. Modprobe gives me absolutely nothing
```
konsta@konsta-MS-7592:~$ sudo modprobe saa7134 card=41
[sudo] password for konsta: 
konsta@konsta-MS-7592:~$ 

```
I thought maybe something is using this module but ```
konsta@konsta-MS-7592:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
konsta@konsta-MS-7592:~$ sudo rmmod saa7134-alsa
ERROR: Module saa7134_alsa is in use

```
Forcing didn't killed it
```
konsta@konsta-MS-7592:~$ sudo rmmod -f saa7134_alsa
ERROR: Removing 'saa7134_alsa': Resource temporarily unavailable

```
Tried to blacklist this 
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
blacklist saa7134_alsa
blacklist saa7134_dvb
blacklist saa7134
```
but nothing is really changed.
Tvtime says no signal and 
```
konsta@konsta-MS-7592:~$ sudo tvtime scanner
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/konsta/.tvtime/tvtime.xml
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Thank you for using tvtime.

```
Anyone has some ideas how to solve this ?

---

### Post by konsta82 on 2011-03-23
I really hope someone has card like this,that will mean a lot to me

---

### Post by konsta82 on 2011-03-25
bump

---

### Post by konsta82 on 2011-06-13
working options for this card are
card=49 tuner=69 (37 or 40 also works fine)

---

