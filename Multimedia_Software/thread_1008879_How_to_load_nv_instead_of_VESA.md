---
title: "How to load nv instead of VESA?"
date: 2008-12-12
forum: Multimedia Software
---

### Post by heluani on 2008-12-12
I'm running ubuntu 2.6.27-9-server on a MacBook Air 2.1
```
$lspci 
VGA compatible controller: nVidia Corporation GeForce 9400M (rev b1)
```
and **don't** want to use the binary nvidia driver. Want to use the open source driver. 

I have installed xserver-xorg-video-nv but when I boot I get the VESA driver by default, well, I guess that from
```
$cat /var/log/Xorg.0.log
(II) VESA(0): Total Memory: 224 64KB banks (14336kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x720" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
.... 
```
It used to be the case that adding Driver "nv" to section "Device" in /etc/X11/xorg.conf would load the open source driver, but when I do that I just get an error when booting, and still just get the VESA driver... 

How can I force the nv driver? how can I check whether or not that driver is properly installed and/or running? 

Thanks

R.

Edit: Well, looking at Xorg.99.log I see that nv gets loaded, and then this horrible line comes up :)
```
(WW) NV: Ignoring unsupported device 0x10de0870 (GeForce 9400M) at 02@00:00:0 
``` and several like that... I guess I'll have to wait to use nv

---

### Post by kpkeerthi on 2008-12-12
> **heluani said:**
> Edit: Well, looking at Xorg.99.log I see that nv gets loaded, and then this horrible line comes up

(WW) **NV: Ignoring unsupported device 0x10de0870 (GeForce 9400M) **at 02@00:00:0

and several like that... I guess I'll have to wait to use nv

From the log, it appears that GeForce 9400M is not supported.

---

### Post by heluani on 2008-12-12
yes, anyway, the original problem I had was that I couldn't get 1280x800 on Vesa, but now I managed to get that resolution, the default Hsync and vrefresh values were wrong for my display... I guess I'll wait for the open source driver to support this card.

R.

---

### Post by rakris on 2008-12-12
Why not nvidia binary?

If you are very much open source, Use gNewSense instead of Ubuntu. :):)

---

