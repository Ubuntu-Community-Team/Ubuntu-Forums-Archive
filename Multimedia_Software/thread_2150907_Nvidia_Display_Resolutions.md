---
title: "Nvidia Display Resolutions"
date: 2013-06-02
forum: Multimedia Software
---

### Post by ironmaidenrule on 2013-06-02
Hi,

Got a strange issue with Display Resolutions from my Nvidia GTX GeForce 550 Ti.

I am using the current "Proprietry, Tested" Nvidia driver in the Additional Drivers section, however it is only allowing me to see two resolutions 1024x768 and another much higher one that makes the text really small. I have used xrandr and the other file in /etc/X11 to manually add new resolutions, however when switched to these resolutions my display produces a blank screen and says "Mode Not Supported", I would be happy to accept that my screen cannot display these resolutions, however I am using the same card and machine as a dual boot to Windows 8 and that can handle 1600x900 and many other resolutions fine.

Is there something specific with Ubuntu and Nvidia that produced a weird signal that my display cannot handle, but Windows does fine??

---

### Post by benzarti on 2013-06-02
Before adding modes in xorg.conf, you can test them :
 1) xrandr --newmode [modeline obtained by cvt xres yres]
 2) xrandr --addmode VGA1 "mode ex:1280x1024_60.00"
 3) xrandr --output VGA1 --mode 1280x1024_60.00
these modes can be 4:3, 5:4, 16:9, 16:10.
I hope that this help you!!!

---

### Post by SeijiSensei on 2013-06-02
Just to check that the NVIDIA driver is installed with the kernel please run

```
lsmod | grep -i nvidia
```

You should see the entry for the NVIDIA kernel module and its (large) size.

---

### Post by CatKiller on 2013-06-03
In Windows you'll have a "monitor driver" which is simply a list of resolutions your monitor can do, information that should be reported by the monitor through EDID. That's the difference.

Run your monitor at its native resolution and if the text is too small make it bigger. Running at non-native resolutions just looks bad.

---

### Post by ironmaidenrule on 2013-06-03
Thanks for the replies guys, just out of curiosity I connected my screen to the PC via VGA and I am now able to access the higher resolutions than I could in HDMI, seems very weird to me!

---

