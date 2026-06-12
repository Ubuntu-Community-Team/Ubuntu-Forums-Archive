---
title: "no output after changing vga cable"
date: 2008-07-02
forum: Multimedia Software
---

### Post by alexao on 2008-07-02
I have a setup with two lcd monitors, where one of them is a tv with a 1360x768 resolution. Today I changed the VGA cable from my computer to the tv from a 1 metre cable to a 10 metre one, and now the setup suddenly does not work (get no output). I have not changed my xorg.conf settings. 

I do however get an output in console and in windows. During the Ubuntu startup screen I do not get an output. 

UPDATE: I should add that it works if I boot up with the 1 metre cable, and then change over to the 10 metre one. However it does not work if I start up X with the 10 metre cable. Have also tried adding options in the xorg like Ignore EDID

Any ideas what is causing this problem?

---

### Post by alexao on 2008-07-03
Changing the xorg.conf file entry for the monitor that is the tv, to this:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync 30.0 - 61.0
    VertRefresh 60.0 - 75.0
    ModeLine "1360x768" 85.5 1360 1416 1528 1792 768 771 777 795
    Option "dpms"

fixed the problem

---

