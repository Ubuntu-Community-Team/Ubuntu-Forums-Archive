---
title: "TV Out video problems in MythTV"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by douglaseg1 on 2006-12-27
Ok - I can't figure this out.  ](*,) 

I have Edgy (amd64) installed with a M2NPV-VM motherboard.  For those of you who aren't familiar with this board, it offers component video out - perfect for connecting my HDTV that doesn't support DVI.  The TV supports 1080i.

I have edited the xorg.conf file to allow my desktop to appear on the TV through the component video out.  This works fine.  I can start mythtv and the startup interface shows up on the TV.  When I select Watch TV, the TV goes black and everything freezes.  I am able to watch TV on my computer monitor (after I change the xorg.conf back to the monitor setting) without the black screen effect.

To get out, I ssh into the computer from another box and shutdown the computer.

Does anyone have any good ideas?  Could this be an issue with my xorg.conf file?  If so, why does the problem only show up when I select "watch tv"?  Is there some other setting in mythtv that I need to set to get this working?

I appreciate any thoughts.

---

### Post by Mateo on 2006-12-27
i think if you turn off your overlays, it will work.  make sure to back up the xorg.conf file first though.

---

### Post by douglaseg1 on 2006-12-27
Update -

I just tried to play a dvd on the HDTV - the video there doesn't work either.  The DVD player just freezes.  This is beginning to look like more of a video problem than a mythtv problem.

I'm not sure how to turn off overlays.  Can you be more specific?  (this is really my first time running linux / ubuntu - i've done a ton of reading, so i'm feeling pretty good about it, but i'm still a noob.)

Thanks

---

### Post by NT4usB on 2006-12-28
post your xorg.conf

---

### Post by douglaseg1 on 2006-12-28
Here is my xorg.conf file.  Thanks for looking.  I believe that the important stuff is at the bottom - however I posted it all just in case.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "MetaModes" "1920x1080"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "Connected Monitor" "TV"
    Option         "TVStandard" "HD1080i"
    Option         "TVOutFormat" "Component"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
    EndSubSection
EndSection

---

### Post by NT4usB on 2006-12-28
Read your first post again... Sounds like a MythTV setting, not xorg.
Have you tried to play a recorded program or a test mpg?
Were you playing the DVD via MythTV?
What do you have set in the mythfrontend under: 
utils/setup>setup>TV settings>playback?
Deinterlace? Algorithm?
Which version Myth and which version of ivtv?

...I remember having this problem when I first set up myth but I don't remember exactly what fixed it.
:-k

ed: another thought.
Are you running this as a slave frontend?
Try running mythfrontend --verbose all from a terminal. Maybe the output will give some ideas. 
Can also try it on the backend. mythbackend -v playback
See what the logs say.

---

### Post by douglaseg1 on 2006-12-29
Actually, the dvd was played by Totem.  So completely seperate from mythtv.

Is there anything else common between the two besides xorg.conf?

---

### Post by douglaseg1 on 2006-12-29
also, I'm not using the ivtv drivers because I have the ATI HDTV Wonder capture card.  This is correct???

---

### Post by superm1 on 2006-12-29
> **douglaseg1 said:**
> also, I'm not using the ivtv drivers because I have the ATI HDTV Wonder capture card.  This is correct???
your not using beryl/xgl/aiglx/compiz by chance are you?

---

### Post by douglaseg1 on 2006-12-29
I don't think so - but to be honest I don't know what those things are.  If they are additional installations - then no.  I followed the guide here:  ([https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)).  If these are the capture card drivers for the HDTV wonder - i used the get_dvb_firmware as noted in the guide.  For the graphics card, I used the nvidia-glx drivers.  I also installed nvidia-glx-dev because I wasn't sure if I was going to need it or not.

---

### Post by superm1 on 2006-12-29
> **douglaseg1 said:**
> I don't think so - but to be honest I don't know what those things are.  If they are additional installations - then no.  I followed the guide here:  ([https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop%29").  If these are the capture card drivers for the HDTV wonder - i used the get_dvb_firmware as noted in the guide.  For the graphics card, I used the nvidia-glx drivers.  I also installed nvidia-glx-dev because I wasn't sure if I was going to need it or not.
Okay then you didnt install any of those.  And your xorg.conf looks good.  After one of these crashes, can you see if anything is indicated in /var/log/Xorg.0.log or /var/log/Xorg.0.log.old related to this?

---

### Post by douglaseg1 on 2006-12-29
ok - I restarted on the HDTV and it did the same thing.  For this test, I used Totem Movie player to play a DVD.  It crashed and locked up the system as soon as I selected Movie -> Play Disk.  I then used ssh to get in and did a sudo shutdown -r to reboot.

Here is what was in the xorg.0.log file.  I've only included the lines tagged with (EE) for error.  I'm not sure what these mean so any help decrypting will be appreciated.  It seems to indicate something about dev/wacom.  I'll be searching on that to see what it is.  If anyone knows and thinks this is related to the issue, please let me know.  If you need the rest of the file, let me know.  Thanks for the responses so far.

(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

---

### Post by NT4usB on 2006-12-29
The waycom stuff comes from the xorg entries that (presumably) you're not using:
```
# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection
``` etc...

I delete all these out of my xorg (remember to delete the entries in server layout too!) and the errors go away.

Did you try logging when running myth to see if that gives any info?

---

