---
title: "What ATI chipsets are supported by the open source drivers?"
date: 2010-01-30
forum: Multimedia Software
---

### Post by Talon2 on 2010-01-30
I'm looking to buy an ATI card (PCIe x16) so I can run dual monitors.  The box has Intel integrated only right now.

I'm having a hard time figuring out what ATI chipsets are supported by the open source Radeon and RadeonHD drivers.  I'm running 9.10 and would prefer Compiz support et al.  The information I am finding seems to be dated.  Any help locating current information appreciated.

---

### Post by sports.car.guy on 2010-01-31
> **Talon2 said:**
> I'm looking to buy an ATI card (PCIe x16) so I can run dual monitors.  The box has Intel integrated only right now.

I'm having a hard time figuring out what ATI chipsets are supported by the open source Radeon and RadeonHD drivers.  I'm running 9.10 and would prefer Compiz support et al.  The information I am finding seems to be dated.  Any help locating current information appreciated.

Compiz is supported by fglrx as well. Is there a particular reason you are wanting the open source driver?

---

### Post by Yellow Pasque on 2010-01-31
From the man pages...
```
SUPPORTED HARDWARE
       The radeonhd driver supports video cards based on the following ATI chips:

       RV505   Radeon X1550, X1550 64bit
       RV515   Radeon X1300, X1550, X1600; FireGL V3300, V3350
       RV516   Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250
       R520    Radeon X1800; FireGL V5300, V7200, V7300, V7350
       RV530   Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200
       RV535   Radeon X1300, X1650
       RV550   Radeon X2300 HD
       RV560   Radeon X1650
       RV570   Radeon X1950, X1950 GT; FireGL V7400
       R580    Radeon X1900, X1950; AMD Stream Processor
       R600    Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650
       RV610   Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000
       RV620   Radeon HD 3450, HD 3470
       RV630   Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630; FireGL V3600/V5600
       RV635   Radeon HD 3650, HD 3670
       RV670   Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170
       R680    Radeon HD 3870 X2
       M52     Mobility Radeon X1300
       M54     Mobility Radeon X1400; M54-GL
       M56     Mobility Radeon X1600; Mobility FireGL V5200
       M58     Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200
       M62     Mobility Radeon X1350
       M64     Mobility Radeon X1450, X2300
       M66     Mobility Radeon X1700, X1700 XT; FireGL V5250
       M68     Mobility Radeon X1900
       M71     Mobility Radeon HD 2300
       M72     Mobility Radeon HD 2400; Radeon E2400
       M74     Mobility Radeon HD 2400 XT
       M76     Mobility Radeon HD 2600; (Gemini ATI) Mobility Radeon HD 2600 XT
       M82     Mobility Radeon HD 3400
       M86     Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700
       M88     Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2
       RS600   Radeon Xpress 1200, Xpress 1250
       RS690   Radeon X1200, X1250, X1270
       RS740   RS740, RS740M
       RS780   Radeon HD 3100/3200/3300 Series
       R700    Radeon R700
       RV710   Radeon HD4570, HD4350
       RV730   Radeon HD4670, HD4650
       RV740   Radeon HD4770. EXPERIMENTAL AND UNTESTED
       RV770   Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro
       RV790   Radeon HD 4890
       M92     Mobility Radeon HD4330, HD4530, HD4570. EXPERIMENTAL
       M93     Mobility Radeon M93. EXPERIMENTAL AND UNTESTED
       M96     Mobility Radeon HD4600
       M97     Mobility Radeon HD4860. EXPERIMENTAL AND UNTESTED
       M98     Mobility Radeon HD4850, HD4870
```

```
SUPPORTED HARDWARE
       The radeon driver supports PCI, AGP, and PCIE video cards based on the following ATI chips:

       R100        Radeon 7200
       RV100       Radeon 7000(VE), M6, RN50/ES1000
       RS100       Radeon IGP320(M)
       RV200       Radeon 7500, M7, FireGL 7800
       RS200       Radeon IGP330(M)/IGP340(M)
       RS250       Radeon Mobility 7000 IGP
       R200        Radeon 8500, 9100, FireGL 8800/8700
       RV250       Radeon 9000PRO/9000, M9
       RV280       Radeon 9200PRO/9200/9200SE/9250, M9+
       RS300       Radeon 9100 IGP
       RS350       Radeon 9200 IGP
       RS400/RS480 Radeon XPRESS 200(M)/1100 IGP
       R300        Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL X1/Z1
       R350        Radeon 9800PRO/9800SE/9800, FireGL X2
       R360        Radeon 9800XT
       RV350       Radeon 9600PRO/9600SE/9600/9550, M10/M11, FireGL T2
       RV360       Radeon 9600XT
       RV370       Radeon X300, M22
       RV380       Radeon X600, M24
       RV410       Radeon X700, M26 PCIE
       R420        Radeon X800 AGP
       R423/R430   Radeon X800, M28 PCIE
       R480/R481   Radeon X850 PCIE/AGP
       RV505/RV515/RV516/RV550
                   Radeon X1300/X1400/X1500/X2300
       R520        Radeon X1800
       RV530/RV560 Radeon X1600/X1650/X1700
       RV570/R580  Radeon X1900/X1950
       RS600/RS690/RS740
                   Radeon X1200/X1250/X2100
       R600        Radeon HD 2900
       RV610/RV630 Radeon HD 2400/2600
       RV620/RV635 Radeon HD 3450/3470
       RV670       Radeon HD 3850/3870
       RS780       Radeon HD 3100/3200/3300
       RV710       Radeon HD 4350/4550
       RV730       Radeon HD 4650/4670
       RV770       Radeon HD 4850/4870
```

---

### Post by Yellow Pasque on 2010-01-31
> **sports.car.guy said:**
> Compiz is supported by fglrx as well. Is there a particular reason you are wanting the open source driver?

The open source drivers run Compiz more smoothly, faster 2D, and are generally more stable. Of course, they're behind in 3D features, but they're catching up.

---

### Post by Melcar on 2010-01-31
Pretty much everything except Evergreen (r8xx).  Chips up to the r5xx (x1k) will work out of the box with full 2D and stable 3D acceleration; you won't get speed out of them and the drivers are only OpenGL1.5, but they're good enough to run most anything from composite managers (Compiz, Kwin, etc.), many open source games, and even some stuff with WINE.  R6xx (hd2k, hd3k) and r7xx (hd4k) chips will also work, but to get proper 3D acceleration with those you will need to update the drivers (either build them on your own or better yet use xorg-edgers packages), and a 2.6.32 or later kernel; the latest code will give you full 2D acceleration and 3D capable of OpenGL2.0.

---

### Post by asn_knight on 2010-01-31
but even with my ATI Rad 3650, desktop effects couldnot be enabled! What ya say to that?

---

### Post by Melcar on 2010-01-31
> **asn_knight said:**
> but even with my ATI Rad 3650, desktop effects couldnot be enabled! What ya say to that?

If you're using the open source drivers, you will need more recent code than what Karmic makes available (the driver version in Karmic only provides 2D for that class of chips).  The easiest way is to use packages from [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa"), and a recent kernel from the [kernel-ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").

---

### Post by Yellow Pasque on 2010-01-31
> **Melcar said:**
> If you're using the open source drivers, you will need more recent code than what Karmic makes available (the driver version in Karmic only provides 2D for that class of chips).  The easiest way is to use packages from [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa"), and a recent kernel from the [kernel-ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").
S/he would also need a >= 2.6.32 kernel. [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

