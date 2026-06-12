---
title: "NVIDIA FX 5200 Dapper"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by antilog on 2006-07-28
I followed the instructions for Method 1 @ [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

and am not able to startx.  I get a bluescreen with ASCII box and an error.

The following is a list of errors and warnings picked out from the Xorg.0.log

```
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) (1280x960,DELL 1704FPV) mode clock 148.5MHz exceeds DDC maximum 140MHz
(WW) (1280x1024,DELL 1704FPV) mode clock 157.5MHz exceeds DDC maximum 140MHz
```

Any ideas??

---

### Post by tseliot on 2006-07-29
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

---

### Post by sabredog on 2006-07-29
I would suggest that once you get a desktop back again by foullowing the above, use Automatix to install the Nvidia drivers.

I have a 128Mb FX5200 and I used Automatix to install the Nvidia drivers. All worked well.

---

### Post by tseliot on 2006-07-29
> **sabredog said:**
> I would suggest that once you get a desktop back again by foullowing the above, use Automatix to install the Nvidia drivers.

I have a 128Mb FX5200 and I used Automatix to install the Nvidia drivers. All worked well.

Automatix uses method 1.

He should try point 4 of the Problems Section instead.

---

