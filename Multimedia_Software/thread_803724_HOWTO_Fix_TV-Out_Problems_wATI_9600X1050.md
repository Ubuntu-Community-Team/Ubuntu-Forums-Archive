---
title: "HOWTO: Fix TV-Out Problems w/ATI 9600/X1050"
date: 2008-05-22
forum: Multimedia Software
---

### Post by wootah on 2008-05-22
[SIZE="4"]HOWTO: Fix weird scrolling on a TV with a Dual Head non-cloning setup on an ATI Radeon 9600/x1050[/SIZE]

[SIZE="3"]**Note**[/SIZE]
I figured as a quick post and a mini-howto, I would mention this to save some one else the hassle of figuring out what the hell is going on :) This *might* work with other video card setups that are exhibiting the same symptoms while trying to use the TV-Out (S-Video out) port.

EDIT: This would probably help out users that *do* have a cloning setup as well.

[SIZE="3"]**Original Problem**[/SIZE]
My original problem was that I was trying to use a dual-head/monitor setup with my ATI Radeon 9600 / x1050  (Sapphire) graphics card using the proprietary drivers. When I connected my TV to the graphics card (by use of the S-Video port along with just an S-Video cable OR the S-Video cable along with the RCA adapter), the tv displayed only black and white colours and it had an odd 'fast rolling' effect that made viewing it impossible. It looked kind of like a slow refresh rate, except the screen shifted vertically.

[SIZE="3"]**Xorg Reference**[/SIZE]

[SIZE="3"]_Monitor section of Xorg_[/SIZE]
```

# ***************************************
#           Setup Monitors
# ***************************************

Section "Monitor"
        Identifier   "NEC MultiSync 90GX2 (Screen 0)"
        HorizSync    30.0 - 65.0
        VertRefresh  50.0 - 75.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "Toshiba 32in (Screen 1)"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

```

[SIZE="3"]_Server Layout of Xorg_[/SIZE]
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "LCD" 0 0
        **Screen         "TV" LeftOf "LCD"**
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

```

So from here we can easily see that it is a dual-head setup with the TV display setup to the left of my LCD (that's what it is physically :))

[SIZE="3"]**Solution**[/SIZE]
Now the magical part! *I found out that the reason the TV was displaying this odd behavior was because it was sending a PAL signal* when I needed NTSC-M (For Canada and USA) (this is a bug with the Sapphire Card. See the [Note]("http://www.mythtv.org/wiki/index.php/ATI_Proprietary_Driver#Black-and-White_output") here). After reviewing the man pages for fglrx, I found that I needed to add one additional option to the device section that was specifying my TV:

[SIZE="3"]_Device Section of Xorg_[/SIZE]
```

# ***************************************
#           Setup Display Ports
# ***************************************

Section "Device"
        Identifier  "ATI Radeon 9600/X1050 (Screen 0)"
        Driver      "fglrx"
        Option      "XAANoOffscreenPixmaps"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "ATI Radeon 9600/X1050 (Screen 1)"
        Driver      "fglrx"
        **[COLOR="Red"]Option      "TVFormat" "NTSC-M" # Set the correct signal output for North America[/COLOR]**
        BusID       "PCI:2:0:0"
        Screen      1
EndSection

```

And for the last little bit:
```

# ***************************************
#       Associate Monitors to Ports
# ***************************************

Section "Screen"
        Identifier "LCD"
        Device     "ATI Radeon 9600/X1050 (Screen 0)"
        Monitor    "NEC MultiSync 90GX2 (Screen 0)"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection

Section "Screen"
        Identifier "TV"
        Device     "ATI Radeon 9600/X1050 (Screen 1)"
        Monitor    "Toshiba 32in (Screen 1)"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "640x480"
        EndSubSection
EndSection

```

After setting the **Option "TVFormat" "NTSC-M"** and restarting X (ctrl-alt-backspace), I logged in and the TV was correctly displaying the other desktop! The other available TVFormat values are: NTSC-JPN, NTSC-M, NTSC-N, PAL-B, PAL-CN, PAL-D, PAL-G, PAL-H, PAL-I, PAL-K, PAL-K1, PAL-L, PAL-N, PAL-M, PAL-SCART. To know your region, review this list: [http://www.tenlab.com/tv-systems/tvsystems.htm]("http://www.tenlab.com/tv-systems/tvsystems.htm") and also see [fglrx's man page]("http://www.linux-man-pages.org/man4/fglrx/").

[SIZE="3"]**Summary**[/SIZE]
[LIST]
[*]ATI Radeon 9600/x1050 was not displaying correct output to a TV on the S-Video out port
[*]It appeared that the output signal of the graphics card through the S-Video port was **PAL**
[*]Needed to change the output signal to **NTSC-M**
[*]Had to add the line **Option "TVFormat" "NTSC-M"** into /etc/X11/Xorg.conf under the device section that listed my secondary monitor(tv)
[*]Optional: In the Screen section that identified my TV, I forced 640x480 (default standard resolution for older TVs) with a 24 bit colour depth
[/LIST]
[SIZE="4"]Todo[/SIZE]
The one last thing I have to do is shift the picture to the left a bit, correct a slight curve, and fill in the screen a little better.

[SIZE="4"]Final Notes[/SIZE]
I hope this helps anyone who might have had the same problem! If you have anything to add, please let me know!

[SIZE="4"]Addition Links[/SIZE]
[LIST]
[*] [MythTV Guide for ATI Users]("http://www.mythtv.org/wiki/index.php/ATI_Proprietary_Driver")
[*] [ATI Binary Driver HOWTO]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
[*] [Colour TV Standards List]("http://www.tenlab.com/tv-systems/tvsystems.htm")
[*] [fglrx's Man Page]("http://www.linux-man-pages.org/man4/fglrx/")
[/LIST]

---

### Post by slacker2 on 2008-06-16
Thank you sooo much.  I have been experiencing this exact same problem with a Radeon 9600 off and on for quite some time (even with Windows XP) and could never figure out exactly what was happening.  By telling it to use NTSC/M within amdcccle, the problem cleared right up!  Thanks alot!

---

