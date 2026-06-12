---
title: "nvidia TV out color out for svideo fix for black white only display"
date: 2009-11-23
forum: Multimedia Software
---

### Post by sdowney717 on 2009-11-23
I was having trouble using svideo out and color on the TV. the picture was black and white. The output was in color when using a s video to composite adapter, but running a straight svideo cable yielded B+W 

adding the line in xorg.conf

           Option "TVStandard" "NTSC-M"

in Section made the svideo output color to the TV. This is on an older card mx4000, running the last driver nvidia has made 96 something.


Section "Device"
Identifier "Videocard1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce4 MX 4000"
Option "TVStandard" "NTSC-M"
EndSection

---

### Post by doas777 on 2009-11-23
> **sdowney717 said:**
> I was having trouble using svideo out and color on the TV. the picture was black and white. The output was in color when using a s video to composite adapter, but running a straight svideo cable yielded B+W 

adding the line in xorg.conf

           Option "TVStandard" "NTSC-M"

in Section made the svideo output color to the TV. This is on an older card mx4000, running the last driver nvidia has made 96 something.


Section "Device"
Identifier "Videocard1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce4 MX 4000"
Option "TVStandard" "NTSC-M"
EndSection

some folks may also need to add a line like:

```
option "TVOutFormat" "SVIDEO"
```. it can also take "COMPOSITE" as an argument. I have not needed this in a long time (I'm thinking feisty or hardy was last).

---

### Post by sdowney717 on 2009-11-23
i tried the composite line and it left it B+W

---

