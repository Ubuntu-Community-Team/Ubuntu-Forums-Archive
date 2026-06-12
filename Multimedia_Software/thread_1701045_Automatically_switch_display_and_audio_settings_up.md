---
title: "Automatically switch display and audio settings upon pluggin in and removing HDMI"
date: 2011-03-05
forum: Multimedia Software
---

### Post by The Flying Penguin on 2011-03-05
The System: HP Pavilion G62-227CL. It has an ATI Mobility Radeon HD 4250 with HDMI. It's running Ubuntu 10.10 32bit. I have 8.801 of the ATI proprietary driver and Catalyst Control Center 10.12 installed.
 
While in Ubuntu, I can connect it to a HDTV and it will automatically mirror the lcd to the HDTV at 1366x768. If I unplug the HDMI it will automatically switch back to the lcd screen at its native resolution of 1366x768. This works on the fly and requires no X restart. Sound seems to work flawlessly over HDMI except I have to manually switch the output to HDMI under sound preferences and then back to the laptop speakers upon unplugging the HDMI.
 
Here is the deal. This is my moms laptop and I am trying to make this as simple as possible for her since she is a total computer noob. When she wants to play a movie or stream Hulu and Netflix (via a vm), all I want her to have to do is plug in the HDMI and be good to go. Here is exactly what I would like it to do:
 
[LIST=1]
[*]Upon plugging the HDMI in,     automatically make the HDTV the primary screen, set resolution to     1280x720 and disable the laptop's lcd. Upon unplugging the HDMI,     automatically turn the laptop's lcd back on at the native 1366x768 (it already does this).     I can do all of this manually from CCC without having to restart X     so I imagine there should be a way to seamlessly automate the     process. CCC doesn't seem to remember my settings after unplugging     the HDMI however if I leave the HDMI plugged in it remembers     everything after restarting the laptop. Is there a line I can add     to xorg.conf that will tell it to only use the laptop's lcd when     there is no device present on the HDMI and apply the appropriate     settings?
[*]How can I make the sound     automatically transfer to HDMI when plugged in and then     automatically transfer back to the laptop speakers after unplugging     the HDMI. It be nice if I could have the HDMI volume be set to max     upon the switch and 50% to the speakers upon switching back.
[*]It would also be nice if compiz     would automatically disable when the HDMI is plugged in and turn     back on once its unplugged. Not that important since it's pretty     easy to disable even for a computer noob like my mom. It just be     nice so she doesn't have to remember.
[/LIST]
 I searched for a couple hours on Google and the Ubuntu forums on how to do this but most of the information I found dealt with getting getting audio working over HDMI in the first place or getting extended monitor options to work correctly. Nothing really seemed to deal with getting automated switching when everything is working properly.
 
Is there a particular piece of software that will handle these automated tasks? Are there config files such as xorg.conf or /etc/modprobe.d/sound.conf that need a line or two added or modified? Do I need a script? If no software is available, I would much rather have to edit some config files than mess with creating a script. I don't have time right now to learn scripting. Light modification of existing scripts, may be within my current ability though.
 
I've included my aplay -l output and xorg.conf. Let me know if you need anything else. Thanks in advance!

aplay -l results
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```xorg.conf
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "true"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:5:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
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

```

---

### Post by barksdale on 2011-08-05
Hi,

I was actually searching for a solution to this... found any already?

---

### Post by dar270785 on 2012-01-31
I have been searching for ages of a way to do this and I eventually succeeded.

Can you run the following commands and post the output back me.
xrandr

pacmd list-cards

Also is 1280x720 listed in the display settings.  Is this the maximum resolution for the HDTV.  Mine accepts 1280x720, but it's maximum is 1366x768 which is not listed in display settings.  If this is true for you please let me know.

---

