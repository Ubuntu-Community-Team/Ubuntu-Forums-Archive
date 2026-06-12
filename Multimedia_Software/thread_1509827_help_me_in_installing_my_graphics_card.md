---
title: "help me in installing my graphics card"
date: 2010-06-14
forum: Multimedia Software
---

### Post by the_storm on 2010-06-14
hey guys, 
i tried to install my graphics card but  i couldn't 
can anyone tell me how to install my Graphics card correctly 
note : when I type 
```
gedit /etc/X11/xorg.conf 
``` I see an empty file  
and the file xorg.conf is not exist 

and this is the output of the command ```
lspci
``````
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```I am  waiting for ur help guys 
thanks in advance :popcorn:

---

### Post by ShadowTek on 2010-06-14
> i tried to install my graphics card but  i couldn't Do you mean that you couldn't physically get your graphics card installed, or what?


> I see an empty file  
and the file xorg.conf is not exist If there is not xorg.conf, then the default settings for xorg will be used.


The following will tell you what the default settings are:
```
man xorg.conf
```

---

### Post by the_storm on 2010-06-14
> **ShadowTek said:**
> Do you mean that you couldn't physically get your graphics card installed, or what?


If there is not xorg.conf, then the default settings for xorg will be used.


The following will tell you what the default settings are:
```
man xorg.conf
```


No i mean that when i am working on Ubuntu a message appears from time to time telling me that the graphics card is not correctly installed and the system will work on low graphic mode 
and also i couldn't use any of visual affects when i try to put the visual affects on normal computer tells me "Desktop effects could not be enabled"
Why all this ?

---

### Post by the_storm on 2010-06-15
Any help guys ??

---

### Post by dabl on 2010-06-15
Which version of Ubuntu are you trying to use?  Did you try a Live CD before installing?  How did it work with your Intel video chip?

This is your chip:

> 00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

If you search this forum, with "intel 82g33/g31" you should find many threads about that chip.

---

### Post by beowulf1416 on 2010-06-15
i have the same intel vga chip for graphics as you do and i'm not having any problems. I couldn't enable desktop effects because the chip doesn't support it so no compiz for me too. i'm assuming you are on a laptop? try searching for reviews on that laptop, maybe it has issues.

---

