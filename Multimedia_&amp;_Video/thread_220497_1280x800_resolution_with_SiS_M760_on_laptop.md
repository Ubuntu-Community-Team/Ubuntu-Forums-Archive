---
title: "1280x800 resolution with SiS M760 on laptop"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by jvh813 on 2006-07-21
I have scoured the forums and googled for this problem to no avail. I have seen some solutions to similar problems but none of those suggestions work for me. Here is my problem:

I installed Dapper Drake on my Averatec AV4155-EH1 Laptop. The laptop resolution is 1280x800 (widescreen) but Using the "screen resolution" applet only allows me to set my resolution to a mamimum od 1024x800. I tried editing the xorg.conf file and adding the 1280x800 setting but the changes are not taking effect.

Any suggestions?

Thanks.
-JVH

---

### Post by Paerez on 2006-07-21
run:
```
sudo dpkg-reconfigure xserver-xorg
```
when it asks about your monitor, choose the medium level (I think its "Beginner" "Medium" and "Advanced") it should give you a list of resolutions with refresh rates. Find 1280x800 in the list and pick that.

For any of the other options, if you are unsure, just hit enter.

---

### Post by tseliot on 2006-07-21
Read this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by dickohead on 2006-07-30
Okay, I tried that.... 

Didn't work.

With all previous versions of Ubuntu and many other Linux distributions editing the xorg.conf file to add the 1280x800 resolution in was all that was needed.

Why won't dapper accept the changes? The file says "1280x800" "1024x768" "800x600" but Gnome is saying 640x480, 800x600 and 1024x768.

What else must be done, or what's changed since previous versions?

---

### Post by tseliot on 2006-07-30
Try this guide then:
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

Read the part about "Getting the Right Mode for an LCD monitor"

---

### Post by pedro.joinville on 2006-07-30
I have a Intel Graphics Media Accelerator 900. I had to install 915resolution package.

---

### Post by mithion on 2006-09-18
I have the exact same computer, and mine works fine in X.  The resolution is dead on and the depth is correct as well.  I do have a problem with the Console though.  As far as I know, the Console doesn't support widescreen resolution, and so I'm stuck setting the parameters to those of regular form factored screens (i.e. 640x480, or 800x600, 1024x768 and 1200x1024).  I usually pick 1024x768 which offers the best compromise.  But if your X doesn't work, that's pretty strange.  Here's my xorg.conf file.  Maybe you can look at it and see where yours is wrong.

Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "Generic Video Card"
  boardname "sis"
  busid "PCI:1:0:0"
  driver "sis"
  screen 0
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "Flat Panel 1280x800"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Generic Video Card"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x800@60" "640x480@60" "800x600@60" "1024x768@60" "1280x1024@60" "1600x1200@60" "1792x1344@60" "1856x1392@60" "1920x1440@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
  Mode 0666
EndSection

# Section "Extensions"
#   option "Composite" "Disable"
# EndSection
Section "device" # 
  identifier "device1"
  boardname "sis"
  busid "PCI:1:0:0"
  driver "sis"
  screen 1
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection

Hope this helps.

---

### Post by barathbr on 2006-12-15
Mithion, Thanks for posting your xorg.conf. I installed dapper a few days back after Win XP crashed and the only problem I was facing was with the screen res. I just pasted in the Monitor and Screen sections into my config and I now get the full resolution :D

---

### Post by barathbr on 2006-12-16
btw, this is on a Acer 5002wlmi

---

### Post by tiger015 on 2007-05-09
Great!! I tried so hard to get it work. I also copied monitor and screen parts to my xorg.conf file, rebooted and 
I could see 1280x800 resolution. I am now working on native resolution on my Acer Aspire 3004 with SiS card:)

---

