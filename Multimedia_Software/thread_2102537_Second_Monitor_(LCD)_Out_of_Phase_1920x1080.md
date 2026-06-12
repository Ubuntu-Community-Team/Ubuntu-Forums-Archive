---
title: "Second Monitor (LCD) Out of Phase? 1920x1080"
date: 2013-01-07
forum: Multimedia Software
---

### Post by churl on 2013-01-07
Hello world! After over 4 years of using Ubuntu, I'm going to do my first post:

    My external monitor (1920x1080 LCD) is plugged into the VGA port of my laptop (LVDS-0) and the external monitor (VGA-0) has horizontal lines rippling as if it is out of phase.

    I can affect the "rippling" by adjusting the Phase setting on the monitor.  Phase all the way up ALMOST fixes the rippling, but it also makes the display blurry.

    My netbook treats this monitor fine, no "rippling".
    I've tried every set of drivers I could find.

(From NVIDIA X Server Settings)
Dimensions: 3200x1080 pixels (847x286 millimeters)
Resolution: 96x96 dots per inch
Depth: 24
GeForce 7150M / nForce 630M (GPU 0)
LPL LP154WX4-TLC8 (DFP-0),
HannStar Display Corp iH254D (CRT-0)

64bit Xubuntu Precise
No xorg.conf

If I turn off the laptop's monitor using: $desper -S      The "rippling" lessens to almost unnoticeable until I move the mouse or type and then it's more like soft "waves" and less of a jarring "rippling".

---

### Post by BicyclerBoy on 2013-01-07
Are you using twinview or separate X screens?

Has this always happened?
Guess there is no DVI-D output..

The rippling could caused by the beat frequency of 2 very similar (but not exactly same) modelines..

You might be able to force one screen (CRT) to 65 or 70Hz but this requires twinview to be disabled.

---

### Post by churl on 2013-01-07
I am using twinview

This "rippling" has always happened since the install.

Where can I find my current modeline settings?  I have no xorg.conf but there are settings in the "NVIDIA X Server Settings".  I assume "NVIDIA X Server Settings" reads the state of X as is and offers to create a xorg.conf for you if desired.
I'll try seperate X screens some more.
Thank you for your reply, any additional feedback is welcome :)

---

### Post by BicyclerBoy on 2013-01-08
AFAIK Twinview requires/forces the video mode refreshrate to be the same across the desktop.

It is possible that your hardware can only generate approximately matching refreshrates & hence the beat freq ripple. Or it could be a electronic or PCB layout design failure.

The video mode (lines) are most likely internal.
Look in /var/log/Xorg.0.log to determine..

You can get xorg.conf created from nvidia-settings or by:
sudo nvidia-xconfig

Have you ever connected a quality brand VGA device ?

---

### Post by churl on 2013-01-08
I do not know what to look for in my Xorg.0.log
Here is my Xorg.0.log [http://pastebin.com/1vfZJVUX](http://pastebin.com/1vfZJVUX)

I have connected to a smaller non-widescreen monitor and it worked fine.
I am not sure where to go from here :)

---

### Post by churl on 2013-01-08
I edited my ~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml and changed all of the refresh rates to:  

<property name="RefreshRate" type="double" value="60"/>

This helped a lot but did not completely fix the issue. 
Here is my displays.xml [http://pastebin.com/yBLZKP5J](http://pastebin.com/yBLZKP5J)
I am open to suggestions :)

---

### Post by BicyclerBoy on 2013-01-10
I would have thought it unlikely that nVidia X server driver would use any setings from .config/Xfce4/..

The nvidia settings come from /etc/X11/xorg.conf & ~/.nvidia_settingsrc.

Maybe the problem is composite effects manager (& it's timing) maybe that is why .config/Xfce4/.. did something..
I think Xfce uses mutter/clutter or metacity effects manager, maybe it needs some refresh rate setting.

Try not using same resolution on each screen...set the CRT to 1440x900_60.

---

### Post by churl on 2013-01-10
> **BicyclerBoy said:**
> I would have thought it unlikely that nVidia X server driver would use any setings from .config/Xfce4/.. 

The nvidia settings come from /etc/X11/xorg.conf & ~/.nvidia_settingsrc.

Right now without an xorg.conf, and changing the refresh values in the displays.xml, the screen looks pretty good

> Maybe the problem is composite effects manager (& it's timing) maybe that is why .config/Xfce4/.. did something..
I think Xfce uses mutter/clutter or metacity effects manager, maybe it needs some refresh rate setting.

I'm not using xfce4's composting or compiz if that is what you're referring to.  If not lemme know what you mean and I'll look into it :)

> Try not using same resolution on each screen...set the CRT to 1440x900_60.

I've tried all kinds of resolutions on the widescreen (CRT) and the rippling persists with all resolutions.  I'm not sure the best thing to use to try different refresh rates.  I tried a hand full of different ones with xrandr, or at least I think I did it right.
xrandr --output VGA-0 --rate 70   (as an example)

---

