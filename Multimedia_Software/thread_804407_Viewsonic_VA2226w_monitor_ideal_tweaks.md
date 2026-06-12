---
title: "Viewsonic VA2226w monitor ideal tweaks"
date: 2008-05-23
forum: Multimedia Software
---

### Post by ebike on 2008-05-23
Hi all,

I have a Viewsonic VA2226w monitor with the following settings in xorg.conf

> 
Section "Monitor"
        Identifier      "Configured Monitor"
        Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Defaultdepth    24
        Device          "Configured Video Device"
        SubSection     "Display"
                Depth       24
                Modes      "1680x1050_60.00"
        EndSubSection
EndSection


Although the resolution is fine, the fonts look a bit thin and the color is a bit washed out (I can correct that in the monitor a little, by setting color to 5600k (warm))

Can anyone suggest settings to get the color right in the xorg.conf file?
(Gamma setting maybe ??)

Thanks.

---

### Post by ebike on 2008-05-24
Bump, Anyone?

---

### Post by prshah on 2008-05-26
> **ebike said:**
> 
Although the resolution is fine, the fonts look a bit thin and the color is a bit washed out (I can correct that in the monitor a little, by setting color to 5600k (warm))

Apparently the slightly washed out colors are a known problem in this particular model; it's presented as a budget model, so I guess you're going to have to live with it..

---

