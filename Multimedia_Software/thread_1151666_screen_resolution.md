---
title: "screen resolution"
date: 2009-05-07
forum: Multimedia Software
---

### Post by gjohnno on 2009-05-07
How do I change my screen resolutions to be 1024 x 780.

My video card is a GEFORCE 6200

I have run xrandr by the terminal and the following resulted
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   576x432        51.0  
   512x384        52.0  
   400x300        53.0     54.0     55.0  
   320x240        56.0  .

Your assistance will be appreciated

Thank you

---

### Post by eternalnewbee on 2009-05-07
> **gjohnno said:**
> How do I change my screen resolutions to be 1024 x 780.

My video card is a GEFORCE 6200

I have run xrandr by the terminal and the following resulted
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   576x432        51.0  
   512x384        52.0  
   400x300        53.0     54.0     55.0  
   320x240        56.0  .

Your assistance will be appreciated

Thank you
Is your video card enabled?

---

### Post by gjohnno on 2009-05-07
This may sound like a dumb question how do I tell if my video card is enables

---

### Post by gandaran on 2009-05-07
> **gjohnno said:**
> This may sound like a dumb question how do I tell if my video card is enables
did you install the nvidia driver in system » administration » hardware drivers?

---

### Post by eternalnewbee on 2009-05-07
Go to Main Menu > System > Administration > Hardware Drivers.

---

### Post by gjohnno on 2009-05-07
NVIDIA accelerated graphics driver (version 180) (Recommended)

( green light) The driver is activated and currently in use

---

### Post by eternalnewbee on 2009-05-07
You should be able to change your screen resolution under Screen Resolution, under Main Menu > System > Preferences

---

### Post by CatKiller on 2009-05-07
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.


I've also recently discovered a way to stop the NVidia driver from lying about the refresh rates. Put 
```

        Option          "DynamicTwinView"               "False"

``` in the "Device" Section.

---

