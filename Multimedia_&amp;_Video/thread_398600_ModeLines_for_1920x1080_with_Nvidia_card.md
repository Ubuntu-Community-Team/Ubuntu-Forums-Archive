---
title: "ModeLines for 1920x1080 with Nvidia card"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by bsharitt on 2007-04-01
Alright, I just installed the Feisty beta and am trying to set up X for a 1920x1080 resolution. The video card is an nVidia GeForce 7300GS 256MB card. The monitor is a 20" Sceptre x20 Naga, 16:9 aspect ratio. The connection is DVI. I installed the driver with the new restricted drivers manage in Feisty. I have attached my xorg.conf file and Xorg.0.log file. The screen is currently running at 1360x768. Previously I was using a Radeon x1300 and fglrx drivers with the same setup and it ran at 1920x1080 just fine. In fact, the ATI card didn't even have the resolution in the xorg.conf, it just defaulted to it anyway. So I know the monitor is capable of it. With the nVidia card, I have Windows Vista running at 1920x1080 very smoothly. Can anyone point out what I'm doing wrong and maybe what I can do to fix the situation?

---

### Post by tseliot on 2007-04-01
Type:
```
sudo nvidia-settings
```

and set the resolution from there

---

### Post by bsharitt on 2007-04-01
> **tseliot said:**
> Type:
```
sudo nvidia-settings
```

and set the resolution from there

There's not setting for 1920x1080 there either, hence all the modelines and stuff.

---

### Post by tseliot on 2007-04-01
Ok, you can create a new modline by typing:
```
gtf 1900 1080 60
```

(60 stands for 60Hz refresh rate)

Add the result (such as the following) to the Section Screen of your xorg.conf
```
# 1904x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 171.72 MHz
  Modeline "1904x1080_60.00"  171.72  1904 2024 2232 2560  1080 1081 1084 1118  -HSync +Vsync

```

then restart the Xserver

---

### Post by CrazyBoyD on 2007-04-01
I'm having the same problem.  I just got a TV that has 1920x1080 native resolution, but even with this as the only mode in my xorg.conf, it just gives me 1400x1050 instead.  Any ideas on why this would be?

---

### Post by Zimmer on 2007-04-01
Have a look at post #3 here

[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

and see if that helps you obtain a correct modeline statement for your hardware...

---

