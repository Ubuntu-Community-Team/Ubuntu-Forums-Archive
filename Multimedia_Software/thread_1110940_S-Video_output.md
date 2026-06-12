---
title: "S-Video output"
date: 2009-03-30
forum: Multimedia Software
---

### Post by JKoder on 2009-03-30
Hello everyone. Currently i have Ubuntu 9.04 ( I know it;s beta ) installed and i am wondering how can i get the S-Video to work without installing ATI Drivers.
Before i had openSuSE (sorry for mentioning , i know thi si ubuntu forum ) and id succsesfuly detected my card using open source driver.
Now in either distro i was not able to make my S-Video to work without proprietary drives.
Is this even possible ?
Thank you.

---

### Post by NT4usB on 2009-03-30
There are some things you can add to xorg.conf might make it work... TVOutFormat, TVStandard, etc.
This is a clip from my MythTV xorg. May be deprecated now. Read the man pages?
```
Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "Component" # or SVIDEO Composite etc...
    Option         "TVStandard" "HD480i" # or "NTSC" etc.
    Option         "ConnectedMonitor" "Monitor[1]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60" "720x576_60" "720x480_60" "640x480_60" "480x320_60"
    EndSubSection
EndSection
```

---

