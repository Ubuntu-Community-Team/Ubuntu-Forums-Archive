---
title: "IBM T221 with dual DVI"
date: 2011-07-12
forum: Multimedia Software
---

### Post by chx1975 on 2011-07-12
The monitor came with an LFS60-two DVI+USB cable. I need to plug the primary DVI into what Linux calls "HDMI3" and the secondary DVI into "HDMI2" and then I can see the available modes with xrandr -q (not if i plug 'em the other way around!). I can switch HDMI3 into either 3840x2400 or 1920x2400 but the moment I switch HDMI2 as well the monitor shuts down. I know the HDMI2 output works because my L220x works with it. Modelines from Xorg.0.log / shown by xrandr:

```
Modeline "3840x2400"x0.0  116.75  3840 3888 3920 4000  2400 2402 2408 2414 +hsync -vsync (29.2 kHz)
Modeline "1920x1200"x0.0  122.50  1920 1968 2000 2080  1200 1202 1208 1228 +hsync -vsync (58.9 kHz)
Modeline "1920x2400"x0.0  126.25  1920 1968 2000 2080  2400 2402 2412 2428 +hsync -vsync (60.7 kHz)
```

```
xrandr --output HDMI3 --mode 1920x2400&#65279; ; xrandr --output LVDS1 --off; xrandr --output HDMI2 --mode 1920x2400 --left-of HDMI3&#65279;
```

If I stop after the first xrandr I see the monitor working (and I can do 3840x2400 as well). Also tried right-of and nothing. I am a bit stuck here.

X.Org X Server 1.10.2&#65279;, Intel driver 2.15.0&#65279;, Chipset: "Sandybridge Mobile (GT2+)"&#65279; (it's an i2520M CPU).

---

### Post by BicyclerBoy on 2011-07-12
FWIW.
HDMI (19pin) is single link.
DVI-D is dual link capable.
The resolution 1920x1200 @ 60 (CVT-RB) is the max for single link.
So to get WQUXGA (3,840 × 2,400) @ 33 Hz with GTF blanking (2 × 159 MHz) requires dual link.
HDMI is not a good solution for computers.

I can't find your monitor.
Your modelines don't look right to me, all the dot clocks do not match the resolutions at normal refresh rates.
1920x1200@60 cvt-rb should be 154MHz (single link).

Your monitor cable should (could) be a one DVI-D (dual link) to twin HDMI (single link).

I have never used a dual link over twin-HDMI.
I would think the graphics driver would detect (EDID) that dual link is required & re-assign the 2nd HDMI wired port as part of the other.
Then the mode setting would only be applied to one wired port (the primary one).

There is/was chatter on forums about HDMI problems on intel sandybridge.

---

### Post by chx1975 on 2011-07-12
Uh, I am using DVI connectors just xrandr calls 'em HDMI. And single link, yes.

And there's nothing normal here, the 3840x2400 over single link is I think 12Hz or so, the 1920x2400 over two single DVI is 25Hz, and finally the monitor, even with four inputs can handle 48Hz at most :) but I only have two ATM.

And the modelines are read by xrandr from the monitor EDID.

---

### Post by chx1975 on 2011-07-13
I got it working based on [http://www.altechnative.net/?p=192](http://www.altechnative.net/?p=192) . Note that post uses a fake xinerama driver which does not seem to be necessary on Intel. Still, I attached it because that link is dead and you'd need to retrieve it from the Internet Archive in case you need it.

The "Primary" DVI plug goes into what Linux calls HDMI3 and the "Secondary" DVI plug (the big cable with an LFH 60 and two DVI and a USB has the DVI plugs labeled) goes into what Linux calls HDMI2.

```

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "HDMI3"
	Option	    "DPMS" "true"
	Option	    "Disable" "false"
	DisplaySize	487	304
EndSection

Section "Monitor"
	Identifier   "HDMI2"
	Option	    "DPMS" "true"
	Option	    "Position" "1920 0"
	Option	    "Disable" "false"
	DisplaySize	487	304
EndSection

Section "Monitor"
	Identifier	"LVDS1"
	Option	"Disable"	"TRUE"
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "intel"
        BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen"
	Device     "Card0"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3840 2400
		Depth     24
		Modes    "1920x2400"
	EndSubSection
EndSection

```

---

### Post by aquarat on 2011-07-14
I've just bought 7 of these displays and I'm trying to get the first one working... I'm going to try your code now. Thanks in advance :) .

---

### Post by aquarat on 2011-07-14
So lots of irritation and frustration and now it's working.

This is how I did it (for Nvidia card owners) :

I acquired the EDID from the "good" display and then overrode the EDIDs on both displays.

I added this to the xorg.conf file under "Screens" :
```

Option     "CustomEDID" "DFP-0:/home/aquarat/edid.bin"
Option     "CustomEDID" "DFP-0:/home/aquarat/edid.bin"
Option	   "NoTwinViewXineramaInfo"

```
This was done after 1) entering recovery mode and applying generic config and then 2) further modifying the generic config with the Nvidia UI (to set the resolutions on both virtual monitors to 1920x1200).

