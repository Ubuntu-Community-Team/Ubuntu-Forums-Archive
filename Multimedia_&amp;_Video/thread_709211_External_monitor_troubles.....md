---
title: "External monitor troubles...."
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by bdpetersen on 2008-02-27
I'm looking for assistance with a problem I'm having getting an external monitor to work properly.

I'm running Ubuntu 7.10, 64-bit version, on a Sony Vaio VGN-SZ480 laptop. The graphics card is an nVidia GeForce Go 7400. There's also a power-saving mode that can run, using an Intel Graphics Media Accelerator 950. The laptop screen runs at 1280x800. The external monitor is a NEC MultiSync LCD225WNXM (resolution of 1680x1050). I'm not running compiz or Visual Effects. 

When using the nv driver, the laptop screen and the external monitor are both active, mirroring each other. But the image on the external monitor is awful. The letters are very pixelated, and they "swim". The monitor reports its signal as 1024x640.

I'm guessing it'd be much happier running at its native resolution, but many hours of fiddling with xorg.conf and "Screens And Graphics", and searching for info on this forum, gives no joy. ](*,)

The Sony Web site says that this machine won't output a video signal at anything higher than 1280x800 when the laptop screen is running, so seems like I need to turn off the laptop screen when an external monitor is connected, and then reset the resolution somehow to 1680x1050. (That's not even offered as an option in "Screen Resolution" at the moment, so....?)

A couple of other threads suggested doing this using Xrandr to turn off the laptop screen, but that doesn't work (command used was "xrandr --output LVDS --off"); the laptop screen stays on.

After much hassle, I managed to install the nvidia driver. (Using envy was the only thing that finally worked for this.) With the nvidia driver, the external monitor doesn't work at all. (Complains of no signal.) 

What am I missing here?

Are there other options that might make the external monitor work right? Would it help to use the DVI-D connection instead of the VGA connection? (There's no signal from the DVI-D connector with either the nv or the nvidia driver.) Would it help to use the other graphics card in the laptop? (Tried that, but couldn't get the intel driver to work -- the system came up in a weird "limping" low-resolution mode.) Would it help to install and use compiz? Something else?  

Any help, clues, assistance, or other info would be much appreciated! Thanks.

Cheers,
Barb Petersen

= = = = =

Output of Xrandr (looks the same with either nv or nvidia driver):

```

Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0*    51.0  
   1280x768       52.0  
   1152x768       53.0  
   1024x768       54.0  
   800x600        55.0     56.0  
   640x480        57.0  
   640x400        58.0  
   640x384        59.0  
   576x384        60.0  
   512x384        61.0  
   400x300        62.0     63.0  
   320x240        64.0  

```

Relevant bits of xorg.conf with nv driver:

```

Section "Device"
        Identifier      "nVidia Corporation G72M [GeForce Go 7400]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Laptop Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Laptop Screen"
        Device          "nVidia Corporation G72M [GeForce Go 7400]"
Monitor         "Laptop Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x800"
        EndSubSection
EndSection

Section "ServerFlags"
        Option "Xinerama" "false" 
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Laptop Screen" 
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

Relevant bits of xorg.conf with nvidia driver:

```

Section "Device"
        Identifier      "nVidia Corporation G72M [GeForce Go 7400]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Laptop Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Laptop Screen"
        Device          "nVidia Corporation G72M [GeForce Go 7400]"
        Monitor         "Laptop Monitor"
        Defaultdepth    16
        SubSection "Display"
                Depth   1
                Modes           "1680x1050"     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1680x1050"     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1680x1050"     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1680x1050"     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1680x1050"     "1280x800"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1680x1050"     "1280x800"
        EndSubSection
        Option          "AddARGBGLXVisuals"     "True"
EndSection

Section "ServerFlags"
        Option          "Xinerama"      "false"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Laptop Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"         "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

```

---

### Post by Sam Lars on 2008-02-27
You could try running nvidia-settings to set it up how you want it.  If you run that with sudo, you can save the configuration to your xorg.conf.

---

### Post by bdpetersen on 2008-02-28
Thanks!!! That did the trick. All's cool now. :-D

---

