---
title: "2 ATI cards with 4 monitors Ubuntu 11.04"
date: 2011-09-15
forum: Multimedia Software
---

### Post by No-more-Restarts on 2011-09-15
I decided to post this as I struggled for weeks to figure this our properly and get my system going. Used lots of information found on the internet to finally got my system sorted out. Hope this helps someone...
_**How to get 4 ATI Radeon HD 3600 working with Ubuntu 11.04**_
 

  This guide works with the default driver that ships with Ubuntu. I did not install any third party drivers yet. Will try that later. My first objective was just to get a working Ubuntu with all four monitors. I have 2 PCI ATI Radeon HD 3600 cards, each with two DVI outputs.
  

  Check to make sure that the cards are properly detected. In order to do this do the following from a terminal window:
  lspci | grep VGA
  

  01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series 
  07:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series
  

  This shows the BusID (01:00.0 and 07:00.0) that the adaptors are on, which is necessary later. This also shows that both cards are being picked up by Ubuntu.
  

  After this check to see which driver is currently in use for the ATI adaptors by doing the following from a terminal window:
  lshw -c video
  

  WARNING: you should run this program as super-user. 
    *-display                
         description: VGA compatible controller 
         product: Mobility Radeon HD 3600 Series 
         vendor: ATI Technologies Inc 
         physical id: 0 
         bus info: pci@0000:01:00.0 
         version: 00 
         width: 64 bits 
         clock: 33MHz 
         capabilities: vga_controller bus_master cap_list rom 
         configuration: ***driver=radeon*** latency=0 
         resources: irq:49 memory:a0000000-afffffff memory:fe6e0000-fe6effff ioport:a000(size=256) memory:fe6c0000-fe6dffff 
    *-display 
         description: VGA compatible controller 
         product: Mobility Radeon HD 3600 Series 
         vendor: ATI Technologies Inc 
         physical id: 0 
         bus info: pci@0000:07:00.0 
         version: 00 
         width: 64 bits 
         clock: 33MHz 
         capabilities: vga_controller bus_master cap_list rom 
         configuration: ***driver=radeon*** latency=0 
         resources: irq:52 memory:c0000000-cfffffff memory:feae0000-feaeffff ioport:d000(size=256) memory:feac0000-feadffff 
  WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 
  

  From this output it is evident that the radeon driver is used.
  

  After this create a new xorg.conf if one does not exist in /etc/X11/. Ubuntu 11.04 works differently than previously released, which means that there might not be a an existing xorg.conf in /etc/X11/xorg.conf
  

  I created an xorg.conf file, with four device sections (2 vga adaptors with 2 outputs each), 4 monitor section (one for each monitor), and 4 screen sections (combining each adaptor with a monitor), and the the layout of the total real estate in the Server Layout section.  
 

  It is imperative that you see how your monitors are connected to your ATI adaptors by doing the following in the terminal:
  grep 'Output.*connected' /var/log/Xorg.0.log
  

  [    15.640] (II) RADEON(0): Output DVI-0 connected 
  [    16.147] (II) RADEON(1): Output DVI-2 connected 
  [    16.324] (II) RADEON(2): Output DVI-1 connected 
  [    16.519] (II) RADEON(3): Output DVI-3 connected 
  

 **The key to this is the part in the Device Section Option “ZaphodHeads” “DVI-0”**
  The DVI-0, DVI-1, DVI-2 and DVI-3 shows what to use in your xorg.conf Device and Monitor sections. I have found that the ZaphodHeads options must be in the device section with the connection and then the connection must be an identifier in the monitor section as you can see in my xorg.conf. This took me at least a couple of months to figure out. This is a lot of trial and error.  
  

  See my xorg.conf at the bottom.
  

  After all this I had the correct configuration and all my monitors working, except that I could not get any keyboard input on any of my other monitors except my primary one. The I did the following and it seems to have fixed it. From a terminal run:
  gconf-editor
  It is kind of like the registry for Ubuntu. Change the key /desktop/gnome/session/required_components/windowmanager from gnome-wm to metacity.
  

  Here is my xorg.conf
  I don't use xinerama as I had issues with it dragging a  window to another screen. This layout gives me 4 independent x-windows, which works ok, once you get use to it.
  #-------ATI Adapters Here-------------------
  Section "Device"
      Identifier   "ATI0"
      Driver         "radeon"
      BusID         "PCI:1:0:0"
      Option       "ZaphodHeads"  "DVI-0"
      Screen         0
  EndSection
  

  Section "Device"
      Identifier   "ATI1"
      Driver         "radeon"
      BusID         "PCI:1:0:0"
      Option       "ZaphodHeads"  "DVI-1"
      Screen         1
  EndSection
  

  Section "Device"
      Identifier   "ATI2"
      Driver         "radeon"
      BusID         "PCI:7:0:0"
      Option       "ZaphodHeads"  "DVI-2"
      Screen         0
  EndSection
  

  Section "Device"
      Identifier   "ATI3"
      Driver         "radeon"
      BusID         "PCI:7:0:0"
      Option       "ZaphodHeads"  "DVI-3"
      Screen         1
  EndSection
  

  #-------Monitors Here----------------------
  Section "Monitor"
      Identifier  "DVI-0"
  #    Option      "Primary" "On"
      Option        "DPMS" "true"
      Option        "PreferredMode" "1920x1200"
      Option        "TargetRefresh" "60"
  #    Option        "Rotate" "normal"
  #    Option        "Disable" "false"
  EndSection
  

  Section "Monitor"
      Identifier  "DVI-1"
      Option        "DPMS" "true"
      Option        "PreferredMode" "1920x1200"
      Option        "TargetRefresh" "60"
  #    Option        "Rotate" "normal"
  #    Option        "Disable" "false"
  EndSection
  

  Section "Monitor"
      Identifier  "DVI-2"
      Option         "DPMS" "true"
      Option      "PreferredMode" "1920x1200"
      Option      "TargetRefresh" "60"
  #    Option      "Rotate" "normal"
  #    Option        "Disable" "false"
  EndSection
  

  Section "Monitor"
      Identifier  "DVI-3"
      Option        "DPMS" "true"
      Option         "PreferredMode" "1920x1200"
      Option        "TargetRefresh" "60"
  #    Option      "Rotate" "normal"
  #    Option      "Disable" "false"
  EndSection
  

  #-------Screens Here---------------------
  Section "Screen"
      Identifier  "Screen0"
      Device      "ATI0"
      Monitor        "DVI-0"
      DefaultDepth     24
      SubSection "Display"
          Depth       24
          Modes      "1920x1200"
      EndSubSection
  EndSection
  

  Section "Screen"
      Identifier  "Screen1"
      Device      "ATI1"
      Monitor     "DVI-1"
      DefaultDepth     24
      SubSection "Display"
          Depth       24        
          Modes     "1920x1200"
      EndSubSection
  EndSection
  

  Section "Screen"
      Identifier   "Screen2"
      Device         "ATI2"
      Monitor         "DVI-2"
      DefaultDepth      24
      SubSection "Display"
          Depth       24
          Modes      "1920x1200"
      EndSubSection
  EndSection
  

  Section "Screen"
      Identifier   "Screen3"
      Device       "ATI3"
      Monitor      "DVI-3"
      DefaultDepth      24
      Subsection "Display"
          Depth       24
          Modes      "1920x1200"
      EndSubSection
  EndSection
  

  #---------Server Configuration---------
  Section "ServerLayout"
      Identifier    "Default Layout"
      Screen "Screen0" 0 0
      Screen "Screen2" 1920 0
      Screen "Screen1" 0 1200
      Screen "Screen3" 1920 1200
  EndSection
  

  #--------Server Flags----------------
  Section "ServerFlags"
  #    Option "Xinerama" "on"
  EndSection

