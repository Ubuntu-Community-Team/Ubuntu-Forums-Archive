---
title: "NVIDIA driver issue?"
date: 2011-11-26
forum: Multimedia Software
---

### Post by Mastiff37 on 2011-11-26
I'm trying to get an old desktop to run Ubuntu and display on my HDTV via VGA cable.  I just installed Ubuntu yesterday and it works fine on my LCD monitor, but when I go to the HDTV it says the display type is unknown and will only allow 640x480 resolution.  NVIDIA drivers are installed and active.  I have tried both the recommended and newest versions.

The fishy thing is when I check the nvidia-settings, under configurations I get:

```
Unable to load X Server Display Configuration page:
Failed to query NoScanout for screen 0.
```

I've seen a lot of posts about this and it seems like some people have successfully worked around this problem, but I still don't really understand what to do.  Can anyone walk me through this?  I looked in xorg.conf and I don't see any reference to nvidia at all.  I think if it's right it should specify that for the driver, right?

---

### Post by inobe on 2011-11-26
try opening nvidia settings with you computer monitor connected.

---

### Post by Mastiff37 on 2011-11-26
Same error screen, but I do have all my resolution settings available. :confused:

---

### Post by emagine1 on 2011-11-28
Try This.

- Open nvidia X server settings GUI
- Go in X server Display Configuration
- In Model select TV-0
- In configuration select Twin View
- in resolution select auto
- In position :  Clones (if support clone) or absolute +0+0 if not
- Save to  X Configuration File
- Save in your HOME directory

- Go to terminal and type: sudo gedit /home/[username]/[filename].backup

Your file like this:

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Monitor"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1360x768_60 +0+0, TV-0: NULL"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Add this lines to Screen section if your connection is component (view options in [http://us.download.nvidia.com/XFree86/Linux-x86_64/173.08/README/chapter-16.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.08/README/chapter-16.html))

    Option         "ConnectedMonitor" "CRT-0, TV-0"
    Option         "TVOutFormat" "COMPONENT"
    Option         "TVStandard" "HD720p"

Like this:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "ConnectedMonitor" "CRT-0, TV-0"
    Option         "TVOutFormat" "COMPONENT"
    Option         "TVStandard" "HD720p"
    Option         "metamodes" "CRT-0: 1360x768_60 +0+0, TV-0: NULL"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Save file


Open terminal  and type: 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back1
(backup is valued!!!!)

sudo cp ~/[filename].backup etc/X11/xorg.conf

Make log off (restart Xserver)

Make login. If in clone mode your TV is working. If not:

- Open Nvidia X server settings
- X server Display configs
- In your monitor select resolution off
- In your TV select auto or resolution desired
- Click on Apply.

My post: [http://ubuntuforums.org/showthread.php?t=1883603](http://ubuntuforums.org/showthread.php?t=1883603)

---

### Post by emagine1 on 2011-11-28
Sorry my english

---

### Post by Mastiff37 on 2011-11-29
Thanks much for the help, I'll give this a shot.

---

