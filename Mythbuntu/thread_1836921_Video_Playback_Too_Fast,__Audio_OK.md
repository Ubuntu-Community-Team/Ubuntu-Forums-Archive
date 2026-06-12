---
title: "Video Playback Too Fast,  Audio OK"
date: 2011-08-31
forum: Mythbuntu
---

### Post by jnjc on 2011-08-31
Hi,

I've setup a fresh install of mythbuntu 11.04 my hardware is:


VIA Mini ITX EPIA EX15000LG 1.5GHz C7 CPU 
with Integrated VIA UniChrome™ Pro II 3D/2D graphics with MPEG-2/4 and WMV9 decoding acceleration

I am using the openchrome driver.

I can get video output etc.  but when I play a video the picture seems to be running at double speed, but the audio is playing at normal speed.  I have tried various tweaks to the xorg.conf file but I'm getting nowhere, anybody got any idea how I might fix this ?  Below is a copy of my xorg.conf file.

Thanks,
   JC

```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "glx"
        Load  "record"
        Load  "dbe"
        Load  "extmod"
        Load  "dri2"
        Load  "dri"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
#        Option "AccelMethod" "EXA"
        Option "TVOutput" "Composite"
        Option "TVType" "PAL"
        Option "VBEModes" "true"
        Option "VBEModes" "true"
        Option "EnableAGPDMA" "true"
        Identifier  "Card0"
        Driver      "openchrome"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    DefaultDepth    24
    Option         "TwinView"
    Option         "SecondMonitorHorizSync" "30-60"
    Option         "SecondMonitorVertSync" "50-60"
    Option         "MetaModes" "640x480, 640x480"
    Option         "TwinViewOrientation" "Clone"
    Option         "ConnectedMonitor" "TV"
    Option         "TVStandard" "PAL-B"
    Option         "TVOutFormat" "Composite"

        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection


```

---

### Post by jnjc on 2011-09-03
I've been doing some more experimenting with this and I've found that if I set the Video scan to interlaced progressive during playback then things more or less work OK.

Does this shed anymore light ?

Does anybody know how to set it this way by default ?

Thanks,
   JC

---

### Post by nickrout on 2011-09-03
Where are these video files from? Are they a TV recording, or something you have ripped/downloaded?

What does mediainfo tell you about the file?

---

### Post by jnjc on 2011-09-04
The video files where ripped, recorded TV is even worse.  Having said this I have gotten a bit further with the issue.

Initially when I setup the box the TV screen was flickering madly.  I did some searching and came across a post that said I should add these two parameters to my xorg file:

        Option "VBEModes" "true"
        Option "EnableAGPDMA" "true"

Which did stop the flickering but left me with the video playback too fast and the sound jumping to catch up with the playback.

Yesterday I removed these two lines  and  played a video.  This time the sound is not jumping, but the screen is flickering and appears to be the incorrect res.

What I suspect now is that I should leave out the options above and maybe I need to set the Modelines etc. in xorg.conf to fix the flickering ?  I have tried various combination of modes lines that I found on the modelines Wiki page but I am not getting anywhere.

I am in a PAL region and using a standard def (not wide screen) TV.  Anybody got any pointers as to what I need to set the resolution and / or modelines to ?  Is there some utility I can run to find out ?

Thanks,
   JC

---

### Post by nickrout on 2011-09-05
At one time there were built in modes for the VIA chipsets that were specicifacally for TV out. From man openchrome found here [http://linux.die.net/man/4/openchrome](http://linux.die.net/man/4/openchrome)

> VIA Technologies VT1622, VT1622A, VT1623
    Supports the following modes: "640x480", "800x600", "1024x768", "848x480", "720x480" (NTSC only) and "720x576" (PAL only). Use "640x480Over", "800x600Over", "1024x768Over", "848x480Over", "720x480Over" (NTSC) and "720x576Over" (PAL) for vertical overscan. The modes "720x480Noscale" (NTSC) and "720x576Noscale" (PAL) (available on VT1622 only) provide cleaner TV output (unscaled with only minimal overscan). These modes are made available by the driver; modelines provided in xorg.conf will be ignored.

However whether that matches your chipset I don't know. I gave up on the VIA crap years ago. mythtv is phasing out support for xvmc in 0.25 anyway, and I think that will kill your setup.

---

