---
title: "Not detecting my monitor"
date: 2015-04-06
forum: Multimedia Software
---

### Post by krelverehan on 2015-04-06
All of the sudden, after my last boot, my screen is stuck at 800x600 (4:3), when it should be 1440x900 (16:10) - a Dell monitor using DVI. And my video card is a NVIDIA GM204 [GeForce GTX 970].

In the preferences, it isn't detecting my monitor any more, and labels it "unknown display".

This is weird, as I haven't done an update/upgrade since my last reboot.

Any thoughts?

```
**krel@namcle:~$ xrandr**
Screen 0: minimum 8 x 8, current 800 x 600, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 connected primary 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3*+
Unknown-0 disconnected (normal left inverted right x axis y axis)
```

```
**krel@namcle:~$ cat /var/log/Xorg.0.log | grep WW**
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.128] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.128] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.128] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.128] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.128] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.131] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     5.131] (WW) "xmir" is not to be loaded by default. Skipping.
[     5.202] (WW) Falling back to old probe method for modesetting
[     5.202] (WW) Falling back to old probe method for fbdev
[     5.202] (WW) Falling back to old probe method for vesa
[     5.993] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[     5.993] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[     5.993] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[     5.993] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[     5.993] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[     5.993] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[     5.993] (WW) NVIDIA(GPU-0):     care.
[     6.041] (WW) NVIDIA(0): DFP-4 does not have an EDID, or its EDID does not contain a
[     6.041] (WW) NVIDIA(0):     maximum image size; cannot compute DPI from DFP-4's EDID.
[     8.896] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[     8.896] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[     8.896] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[     8.896] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[     8.896] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[     8.896] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[     8.896] (WW) NVIDIA(GPU-0):     care.
[    10.167] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[    10.167] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[    10.167] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[    10.167] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[    10.167] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[    10.167] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[    10.167] (WW) NVIDIA(GPU-0):     care.
[    22.288] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[    22.288] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[    22.288] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[    22.289] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[    22.289] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[    22.289] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[    22.289] (WW) NVIDIA(GPU-0):     care.
[   495.306] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[   495.306] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[   495.306] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[   495.306] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[   495.306] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[   495.306] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[   495.306] (WW) NVIDIA(GPU-0):     care.
[   630.443] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[   630.443] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[   630.443] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[   630.443] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[   630.443] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[   630.443] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[   630.443] (WW) NVIDIA(GPU-0):     care.
[  1063.889] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[  1063.889] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[  1063.889] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[  1063.889] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[  1063.889] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[  1063.889] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[  1063.889] (WW) NVIDIA(GPU-0):     care.
[  1378.461] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[  1378.461] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[  1378.461] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[  1378.461] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[  1378.461] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[  1378.461] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[  1378.461] (WW) NVIDIA(GPU-0):     care.
[  1509.900] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[  1509.900] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[  1509.900] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[  1509.900] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[  1509.900] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[  1509.900] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[  1509.900] (WW) NVIDIA(GPU-0):     care.
[  1751.804] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-4 is invalid:
[  1751.804] (WW) NVIDIA(GPU-0): - The EDID has a bad checksum. The "IgnoreEDIDChecksum" X
[  1751.804] (WW) NVIDIA(GPU-0):     configuration option may be used to attempt using mode
[  1751.804] (WW) NVIDIA(GPU-0):     timings in this EDID in spite of this error. A corrupt
[  1751.804] (WW) NVIDIA(GPU-0):     EDID may have mode timings beyond the capabilities of your
[  1751.804] (WW) NVIDIA(GPU-0):     display, and could damage your hardware. Please use with
[  1751.804] (WW) NVIDIA(GPU-0):     care.
```

```
**krel@namcle:~$ cat /var/log/Xorg.0.log | grep EE**
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.202] (EE) open /dev/fb0: No such file or directory
[     8.980] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    10.087] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    10.095] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    61.018] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
```

---

### Post by dino99 on 2015-04-07
As often the EDID is wrong; but 'nouveau' at least should works, otherwise it can be a dvi issue 
if you have set a xorg.conf, then delete or rename it, as now the kernel is doing the job by default

---

### Post by krelverehan on 2015-04-07
> **9d9 said:**
> As often the EDID is wrong; but 'nouveau' at least should works, otherwise it can be a dvi issue 
if you have set a xorg.conf, then delete or rename it, as now the kernel is doing the job by default

Where is the xorg.conf file located? I can't find it, which leaves me to believe it doesn't exist on my machine. I am running 14.10, 64bit.

---

