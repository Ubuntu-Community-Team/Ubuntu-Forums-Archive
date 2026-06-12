---
title: "libv4l2: error setting pixformat: Input/output error"
date: 2011-01-29
forum: Multimedia Software
---

### Post by tiejaz on 2011-01-29
Ok so when I run 'cheese' (with or without sudo and gksudo)
it shows a black screen and gives me the error
```
"libv4l2: error setting pixformat: Input/output error"

```it worked before and isn't working now
lsusb gives this:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 015: ID 0bc2:3300 Seagate RSS LLC 
Bus 002 Device 003: ID 03f0:2504 Hewlett-Packard DeskJet F4200 series
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I'm running Ubuntu 11.04 with Gnome 2.32.0

---

### Post by no2498 on 2011-01-29
look in sound and video for xawtv
if not loaded find and install it
try the cam in xawtv
if it comes on retry cheese

---