Here's a copy of my xorg.conf file if anyone is interested :
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "IBM"
    HorizSync       22.0 - 105.0
    VertRefresh     9.0 - 95.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 285"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +1920+0, DFP-1: 1920x2400 +0+0"
# Removed Option "TwinViewXineramaInfoOrder" "DFP-1"
# Removed Option "metamodes" "DFP-0: 1920x2400_20 +1920+0, DFP-1: 1920x2400_20 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "CustomEDID" "DFP-0:/home/aquarat/edid.bin"
    Option         "CustomEDID" "DFP-1:/home/aquarat/edid.bin"
    Option	"NoTwinViewXineramaInfo"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1920x2400 +0+0, DFP-1: 1920x2400 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

Adding "Option	"NoTwinViewXineramaInfo" under "Screen" causes Nvidia's drivers to suppress display composition data so that the window manager doesn't know there are two displays so everything acts like it's one big display.

---

### Post by chx1975 on 2011-07-14
Very interesting. The T221 manuals have an EDID change process, you sure needed to do this? Do not use the EDID manual but the full user manual [http://download.lenovo.com/ibmdl/pub/pc/pccbbs/visuals/usersguidet221.pdf](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/visuals/usersguidet221.pdf)

In any case how did you dump the EDID?

---

### Post by aquarat on 2011-07-15
> 
have an EDID change process


That's convenient :P I'll take a look, thanks.

I dumped the EDID using the "acquire EDID" button in Nvidia's control application.

---

### Post by BicyclerBoy on 2011-07-15
I'm so slow I only just found the monitor on Wikipedia..

This monitor would be excellent for CAD..
Shame the monitor did not use dual-link DVI from the start but I guess the video cards were not ready, hence the adaptor boxes etc.

I think you can set the verbosity levels of Xorg & it will then dump EDID into a file..
The nvidia-xconfig does it as a cmdline option..

---

### Post by chx1975 on 2011-07-16
No need for adaptor boxes any more. Drop me a PM if interested in LFH 60-DL DVI adapters for this monitor.

---

### Post by chx1975 on 2011-07-18
A lot of what I had above was not necessary and also it lacked the DisplaySize section which made everything way too small. I added that now -- helps readibility, tons. xdpyinfo reports 200x201 dots per inch now.

Also I got my DisplayLink-dual link DVI converters , the results are not promising yet because I only have single link DVI cables at home, I hope with DL DVI the 3840x2400@48Hz nirvana can be achieved, stay tuned.

---

### Post by discord on 2011-07-28
I'd love to have one of these monitors. I'm afraid they are out of my price range. Do you mind me asking what you paid for one?

---

### Post by aquarat on 2011-07-30
Hey Discord

They're going for about $950 USD at the moment on eBay.

:)

---

### Post by mfsuri on 2011-08-18
> **chx1975 said:**
> No need for adaptor boxes any more. Drop me a PM if interested in LFH 60-DL DVI adapters for this monitor.

YES PLEASE ! How can I acquire one.

---

