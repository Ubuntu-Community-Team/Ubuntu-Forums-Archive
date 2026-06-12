---
title: "No output on 2ndd ATI card and fourth monitor"
date: 2012-12-20
forum: Multimedia Software
---

### Post by securitybreach on 2012-12-20
First off, thanks to[ [COLOR="Blue"]No-more-Restarts[/COLOR]]("http://ubuntuforums.org/showthread.php?p=12412801#post12412801") for giving me an outline of xorg.conf  from scratch for my 4 monitor/2 video card setup. 

I followed his guide and replaced the sections with my system's info but I am still having issues. I think the issue is the ServerLayout section but I am not really for sure. I would appreciate it if someone could take a look at my issue.

Here is the relevant information:

```
&#9556;&#9552; comhack@Cerberus 12:37 AM 
&#9562;&#9552;&#9552;&#9552; ~-> lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts LE [AMD Radeon HD 6700 Series]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450]
```

I ran xrandr and it shows the fourth monitor as:
```
DVI-1 disconnected (normal left inverted right x axis y axis)
```

Here is the entire xrandr output:
```
Screen 0: minimum 320 x 200, current 3520 x 2160, maximum 16384 x 16384
DisplayPort-0 connected 1920x1080+1600+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      59.9  
   1680x945       60.0  
   1400x1050      59.9  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI-0 connected 1920x1080+1600+1080 (normal left inverted right x axis y axis) 520mm x 290mm
   1920x1080      60.0*+   50.0     25.0     30.0  
   1600x1200      60.0  
   1680x1050      59.9  
   1680x945       60.0  
   1400x1050      74.9     59.9  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1280x720       50.0     60.0  
   1440x576       25.0  
   1024x768       75.1     70.1     60.0  
   1440x480       30.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   848x480        60.0  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
DVI-0 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0*+
   1440x900       75.0     59.9  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI-1 disconnected (normal left inverted right x axis y axis)
```
Also the second card looks like it has been identified per /etc/X11/xorg.conf.d/20-radeon-conf:
```
Section "Device"
Identifier "Device0"
Driver "radeon"
BusID "PCI:01:00.0"
EndSection

Section "Device"
Identifier "Device1"
Driver "radeon"
BusID "PCI:02:00.0"

Option "AccelMethod" "EXA"
```
Here is my old xorg.conf from Catalyst:
> Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "amdcccle-Screen[1]-0" 1599 1080
        Screen         "amdcccle-Screen[2]-0" 3520 0
        Screen         "amdcccle-Screen[1]-1" 0 0
        Screen         "amdcccle-Screen[1]-2" 1600 0
EndSection
 
Section "ServerFlags"
        Option      "Xinerama" "on"
EndSection
 
Section "Monitor"
        Identifier   "0-DFP1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection
 
Section "Monitor"
        Identifier   "0-DFP5"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection
 
Section "Monitor"
        Identifier   "0-DFP7"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1080"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection
 
Section "Monitor"
        Identifier   "1-DFP2"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1600x900"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection
 
Section "Monitor"
        Identifier   "0-DFP6"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1600x900"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection
 
Section "Device"
        Identifier  "amdcccle-Device[1]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP5" "0-DFP5"
        BusID       "PCI:1:0:0"
EndSection
 
Section "Device"
        Identifier  "amdcccle-Device[2]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP2" "1-DFP2"
        BusID       "PCI:2:0:0"
EndSection
 
Section "Device"
        Identifier  "amdcccle-Device[1]-1"
        Driver      "fglrx"
        Option      "Monitor-DFP6" "0-DFP6"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection
 
Section "Device"
        Identifier  "amdcccle-Device[1]-2"
        Driver      "fglrx"
        Option      "Monitor-DFP1" "0-DFP1"
        BusID       "PCI:1:0:0"
        Screen      2
EndSection
 
Section "Screen"
        Identifier "amdcccle-Screen[1]-0"
        Device     "amdcccle-Device[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
 
Section "Screen"
        Identifier "amdcccle-Screen[2]-0"
        Device     "amdcccle-Device[2]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
 
Section "Screen"
        Identifier "amdcccle-Screen[1]-1"
        Device     "amdcccle-Device[1]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
 
Section "Screen"
        Identifier "amdcccle-Screen[1]-2"
        Device     "amdcccle-Device[1]-2"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
