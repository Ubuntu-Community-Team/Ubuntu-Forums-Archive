---
title: "Resolutions listed in Display Preferences dialog and xorg.conf are not the same"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by jis on 2006-09-10
Xubuntu's Display Preferences dialog lists many very low resolution modes that are not listed in xorg.conf and does not list all high resolution modes listed in xorg.conf. There is the "Default" item in the list and I suppose it is the highest resolution listed in xorg.conf, but that resolution is not listed elsewhere in the list of the dialog. Why are lists so different? How can I get the resolutions listed in xorg.conf to the dialog's list and get rid of those useles low resolution items?

---

### Post by Ziox on 2006-09-10
> **jis said:**
> Xubuntu's Display Preferences dialog lists many very low resolution modes that are not listed in xorg.conf and does not list all high resolution modes listed in xorg.conf. There is the "Default" item in the list and I suppose it is the highest resolution listed in xorg.conf, but that resolution is not listed elsewhere in the list of the dialog. Why are lists so different? How can I get the resolutions listed in xorg.conf to the dialog's list and get rid of those useles low resolution items?

try changing the horizontal rates and vertical rates in xorg.conf...

also, try adding this option to your device section (if you are using an ATI card):

[PHP]Option "DDCMode" "true"[/PHP]

---

### Post by jis on 2006-09-10
I have "Matrox Graphics, Inc. MGA G400 AGP", AFAIK.

I have H Freq/ V Freq: 30-70 khz / 50-120 hz. The modes I use in GUI are fine. What values do you suggest?

---

### Post by Ziox on 2006-09-10
I don't know if i'll continue to post in both threads, but...

I would suggest something like this:

HorizSync       30-65
        VertRefresh     50-75

---

### Post by jis on 2006-09-10
I ran "sudo ddcprobe" and it gives this output:

```
vbe: VESA 3.0 detected.
oem: Matrox Graphics Inc.
vendor: Matrox
product: Matrox G450 00
memory: 32768kb
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 640x400x256
mode: 800x600x16
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 132x43 (text)
edid:
edid: 1 1
id: 7752
eisa: MAG7752
serial: f900024e
manufacture: 50 1997
input: sync on green, analog signal.
screensize: 33 24
gamma: 2.700000
dpms: RGB, active off, suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@60
ctiming: 1024x768@85
ctiming: 800x600@85
ctiming: 640x480@85
dtiming: 1024x768@104
dtiming: 800x600@85
monitorname: MAG DJ707
monitorrange: 30-70, 50-120

```

I wonder why 1152x864 is not listed although I use it successfully as default mode.

---