---

### Post by securitybreach on 2012-12-19
First off, let me say that I really appreciate your post as I have been racking my brain trying to write an xorg.conf from scratch for my 4 monitor/2 video card seupt. =D>

I followed your guide and replaced the sections with my system's info but I am still having issues. I think the issue is the ServerLayout section but I am not really for sure. I would appreciate it if you could take a look at my issue.

Here is the relevant information:

I ran xrandr and it shows the fourth monitor as:

> DVI-1 disconnected (normal left inverted right x axis y axis)

Here is the entire xrandr output:*
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

Here is my old xorg.conf from Catalyst:*
```
Section "ServerLayout"
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
```

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

I am not really for sure what the Server layout values should be. Also, I am curious if DisplayPort-0 is the correct value on the xorg.conf as Catalyst identified it as 0-DFP7. I am not sure if the naming convention is different with the two different drivers but  xorg shows them as:
> &#9556;&#9552; comhack@Cerberus 01:54 PM 
&#9562;&#9552;&#9552;&#9552; ~-> grep 'Output.*connected' /var/log/Xorg.1.log
[   618.900] (II) RADEON(0): Output **DisplayPort-0 connected**
[   618.900] (II) RADEON(0): Output **HDMI-0 connected**
[   618.900] (II) RADEON(0): Output **DVI-0 connected**
[   618.900] (II) RADEON(0): Output DVI-1 disconnected
[   619.220] (II) RADEON(G0): Output HDMI-1 disconnected
[   619.220] (II) RADEON(G0): Output **DVI-1 connected**
[   619.220] (II) RADEON(G0): Output VGA-0 disconnected


Here is the error I received when trying to startx:
```
&#9556;&#9552; comhack@Cerberus 02:20 PM 
&#9562;&#9552;&#9552;&#9552; ~-> cat output 
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

If you have any ideas, I would great appreciate it.

Thanks

---

### Post by overdrank on 2012-12-19
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