My /etc/X11/xorg.conf based upon your setup:
```
#-------ATI Adapters Here-------------------
Section "Device"
Identifier "ATI0"
Driver "radeon"
BusID "PCI:01:00:0"
Option "ZaphodHeads" "HDMI-0"
Screen 0
EndSection


Section "Device"
Identifier "ATI1"
Driver "radeon"
BusID "PCI:01:00:0" 
Option "ZaphodHeads" "DisplayPort-0"
Screen 1
EndSection


Section "Device"
Identifier "ATI2"
Driver "radeon"
BusID "PCI:01:00:0"
Option "ZaphodHeads" "DVI-0"
Screen 0
EndSection


Section "Device"
Identifier "ATI3"
Driver "radeon"
BusID "PCI:02:00:0"
Option "ZaphodHeads" "DVI-1"
Screen 1
EndSection


#-------Monitors Here----------------------
Section "Monitor"
Identifier "HDMI-0"
# Option "Primary" "On"
Option "DPMS" "true"
Option "PreferredMode" "1920x1080"
Option "TargetRefresh" "60"
# Option "Rotate" "normal"
# Option "Disable" "false"
EndSection


Section "Monitor"
Identifier "DisplayPort-0"
Option "DPMS" "true"
Option "PreferredMode" "1920x1080"
Option "TargetRefresh" "60"
# Option "Rotate" "normal"
# Option "Disable" "false"
EndSection


Section "Monitor"
Identifier "DVI-0"
Option "DPMS" "true"
Option "PreferredMode" "1600x900"
Option "TargetRefresh" "60"
# Option "Rotate" "normal"
# Option "Disable" "false"
EndSection


Section "Monitor"
Identifier "DVI-1"
Option "DPMS" "true"
Option "PreferredMode" "1600x900"
Option "TargetRefresh" "60"
# Option "Rotate" "normal"
# Option "Disable" "false"
EndSection


#-------Screens Here---------------------
Section "Screen"
Identifier "Screen0"
Device "ATI0"
Monitor "HDMI-0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1080"
EndSubSection
EndSection


Section "Screen"
Identifier "Screen1"
Device "ATI1"
Monitor "DisplayPort-0"
DefaultDepth 24
SubSection "Display"
Depth 24 
Modes "1920x1080"
EndSubSection
EndSection


Section "Screen"
Identifier "Screen2"
Device "ATI2"
Monitor "DVI-0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1600x900"
EndSubSection
EndSection


Section "Screen"
Identifier "Screen3"
Device "ATI3"
Monitor "DVI-1"
DefaultDepth 24
Subsection "Display"
Depth 24
Modes "1600x900"
EndSubSection
EndSection


#---------Server Configuration---------
Section "ServerLayout"
Identifier "Default Layout"
Screen "Screen0" 0 0
Screen "Screen2" 1600 0
Screen "Screen1" 0 1080
Screen "Screen3" 1600 900
EndSection


#--------Server Flags----------------
Section "ServerFlags"
# Option "Xinerama" "on"
EndSection
```
I am not really for sure what the Server layout values should be. Also, I am curious if DisplayPort-0 is the correct value on the xorg.conf as Catalyst identified it as 0-DFP7. I am not sure if the naming convention is different with the two different drivers but xorg shows them as:
> 
&#9556;&#9552; comhack@Cerberus 01:54 PM 
&#9562;&#9552;&#9552;&#9552; ~-> grep 'Output.*connected' /var/log/Xorg.1.log
[ 618.900] (II) RADEON(0): **Output DisplayPort-0 connected**
[ 618.900] (II) RADEON(0): Output **HDMI-0 connected**
[ 618.900] (II) RADEON(0): Output **DVI-0 connected]**
[ 618.900] (II) RADEON(0): Output DVI-1 disconnected
[ 619.220] (II) RADEON(G0): Output HDMI-1 disconnected
[ 619.220] (II) RADEON(G0): Output **-1 connected**
[ 619.220] (II) RADEON(G0): Output VGA-0 disconnected
Here is the error I received when trying to startx:
```
&#9556;&#9552; comhack@Cerberus 02:20 PM 
&#9562;&#9552;&#9552;&#9552; ~-> cat /var/log/Xorg.1.log | tail
[  2591.062] 
Fatal server error:
[  2591.062] no screens found
[  2591.063] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  2591.065] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[  2591.066] (EE) 
[  2591.067] Server terminated with error (1). Closing log file.
```

If anyone has any ideas, I would greatly appreciate it.

Thanks

---

### Post by securitybreach on 2012-12-20
So I have been trying for about a week to get the xf86-video-ati (opensource ATI driver) to recognize my fourth monitor that is attatched to my 2nd ati card. The problem is the foss driver uses xorg's autodtect so I was trying to write an xorg.conf from scratch based upon the Catalyst xorg.conf. I have been playing around for days trying to get it to work but have not yet succeeded.

My main video card, Radeon HD 6790, has four outputs (single-link dvi/dual-link dvi/hdmi/displayport). When I received my fourth monitor, I had problems getting the dual-link dvi to recognize my monitor. After researching, I realized that I could not use the dual-link port if I used the hdmi and displayport. This seemed to be a limitation of the hardware (and ATI's Catalyst driver) so I went and bought a cheaper Radeon 6450 to power my fourth monitor. I still had issues getting the monitor detected so I ended up manually ading the information to my xorg.conf and everything was fixed.

Everything has been fine for about 5 months until I started having issues with the Catalyst driver and the latest xorg-server so I decided to try to setup and install the opensource driver, xf86-video-ati. Once again, the fourth monitor would not work so I started researching again. Well since the opensource driver uses Xorg's autodetection for setup, I could not just add the monitor/2nd video card's information to xorg.conf so I decided to try to write an xorg.conf from scratch. Well this did not go over well even though I once got the monitor to light up but it still wasnt functional.

So a few minutes ago, I tried plugging the monitor into the fourth port on the main card. Well what do you know, it worked beautifully. I could not believe that the opensource driver now supported all four outputs on my Radeon 6790.

Also whenever I started X, it had my monitors running as a clone of each other so I started messing around with xrandr to change the resolutions and location of the monitors. Xrandr is a console based application and  I was having issues getting it to work so I installed an app called arandr which is like a gui version xrandr with output so you can see the underlying code. Arandr allows you to save the configuration file as xrandr.sh. So I just added that to my startup scripts in ~/.xinitrc and voila, I have a perfect setup as soon as I start X.

I have a window's partition for gaming that keep the network disabled on except when I run the updates once a month. So I decided to reboot into windows to see if the monitor worked. Well sure enough, the Catalyst driver disabled my hdmi port since I was using both dvi ports. So I have to unplug the fourth monitor if I reboot into windows.

It is pretty amazing that the open source ATI driver outperforms the proprietary Catalyst driver from ATI. Gotta love opensource!!!!!!!!!!!

---

