---
title: "Ubuntu nvidia 8500GT and 1920x1080 ?"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by timdf911 on 2007-12-09
Hi,
I'm a recent convert from Fedora to Ubuntu and I must say I'm impressed with Ubuntu - despite the 'usual' nvidia driver drama ;-)

So here's my problem which despite much googling and searching this site - I'm still puzzled.

I have a fresh install of Mythubuntu  Gutsy 7.10 with a 8500GT video card and driver 100.14.19.  I've installed the restricted drivers and can select a resolution of 1920x1200 right down to vga no problem.  My display is a Samsung 24 inch 245BW and all works well.

However I also need to get 1920x1080 working to drive the family room Sharp 45" flat screen via the DVI output to either the HDMI or DVI input on the Sharp .

I've tried editing xorg.conf adding extra modelines and metamodes but to no effect - either they have no impact or corrupt the xorg.conf file.

With my Sharp 45" HDTV the best I can get is 1024x768 via DVI or 1280x720 via HDMI - no sign of the elusive 1920x1080.  I'm beginning to think it's something to do with the 8500 GT and HDCP (or lack off)  resulting in the Sharp throttling back the resolution.

Maybe time to buy a different video card ?

Here's my latest xorg.conf file - any suggestions ?

BTW I've tried Envy, but no driver I've found will give me a 1920x1080 option.

I have an 8800 running under Vista and that driver gives me a range of resolutions - including 1920x1080.  The 8500 is supposed to support HDTV 1920x1080, but just can't find the right combo of drivers and settings :-(

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

