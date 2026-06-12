---
title: "monitor not detected."
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2010-10-07
i have installed maverick and the monitor is not detected when i use the default nouveau drivers however it is detected when i use the nvidia-current driver. 

i would really like to text the nouveau drivers how do i get it to detect my monitor. 

when i use the nouveau drivers it detects and load 1280x1024 but the screen is in the center of monitor (i have about 1" all sides just black but with the nvidia drivers i get full screen and screen res upto 1900 and something x 1080. 

any ideas thanks

---

### Post by cariboo on 2010-10-07
Check the monitor frequency is System->Preferences->Monitors.

I had the same problem with Win 7 and Maverick. Setting the frequency to 85Hz solved the problem in both oses.

---

### Post by terry_gardener on 2010-10-08
it didn't list any frequency to choose from

---

### Post by lancest on 2010-10-08
My monitor can't get past plymouth using the Nouveau driver. 
Black screen.

---

### Post by ssam on 2010-10-09
could either of you try to get the /var/log/messages file from when the machine does not detect the monitor.

if you can't get it to log in at all the easist way might be to load a live cd after, and get the file.

i am wondering if it is related to invalid EDID information, and my issue [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601376](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/601376)

---

### Post by MacUntu on 2010-10-09
Install the package 'x11-xserver-utils' and run ```
xvidtune -show
``` when running the Nvidia driver. Then simply copy the output to the Monitor section of your xorg.conf, eg.:```
[...]

Section "Monitor"
    [...]
    Modeline        "1280x1024_75" 135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
    Option          "PreferredMode" "1280x1024_75"
EndSection

[...]
```

---

