---
title: "installing nvidia drivers"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by unisol on 2006-06-22
when i try to install the nvidia drivers for my geforce 5500 agpi get error message cannot find libedata 1.2-2  is missing in new line when t try to install it tells me  E: sub process /usr/bin/dpkg returned an error code 1 what do i need to do values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

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
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "NVIDIA Corporation NV34 [GeForce FX 5500]"
Driver "nv"
BusID "PCI:1:0:0"
VideoRam 262144
EndSection

Section "Monitor"
Identifier "Gateway EV70"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-130
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34 [GeForce FX 5500]"
Monitor "Gateway EV70"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection
__________________
tr
unisol is online now 	
Tag This Post 	No tags yet, please tag this post - what is this?
Your Tags: 	
	Report this post Edit/Delete Message Reply With Quote
unisol
View Public Profile
View LQ Blog
View Review Entries
View HCL Entries
Send email to unisol
Find More Posts by unisol
Add unisol to Your Buddy List

Reply

« Previous Thread | Back to Top | Next Thread »

LinuxQuestions.org Message
 
Cancel Changes
Quick Reply
The following errors occurred when this message was submitted
Okay
Message:
	
Remove Text Formatting
		
Bold
	
Italic
	
Underline
		

	
		
Insert Link
		
Wrap [QUOTE] tags around selected text
	  	
Decrease Size
Increase Size

---

### Post by unisol on 2006-06-22
when i chech libedata 1.2-2 is installed

---

