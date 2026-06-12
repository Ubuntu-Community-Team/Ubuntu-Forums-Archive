---
title: "help for wide screen resolution"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by june8th on 2006-08-08
Hello,
I have new machine has following spec.

Monitor: Dell 2005FPW (optimum resolution is 1650x1050)
Graphics: Intel 945G chipset.
Connection: DVI-D

I installed Dapper and tried many suggestions from googling.
915resolution package is installed, and xorg.conf is modified.

But I didn't get the real 1650x1050 resolution.
Instead of that, I have panning 1650x1050 resolution.

I attached my current config. I tried many variations of these.
If anyone has working configuration for similar system, let me know it.
Thank you. 

-----------------------------
more /etc/default/915resolution
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=54
#
# and set resolutions for the mode.
#
XRESO=1680
YRESO=1050
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=24
--------------------------------------------
Section "Device"
        Identifier      "Intel Corporation 945G Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "ForceBIOS" "1024x768=1650x1050"
EndSection

Section "Monitor"
        Identifier      "DELL 2005FPW"
        Option          "DPMS"
        HorizSync 30-83
        VertRefresh 60
        Modeline "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 945G Integrated Graphics Controller"
        Monitor         "DELL 2005FPW"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050@60" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection

EndSection
---------------------------------------

---

### Post by june8th on 2006-08-08
Finally I got solution.Use vesa driver instead of i850.
I'm not sure this is the best, but have beautiful screen right now.

---------------------------
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=38
#
# and set resolutions for the mode.
#
XRESO=1680
YRESO=1050
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=
-----------------------------
Section "Device"
        Identifier      "Intel Corporation 945G Integrated Graphics Controller"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection

....

---

### Post by HwyXingFrog on 2006-08-15
I am having the exact same issue as you.  Although I am on a new Dell Latitude D820 Laptop with the Movile Intel(R) 945GM Express Chipset Family for video.  It also has an optimum resolution of 1680x1050, and I have the same scrolling issues.

But when I tried your (non reccomended) way of getting around the issue, my login screen was perfect but every time I tried it kept booting me out.

I had to login under the console and change it back to i815, so it still sucks and my issue has yet to be resolved.

---

### Post by tseliot on 2006-08-15
Try installing this 915resolution:
```
sudo apt-get install 915resolution
```

---

### Post by HwyXingFrog on 2006-08-17
> **tseliot said:**
> Try installing this 915resolution:
```
sudo apt-get install 915resolution
```

I did exactly that to install it, and it didn't work.

---

