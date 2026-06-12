---
title: "HOWTO: Thinkpad X60t (intel driver) and Samsung 203B"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by haelters on 2008-01-21
I've been looking for quite some time for a good solution for the following problem:

When using my X60t with Intel chipset (VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)) in combination with my external Samsung 203B TFT Screen (native resolution of 1400x1050 - same as internal TFT of laptop) through the VGA port, the picture ont the external screen is always shifted to the right and the bottom 26 lines did not show.

There is already a solution on this forum by oh6eh ([http://ubuntuforums.org/showthread.php?p=3318820#post3318820](http://ubuntuforums.org/showthread.php?p=3318820#post3318820)). However, that solution uses the i810 driver and needs extra modlines in the xorg.conf file. Due to this, I could not use XRandR.

Since I use another screen at work, this is annoying. So I decided to open a bug report on xorg. These fine people pointed me to the git version of the intel driver. So I decided to give it a go, and IT WORKED !!!

Here is how I've compiled it:

```

sudo apt-get install git-core autoconf automake libtool
sudo apt-get install xorg-dev libdrm-dev mesa-common-dev build-essential
cd /tmp
git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
cd xf86-video-intel
sh autogen.sh
make
sudo cp /usr/lib/xorg/modules/drivers/intel_drv.so /usr/lib/xorg/modules/drivers/intel_drv.so.backup
sudo cp src/.libs/intel_drv.so /usr/lib/xorg/modules/drivers/intel_drv.so

```

Then I changed my xorg.conf file:
```

Section "Device"
       Identifier      "Intel Controller 0"
       Driver          "intel"
       BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Controller 0"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

[B]Note that the above xorg.conf is NOT complete (you need input sections, ...). I'm only showing the relevant parts
[/B]

Then all I needed to do was restart gdm
```

sudo /etc/init.d/gdm restart

```

and voila, it works now with XRandR:
```

Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1400
VGA connected 1400x1050+0+0 (normal left inverted right) 408mm x 300mm
   1400x1050      60.0*+   60.0  
   1280x1024      59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1400x1050+0+0 (normal left inverted right) 245mm x 184mm
   1400x1050      50.0*+
   1280x1024      59.9  
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0     59.9  

```

Me+=Happy :-)

---