### Post by aquarat on 2012-01-26
So... if anyone's interested, I'm now running two IBM T221 DGP displays using two Nvidia GTX 260 GFX cards. This is my xorg.conf (in case it helps someone) : (The edid.bin reference is a file created by the nvidia-settings utility)

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 280.13  (buildd@yellow)  Fri Aug  5 12:31:28 UTC 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 3840 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "IBM"
    HorizSync       22.0 - 105.0
    VertRefresh     9.0 - 95.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "IBM"
    HorizSync       22.0 - 105.0
    VertRefresh     9.0 - 95.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 285"
    BusID          "PCI:2:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 285"
    BusID          "PCI:6:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "CustomEDID" "DFP-0:/home/aquarat/edid.bin"
    Option         "CustomEDID" "DFP-1:/home/aquarat/edid.bin"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1920x2400 +0+0, DFP-1: 1920x2400 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-1: 1920x1080 +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "CustomEDID" "DFP-0:/home/aquarat/edid.bin"
    Option         "CustomEDID" "DFP-1:/home/aquarat/edid.bin"
    Option         "NoTwinViewXineramaInfo"
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-1: 1920x2400 +1920+0, DFP-0: 1920x2400 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

I still need to work out how to set the dpi. The displays run at 25Hz and present to the user as one large Desktop (7680x 2400).

---

### Post by b00n on 2012-02-12
> So... if anyone's interested, I'm now running two IBM T221 DGP displays  using two Nvidia GTX 260 GFX cards. This is my xorg.conf (in case it  helps someone) :Thanks much, I am trying to get up a pair of T221s and still having problems, I wonder if anybody has thoughts.

I am using Ubuntu 11.10, with up to today's updates, 64-bit, and two EVGA GTX 550 Ti cards.

I have so far tried various configurations produced by the Nvidia configuration tool and saved to /etc/X11/xorg.conf.  The most successful combination is to enable each card's two half monitors using TwinView and to not enable Xinarama.  This gives me both displays "lit up", but only the 0th device's display is useful.  When I move the cursor to the 1th display, the cursor changes from an arrow to an X, and the standard Ubuntu display configuration tool only recognizes the 0th display (and as "Unknown").

If I click the checkbox in the Nvidia configuration tool to enable Xinerama, the 1th display now becomes active, but the mouse has to be on the 0th display in order to point at stuff on the 1th display.  This makes it a bit hard to do anything useful.  I notice aquarat's configuration has screen1 to the left of screen0.  That does not seem to be possible from within the Nvidia configuration tool, but I will look at xorg.conf again when I finish reinstalling (my HDD got trashed enough I could not boot, see below).

Alternatively, I can select each of the half-displays separately and try to bring them up under Xinerama.  I get 4x identical 1920x2400 backgrounds and can move the mouse around between them all, but it gets stuck at the background that says "Ubuntu 11.10" and I never seem to get a working window manager or the default background.

An additional problem seems to appear in several configurations: I have the screen saver set to blank after, say, 5 minutes idle.  When I try to "wake it up" again, the backlight comes on and the arrow mouse cursor is visible, but nothing else shows up.  I'm not sure if this is in all configurations.  In some cases I can mouse around and get stuff by dead reckoning.  In some cases, I can do Ctrl-Alt-F1 to get a text login, but that brings me to my next problem...

Some time after logging in a text console, the video goes haywire -- it looks almost black, but with a hazy color to it.  I can no longer Alt-F7 back to the console.  It does not seem to be obviously related to anything, and sometimes happens quickly -- in one case before I even managed to log in.  I'm not sure how much is still alive at this point, in some cases I have resorted to pressing the reset button, but I don't recall at this point if it is 100% of the time or if I have managed to escape by dead reckoning.

Finally, I tried adding a 'Section "Monitor"' entry of
```

    DisplaySize       478 299
```which I had hoped (based on some other posts) would rationalize the size of stuff which is otherwise itty bitty tiny by default.  So far it seems to just be ignoed.

If folks have further thoughts on any of these, I'd appreciate a hand.  Thanks!

---

### Post by taj123 on 2012-06-25
> **chx1975 said:**
> No need for adaptor boxes any more. Drop me a PM if interested in LFH 60-DL DVI adapters for this monitor.
 
 
chx1975 - I know this is a old thread, but where can I get these adaptors from???

---

### Post by b00n on 2012-06-30
> where can I get these adaptors[http://http://forum.notebookreview.com/lenovo-ibm/566338-lenovo-w520-owners-thread-472.html](http://http://forum.notebookreview.com/lenovo-ibm/566338-lenovo-w520-owners-thread-472.html)

I still don't have both monitors working, but one at a time they work fine -- using adapters from Cirthix.

---

