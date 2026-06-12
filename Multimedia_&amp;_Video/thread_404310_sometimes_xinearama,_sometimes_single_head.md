---
title: "sometimes xinearama, sometimes single head"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by mvsjes2 on 2007-04-08
I have a mythtv setup using an nvidia video card with multiple ports, where I attach a CRT monitor on the VGA port and a TV to the DVI port. I have successfully configured X to use xinearama for this setup.

However, I sometimes have my monitor connected and sometimes don't. When I disconnect my monitor and X starts, X tries to assign the resolution of my monitor to the TV, as if it's assigning the TV to port 0 of the card.

I would like to have X realize that the monitor isn't there and simply ignore those definitions and carry on to use the TV. Is this possible? Would multiple serverlayout sections allow for this?

Section "Monitor"
    Identifier     "DELL M992"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Toshiba TV"
    VendorName     "Toshiba"
    ModelName      "30HF84"
    DisplaySize     665    385
    HorizSync       14.0 - 65.0
    VertRefresh     56.0 - 61.0
EndSection

Section "Device"
    Identifier     "Video Port 0"
    Driver         "nvidia"
    BusID          "PCI:7:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Video Port 1"
    Driver         "nvidia"
    BusID          "PCI:7:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Monitor Screen"
    Device         "Video Port 0"
    Monitor        "DELL M992"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "TV Screen"
    Device         "Video Port 1"
    Monitor        "Toshiba TV"
    DefaultDepth    24
    Option         "UseEDID" "False"
    Option         "ExactModeTimingsDVI"     "true"
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1280x720_60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Monitor Screen" 0 0
    Screen      1  "TV Screen" RightOf "Monitor Screen"
    InputDevice    "Keyboard"
    InputDevice    "Mouse"
EndSection

(==) ServerLayout "Default Layout"
(**) |-->Screen "Monitor Screen" (0)
(**) |   |-->Monitor "DELL M992"
(**) |   |-->Device "Video Port 0"
(**) |-->Screen "TV Screen" (1)
(**) |   |-->Monitor "Toshiba TV"
(**) |   |-->Device "Video Port 1"
(**) |-->Input Device "Keyboard"
(**) |-->Input Device "Mouse"
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GS at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.43.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GS at PCI:7:0:0:
(--) NVIDIA(0):     TSB-H84S (DFP-0)
(--) NVIDIA(0): TSB-H84S (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): TSB-H84S (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(--) NVIDIA(0): DPI set to (126, 169); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option

---

### Post by WakkiTabakki on 2007-04-08
Try putting 
	```
Option		"NoPowerConnectorCheck"
```
in your Device-section.

/N

---

### Post by mvsjes2 on 2007-04-08
Thanks Wakki for the suggestion, but it did the same thing (see log below). I put the option in both device sections.

According to this
[http://www.nvnews.net/vbulletin/showthread.php?p=737256](http://www.nvnews.net/vbulletin/showthread.php?p=737256)
I can't do what I want very easily, which I find puzzling given the number of people who must use laptops and would need the same kind of functionality that I'm looking for.

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "NoPowerConnectorCheck"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(GPU-0): Skipping Power Connector Check.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GS at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.43.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GS at PCI:7:0:0:
(--) NVIDIA(0):     TSB-H84S (DFP-0)
(--) NVIDIA(0): TSB-H84S (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): TSB-H84S (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(--) NVIDIA(0): DPI set to (126, 169); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor

---

### Post by WakkiTabakki on 2007-04-09
Hi again
I must admit I only read enough of your post to identify it as a problem I had earlier, which it wasn't... Sorry about that.

From what I understand, you get the wrong resolution on your TV/external monitor? It seems like X isn't able to recognize what resolutions the screen is capable of, like it can't identify whether its a TV or an LCD hooked up to your DVI. Is that it?

 Does it change anything if you switch the option "UseEDID" to true ([http://en.wikipedia.org/wiki/EDID](http://en.wikipedia.org/wiki/EDID))?

/N

---

### Post by mvsjes2 on 2007-04-09
Hi Wakki,

I get the correct resolution if both monitor and TV are connected. If Just the TV is connected, it picks up the definitions for the monitor. If I UseEDID or not doesn't make any difference.

I've spent a lot of time reading up on this and it looks like I need to start X with a different layout parm, specifiying a ServerLayout section in the config file. I'll give that a try and see what happens.

Robin

---

### Post by WakkiTabakki on 2007-04-10
Hi
Yup, thats what I do on my laptop. Found it a bit tedious (obviously) to fiddle around with the xorg.conf-file every time so I wrote a small managing proggie for it. 
Check it out: [http://ubuntuforums.org/showthread.php?t=353103](http://ubuntuforums.org/showthread.php?t=353103)


Cheers
/N

---

### Post by mvsjes2 on 2007-04-11
Thanks Wakki,

I've downloaded your prog and will check it out. Meanwhile I've been writting a script that will check the output of "X -probeonly" and pick an appropriate xorg.conf file. I'm trying to figure out where to put the script though. Where would I put it if I wanted it to run just before before X starts up and reads the xorg.conf?

---

### Post by WakkiTabakki on 2007-04-12
I'm not 100% sure, but I'd start testing by putting it to run early at runlevel 2 (in /etc/rc2.d)... 
More info: [http://www.debian.org/doc/FAQ/ch-customizing.en.html#s-booting](http://www.debian.org/doc/FAQ/ch-customizing.en.html#s-booting)

Let me know how it goes!

(BTW, the XConfigManager-prog also contains python-functions for applying an xorg.conf unattended as well...)

/N

---

### Post by mvsjes2 on 2007-04-12
Hi Wakki,

I got the script working. I put it in /usr/local/bin/initx.sh and called it from /etc/rc.local

I put keywords to search for in my script and used those keywords to append to the end of my xorg.conf. It sounds complicated but it's actually quite simple. I've written programs in many other languages but this is pretty much my first bash script, so there may be much easier ways to do what I want.

Here's the script:
--------------------------------------------------------
#! /bin/bash

# the path to the xorg conf file
xorg="/etc/X11/xorg.conf"

# the models that are being searched for
models="M992 TSB-H84S"

# load up the x log
X -probeonly

# go find them
found=""
for model in $models
do
  check=`grep -c $model /var/log/Xorg.0.log`
  if [ $check -ge 1 ]; then
    found=$found"."$model
  fi
done

# copy the file to the conf
cp $xorg$found $xorg

exit 0
-----------------------------------------------------------

I have these three files in my /etc/X11:
xorg.conf.M992
xorg.conf.TSB-H84S
xorg.conf.M992.TSB-H84S

My dell monitor is the M992. My Toshiba TV is the TSB-H84S. If it finds both of these in Xorg.0.log it will copy xorg.conf.M992.TSB-H84S to xorg.conf. If only one it will copy the single file extension.

It's a bit crude and I have to now maintain 3 xorg.conf files, but it works enough for me.

---

### Post by mvsjes2 on 2007-04-13
It looked to me like this worked, but a problem showed up. rc.local is too late in the boot process I think. The first time I boot with a changed config it doesn't update in time. If I boot a second time without any changes it works, so ths script must be updating the xorg.conf after x is already up. I need to find another spot to put the script that's earlier in the boot process it seems.

---

### Post by mvsjes2 on 2007-04-13
For the record, I moved the script to /etc/init.d and  ran the command:
update-rc.d initx.sh start 50 S .
This put the script early enough in the boot process to successfully move the correct config.

---

