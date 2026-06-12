---
title: "Thinkpad T42 display output switching, Fn+F7, new xorg.conf.fglrx-## created??"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by SjRaptor on 2007-03-29
I'm having trouble getting one last Thinkpad special key button to work on my T42 2378-FVU. This model has an ATI 9600 Mobility. I've read the pages at ThinkWiki, specifically [How to get special keys to work]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work#ibm-acpi_events") and also [Problem with video output switching]("http://www.thinkwiki.org/wiki/Problem_with_video_output_switching"). To help make reading this easier, **I've put commands in bold**.

I have done the following:

**root@localhost~# echo enable,0xffff >/proc/acpi/ibm/hotkey**

**root@localhost~# cat /proc/acp/ibm/hotkey**
status:         enabled
mask:           0x09dc
commands:       enable, disable, reset, <mask>

To test, I ran 'xev' and tailed the output of /var/log/acpid

**user@localhost:~$ tail -f /var/log/acpid**
[Thu Mar 29 09:46:12 2007] received event "ibm/hotkey HKEY 00000080 00001007"
[Thu Mar 29 09:46:12 2007] notifying client 4676[108:108]
[Thu Mar 29 09:46:12 2007] notifying client 4849[0:0]
[Thu Mar 29 09:46:12 2007] executing action "/bin/true"
[Thu Mar 29 09:46:12 2007] BEGIN HANDLER MESSAGES
[Thu Mar 29 09:46:12 2007] END HANDLER MESSAGES
[Thu Mar 29 09:46:12 2007] action exited with status 0
[Thu Mar 29 09:46:12 2007] completed event "ibm/hotkey HKEY 00000080 00001007"
[Thu Mar 29 09:46:17 2007] received event "ibm/hotkey HKEY 00000080 00001007"
[Thu Mar 29 09:46:17 2007] notifying client 4676[108:108]
[Thu Mar 29 09:46:17 2007] notifying client 4849[0:0]
[Thu Mar 29 09:46:17 2007] executing action "/bin/true"
[Thu Mar 29 09:46:17 2007] BEGIN HANDLER MESSAGES
[Thu Mar 29 09:46:17 2007] END HANDLER MESSAGES
[Thu Mar 29 09:46:17 2007] action exited with status 0
[Thu Mar 29 09:46:17 2007] completed event "ibm/hotkey HKEY 00000080 00001007"


Clearly, ibm/hotkey HKEY 00000080 00001007 correctly corresponds with the event listed for Fn+F7 on the ThinkWiki page under "ibm-acpi events". However, Fn+F7 does not switch video output to an external monitor as hoped. Just to clarify, in case anybody asks, every hotkey so far works. Fn+F3 switches off LCD display, Fn+F4 puts computer to sleep, Fn+F5 turns off wireless radio, Fn+Home/End adjusts brightness and Fn+PgUp toggles ThinkLight. 

I can use the following command to enable both my LCD and external monitor:

**root@localhost~# aticonfig --enable-monitor=lvds,crt1**

I can disable the external monitor and just go back to my LCD by issuing this command:

**root@localhost~# aticonfig --enable-monitor=lvds**

These commands do work to enable my LCD and external monitor, but I have some minor issues.

Whenever I "switch" output, a new backup of my xorg.conf is created. For example:

**root@thinker:~# aticonfig --enable-monitor=lvds,crt1**
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-16
**root@thinker:~# aticonfig --enable-monitor=lvds**
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-17

As you can see from this output, a new backup is created each time displays are enabled/switch, and the number at the end of filename continues to increment.


**What I'd like to do...**

I'd like to create a single xorg.conf that will recognize lvds (my laptop lcd) as 1400x1050 resolution and also an external monitor (or projector) as 1280x1024 resolution. My plan would be to get Fn+F7 to use this single file and not create any new ones after switching between displays. Thanks to anyone who helps... I appreciate it :)

---

### Post by SjRaptor on 2007-03-30
ttt, anybody have any ideas??

---

### Post by SjRaptor on 2007-04-01
ttt

---

### Post by SjRaptor on 2007-04-05
Here is my xorg.conf. With this setup, when I start X with my external monitor plugged in, it'll load with a virtual resolution of 1400x1050. I don't think it sees the line,**         Option          "Mode2" "1280x1024"**. By virtual resolution, I mean the screen can be "scrolled" around but is only viewable 1280x1024 pixels at a time. I also figured out how I can use aticonfig to load an xorg.conf file without creating a backup, using the command **aticonfig --input=/etc/X11/xorg.conf --nobackup**

I still am trying to figure out how to get Fn+F7 working correctly and the output display resolution correct.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Files"
        # path to defoma fonts
        Fontpath        "/usr/share/X11/fonts/misc"
        Fontpath        "/usr/share/X11/fonts/cyrillic"
        Fontpath        "/usr/share/X11/fonts/100dpi/:unscaled"
        Fontpath        "/usr/share/X11/fonts/75dpi/:unscaled"
        Fontpath        "/usr/share/X11/fonts/Type1"
        Fontpath        "/usr/share/X11/fonts/100dpi"
        Fontpath        "/usr/share/X11/fonts/75dpi"
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "type1"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "YAxisMapping"  "4 5"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "EmulateWheel"  "on"
        Option          "EmulateWheelButton"    "2"
        #Option     "XAxisMapping" "6 7"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        # /dev/input/event
        # for USB
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        # /dev/input/event
        # for USB
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        # /dev/input/event
        # for USB
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Option          "EnableMonitor" "lvds,crt1"
        Option          "DesktopSetup"  "clone"
        Option          "Mode2" "1280x1024"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1400x1050"     "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1400x1050"     "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1400x1050"     "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1400x1050"     "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1400x1050"     "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1400x1050"     "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite"     "Disable"
        Option          "Composite"     "0"
        Option          "Composite"     "0"
EndSection

```

---

