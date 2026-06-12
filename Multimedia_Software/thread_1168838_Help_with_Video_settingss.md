---
title: "Help with Video settingss"
date: 2009-05-24
forum: Multimedia Software
---

### Post by Imoen on 2009-05-24
lspci:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
```


lshw
```
*-display:0 UNCLAIMED
 description: VGA compatible controller
 product: RV530 [Radeon X1600]
 vendor: ATI Technologies Inc
 physical id: 0
 bus info: pci@0000:01:00.0
 version: 00
 width: 64 bits
 clock: 66MHz
 capabilities: bus_master cap_list
```

xorg.conf:
```
Section "Monitor"
 Identifier	"Configured Monitor"
EndSection

Section "Screen"
 Identifier	"Default Screen"
 Monitor		"Configured Monitor"
 Device		"Configured Video Device"
EndSection

Section "Device"
 Identifier	"Configured Video Device"
 Option		"UseFBDev"		"true"
EndSection

Section "ServerFlags"
 Option	"DontZap"	"True"
EndSection
```

Video Card Specs:
 Display Modes
        * Digital Displays (Connected by DVI)
              o All Resolutions up to 2560x16003
        * Analog Displays (Connected by VGA)
              o All resolutions up to 2048x15363
        * TV-out
              o SDTV (analog): 480i | 525i
              o HDTV (analog or digital): 480p | 720p | 1080i | Any custom resolution3

Monitor Support:
          Resolution------Horizontal----Vertical     
Mode-------Frequency------Frequency----Frequency----Pixel
VGA--------640 x 480------31,469KHz------60Hz------25,175MHz
VGA--------640 x 480------37,861KHz------72Hz-------31,50MHz
VGA--------640 x 480-------37,50KHz------75Hz-------31,50MHz
SVGA-------800 x 600------35,156KHz------56Hz-------36,00MHz
SVGA-------800 x 600------37,879KHz------60Hz-------40,00MHz
SVGA-------800 x 600------48,077KHz------72Hz-------50,00MHz
SVGA-------800 x 600------46,875KHz------75Hz-------49,50MHz
XGA-------1024 x 768------48,363KHz------60Hz-------65,00MHz
XGA-------1024 x 768------56,476KHz------70Hz-------75,00MHz
XGA-------1024 x 768-------57,70KHz------72Hz-------78,40MHz
XGA-------1024 x 768------60,023KHz------75Hz-------78,75MHz
Mac-------1152 x 864--------67,5KHz------75Hz------108,00MHz
Mac-------1280 x 960----------60KHz------60Hz------108,00MHz
WXGA------1280 x 800------49,702KHz------60Hz--------83.5MHz
WXGA------1280 x 800------62,795KHz------75Hz-------106.5MHz
SXGA-----1280 x 1024------63,981KHz------60Hz------108,00MHz
SXGA-----1280 x 1024--------74,4KHz------70Hz-------124,9MHz
SXGA-----1280 x 1024--------77,9KHz------72Hz-------134,6MHz
SXGA-----1280 x 1024------79,976KHz------75Hz------135,00MHz
WXGA+-----1440 x 900------55,935KHz------60Hz-------106,5MHz
WXGA+-----1440 x 900------70,635KHz------75Hz------136,75MHz    
WSXGA----1680 x 1050-------65,29KHZ------60Hz------146.25MHz

I would like to have the largest screen size possible without flashing pixels or really poor/slow performance. Right now the performance is terrible, everything lags and when booting up I see nothing but "out of range" displayed so I just have to wait and assume that it isn't saying any error messages since I wouldn't see them.

---

### Post by aussieboy on 2009-05-26
I had similar problems with an NVidia card and had to edit the xorg.cnf file in X11.
Your xorg.cnf needs to contain the relevant numbers for the screen sizes supported 
in "Monitor" - specifically change my HorizSync and VertRefresh settings to those your monitor supports, Get the correct modeline entries (use EnvyNG if necessary).
Also, change the Virtual line in "Screen" secrtion to reflect your maximum screen size. Mine says 1024 768 (below)
The Modes command in "Screen" should match the number and value of the modeline commands in t he "Monitor" setcion.

Hope this helps - Good Luck.
The appropriate section of my xorg.cnf follows and gives you an idea of what should be in it.


Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Plug 'n' Play"
    Modelname    "Plug 'n' Play"
    HorizSync       31.5-80
    VertRefresh     56.3-75.1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1024    768
        Modes        "1024x768@60"    "800x600@60"    "800x600@56"    "640x480@60"
    EndSubSection

---

### Post by Imoen on 2009-06-02
I installed EnvyNG and restarted as it says to and now I have a screen that looks like zebra print. I can't see anything to uninstall the program at all. How can I fix this? Please help me to go back to what it was before, I didn't realize that to get the video settings would cause this to happen.

---

### Post by xc3RnbFO8P on 2009-06-02
Start the computer in Recovery mode, and run **xfix**

---

