---
title: "configuring an acer AL1714 monitor to have a reasonnable resolution"
date: 2009-07-28
forum: Multimedia Software
---

### Post by sdenel on 2009-07-28
Hello everybody!
I need your help. Here is my problem:

I have got an nvidia NV37GL [Quadro FX 330/GeForce PCX 5300] graphix card, with an acer AL1714 monitor.
And I can't get a better resolution than 800*600! Even If can have a 1024*768 resolution with:
-Windows and this screen
-Ubuntu but another screen

I tried to install prioritary drivers: both 96 and 173 nvidia drivers gave me an even lower resolution (Yes, it is possible! a 640*480 at maximum...)

I already tried to solve my problem by myself, following this guide:
[https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Dynamically%20testing%20different%20resolutions")

But here is the result:
> $ cvt 1024 768 50
# 1024x768 49.98 Hz (CVT 0.79M3) hsync: 39.63 kHz; pclk: 52.00 MHz
Modeline "1024x768_50.00"   52.00  1024 1072 1168 1312  768 771 775 793 -hsync +vsync

$ xrandr --newmode "1024x768_50.00"   52.00  1024 1072 1168 1312  768 771 775 793 -hsync +vsync

$ xrandr --output default --mode 1024x768_50.00
xrandr: cannot find mode 1024x768_50.00

$ xrandr --addmode default 1024x768_50.00

$ xrandr --output default --mode 1024x768_50.00
**xrandr: Configure crtc 0 failed**I think that the modeline gave by cvt is wrong and I also think that refresh information must be taken in the windows driver file. But I don't know where those informations are!
Here is the content of this .inf driver:
> 
;AL17xx.INF Ver. 2.0 
;Monitor INF file for Acer Incorporated Monitor AL17xx 
;Copyright 2003 Acer Incorporated 
 
[Version] 
signature="$CHICAGO$" 
Class=Monitor 
ClassGuid={4D36E96E-E325-11CE-BFC1-08002BE10318} 
Provider=%Acer% 
CatalogFile=Acer.cat 
DriverVer=12/08/2003, 2.0.0.0 
 
[ControlFlags] 
ExcludeFromSelect.nt=Monitor\ACR02DC 
 
[ClassInstall32] 
AddReg=ClassAddReg32 
 
[ClassAddReg32] 
HKR,,,,%MonitorClassName% 
HKR,,Icon,,"-1" 
HKR,,NoInstallClass,,1 
 
[DestinationDirs] 
DefaultDestDir=11 
AL17xx.CopyFiles=23 
 
[SourceDisksNames] 
1=%DISK%,,, 
 
[SourceDisksFiles] 
776.ICM=1 
 
[Manufacturer] 
%Acer%=Acer 
 
[Acer] 
%AL17xx%=AL17xx.Install, Monitor\ACR02DC 
 
[AL17xx.Install] 
DelReg=DEL_CURRENT_REG 
AddReg=AL17xx.AddReg, 1280, DPMS 
CopyFiles=AL17xx.CopyFiles 
 
[DEL_CURRENT_REG] 
HKR,MODES 
HKR,,MaxResolution 
HKR,,DPMS 
HKR,,ICMProfile 
 
[1280] 
HKR,,MaxResolution,,"1280,1024" 
 
[DPMS] 
HKR,,DPMS,,1 
 
[AL17xx.AddReg] 
HKR,"MODES\1280,1024",Mode1,,"30-80,56-75,+,+" 
HKR,,ICMProfile,0,"776.ICM" 
 
[AL17xx.CopyFiles] 
776.ICM 
 
[Strings] 
DISK="Driver & Utility for Acer AL17xx" 
MonitorClassName="Monitor" 
Acer="Acer Incorporated" 
AL17xx="Acer AL17xx"
So: Is any able to help me? Thanks a lot for your help,
Simon.

---

### Post by matttennant on 2009-07-28
I'd like the answer to this, too.  Bump.

---

### Post by igorzwx on 2009-07-28
report this bug

but you may find it is already there (among bugs)

---

### Post by sdenel on 2009-07-29
Well, it would be a bug from Ubuntu, but anyway I pretty sure that an experiment user would help you to solve our problem within 5 minutes: I think we just need to know which parameters setting in the Modeline line.

---

### Post by sdenel on 2009-07-29
Solved! :D
The solution is to modify the xorg.conf and to replace screen and monitor sections with that:
> 
Section "Monitor"
    Identifier   "Monitor0"
    ModelName    "Acer AL1714"
    HorizSync    30.0 - 82.0
    VertRefresh  50.0 - 75.0
    Option        "dpms"
        Modeline "1280x1024_60.00"  108.00  1280 1328 1440 1688  1024 1025 1028 1066  +HSync +Vsync
#    Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync

EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    Monitor    "Monitor0"
    DefaultDepth     24
    Option        "UseEdid" "False"
    SubSection "Display"

        Depth     24
    Modes    "1280x1024" "1280x960" "1280x800" "1152x864" "1280x768" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
found on this forum thread: [http://forums.fedoraforum.org/archive/index.php/t-191198.html](http://forums.fedoraforum.org/archive/index.php/t-191198.html)
Thank you to have tried to help me!



**OR**, another solution that allows you to have 2D acceleration is to use nouveau driver:
sudo apt-get install xserver-xorg-video-nouveau

sudo gedit /etc/X11/xorg.conf
add: Driver "nouveau" to the Device section.
NOT all the lines above.

Restart: **enjoy**!

---

