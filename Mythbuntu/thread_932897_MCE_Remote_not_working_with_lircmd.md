---
title: "MCE Remote not working with lircmd"
date: 2008-09-28
forum: Mythbuntu
---

### Post by quixote23 on 2008-09-28
Before I begin, let it be known that I'm pretty much a complete Linux noob - I installed Mythbuntu about a month ago and that has been my first real experience with a Linux OS.  It's been great, I've learned a lot, but most things are still out of my grasp.  With that in mind...

I have a [Vista MCE remote]("http://www.directron.com/hair01sv.html") that I'm using with MythTV.  I've got lircrc configured and it works great, no problems there.  What I'm trying to do now is get the remote to act as a mouse outside of the MythTV interface.  In short:

1. lsusb finds the remote with no problems.  irw returns the appropriate output. 

2. lircmd is running and /dev/lircm is created.

3. I haven't been able to find an MCE-specific lircmd.conf so I'm using the most generic and common one I've been able to find.

4. Xorg.0.log shows that lircmd is loading without any problems.

And yet, when I exit out of MythTV, I don't get any control over the mouse cursor with the remote.  I've been researching this all afternoon and I haven't been able to make any headway.  I have the feeling that if I could find the right lircmd.conf file I'd be halfway home.  So... little help?

current lircmd.conf:

> 
#
# lircmd config file
#

# protocol to use
PROTOCOL IMPS/2

# ACCELERATOR start max multiplier
ACCELERATOR 1 30 1

# this button activates/deactivates mouse mode
# in this case it is the 'drag' (below power) button
# commenting out keeps it on
#ACTIVATE * drag
#TOGGLE_ACTIVATE * drag

MOVE_N  * mouse-up
MOVE_NE * mouse-right_up
MOVE_E  * mouse-right
MOVE_SE * mouse-right_down
MOVE_S  * mouse-down
MOVE_SW * mouse-left_down
MOVE_W  * mouse-left
MOVE_NW * mouse-left_up
MOVE_IN * cursor-up
MOVE_OUT * cursor-down

BUTTON1_CLICK * mouse-button_left
BUTTON2_CLICK * mouse-button_right


xorg.conf:

> 
Section "ServerLayout"
        Identifier      "MyLayout"
  screen "Screen[0]"
        Inputdevice     "Keyboard1"     "CoreKeyboard"
        Inputdevice     "Mouse1"        "CorePointer"
        InputDevice     "LIRC-Mouse"    "CorePointer"
EndSection

Section "Files"
        Fontpath        "unix/:-1"
        Fontpath        "/usr/share/fonts/misc:unscaled"
EndSection

Section "Module"
        Load            "dbe"# Double-Buffering Extension
        Load            "v4l"# Video for Linux
        Load            "extmod"
        Load            "type1"
        Load            "freetype"
        Load            "glx"# 3D layer
EndSection

Section "ServerFlags"
        Option          "allowmouseopenfail"
EndSection

Section "InputDevice"
        Identifier      "Keyboard1"
        Driver          "kbd"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "compose:rwin"
EndSection

Section "InputDevice"
        Identifier      "Mouse1"
        Driver          "mouse"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Device"        "/dev/input/mouse1"
EndSection

Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "IntelliMouse"
        Option      "SendCoreEvents"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier      "Monitor[0]"# TV
        Horizsync       30-50
        Vertrefresh     60
EndSection

Section "Device"
        Identifier      "Device[0]"
        Driver          "nvidia"
        Vendorname      "nVidia Corporation"
        Boardname       "NVIDIA GeForce FX - GeForce 6200"
        Busid           "PCI:0:13:0"
        Option          "DPMS"  "true"
        Option          "RenderAccel"   "true"
        Option          "NoLogo"        "True"
        Option          "TVOverScan"    "0.6"
        Option          "ConnectedMonitor"      "TV"
        Option          "TVStandard"    "NTSC-M"
        Option          "TVFormatOut"   "SVIDEO"
        #       Option "TwinViewOrientation" "Clone"
        #       Option "Metamodes" "1280x1024,1024x768,640x480"
EndSection

Section "Screen"
        Identifier      "Screen[0]"
        Device          "Device[0]"
        Monitor         "Monitor[0]"
        Defaultdepth    24
        Option          "TVOutFormat"   "SVIDEO"
        Option          "TVStandard"    "NTSC-M"
        Option          "ConnectedMonitor"      "TV"
        SubSection "Display"
                Depth   24
                Modes           "800x600"
        EndSubSection
EndSection

#Section "Extensions"
#        Option "Composite"
#EndSection


---

