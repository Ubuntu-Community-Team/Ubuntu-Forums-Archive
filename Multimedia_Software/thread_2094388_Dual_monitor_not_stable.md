---
title: "Dual monitor not stable"
date: 2012-12-13
forum: Multimedia Software
---

### Post by amir_pasha on 2012-12-13
I have Ubuntu 10.04 on my laptop (Inspiron 6000) and I wanted to connect it to a second monitor via VGA cable. The screen I am using is HP L1950g. When I connect it to the laptop and set up the dual monitor the screen can't get stable the screen goes blank and then appears again (like going on and off). In "monitors" section the second monitor named "Unknown". I tested another monitor HP L1950 (don't know the difference between L1950 and 1950g) it works perfectly and Ubuntu recognized the screen as "Hewlett Packard 19" ". I tried to change the "Horizontal Frequency" and "Vertical Refresh Rate" on /etc/X11/xorg.conf  according to the manual [here]("http://bizsupport1.austin.hp.com/bc/docs/support/SupportManual/c01555675/c01555675.pdf") but nothing has changed:

```
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync       24.0 - 83.0          # you have to enter your specific values here
    VertRefresh     50.0 - 77.0         # see guides below
    Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync Option
    "PreferredMode" "1280x1024_60.00"
EndSection
```anybody knows what could possibly be the reason?

---

### Post by dannyboy79 on 2012-12-13
is the graphics card a ATi Mobility Radeon X300? which drivers are you using?

---

### Post by amir_pasha on 2012-12-13
> **dannyboy79 said:**
> is the graphics card a ATi Mobility Radeon X300? which drivers are you using?
yes that's right
I don't know how to find out the drivers but I guess it is the default ubuntu drivers
this is the output from glxinfo | grep -i vendor
```
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: DRI R300 Project
```

is that what you mean?

---

### Post by dannyboy79 on 2012-12-13
do you have an xorg.conf file located at /etc/X11/? if so, what is listed as the Driver within the Device section

---

### Post by amir_pasha on 2012-12-13
> **dannyboy79 said:**
> do you have an xorg.conf file located at /etc/X11/? if so, what is listed as the Driver within the Device section

the "Device" section in xorg.conf says:
```
Section "Device"
    Identifier  "Card0"
    Driver      "ati"
EndSection
```

---

### Post by dannyboy79 on 2012-12-13
you could try this out. [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X300](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X300)

try at your own risk.

---

### Post by amir_pasha on 2012-12-13
Do you mean to replace the Device section in xorg.conf with the content proposed there?
or install the fglrx driver?

---

