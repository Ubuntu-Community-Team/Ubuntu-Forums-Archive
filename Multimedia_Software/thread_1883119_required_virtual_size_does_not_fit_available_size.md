---
title: "required virtual size does not fit available size"
date: 2011-11-18
forum: Multimedia Software
---

### Post by socken23 on 2011-11-18
Hi all

I have an Acer Aspire 5670 notebook with an ATI x1400. When trying to extend the screen with an external monitor, I get an exception:

Could not apply the selected configuration
required virtual size does not fit available size: requested=(2304, 800), minimum=(320, 200), maximum=(1280, 1280)

I can't choose any drivers under "additional drivers" in the system menu. It worked before updating to 11.10 so I'm sure there has to be a solution. I found some forum entries talking about changing the xorg.conf in /etc/X11/, but I don't have that file. There's just the xorg.conf.failsafe. 

Also, some articles mention the Catalyst Control Center which doesn't work either. Probably because I don't have the binary drivers installed as mentioned above.
Any idea?

---

### Post by AmateurDev on 2011-11-22
I have the same problem, except my laptop has the ATI Radeon Xpress 200M graphics card.
This code:
```
xrandr -o VGA-0 --right-of LVDS
```
lets me have dual screens, but the wallpaper get's messed up and causes windows to "drag" when moving them.

---

### Post by MoreOrLess on 2011-11-23
You probably need to create an xorg.conf and specify a larger virtual screen. It's best not to stretch the virtual screen beyond 2048 in any direction or direct rendering might be disabled on older GPU's (which causes problems like AmateurDev describes). Although some info is specific to intel, this page explains it well: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R60e#Intel_945GM_with_the_xorg_Intel_driver]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R60e#Xorg.config_for_two_screens")

---

### Post by socken23 on 2011-12-23
Hey MoreOrLess

Quite late with my answer, but I got it working with your tip. Basically, I just had to create a file /etc/X11/xorg.conf with the following content:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
            Depth           24
            Virtual         2304 2048
        EndSubSection
EndSection

```

---

### Post by inspiral on 2012-02-15
This solution worked for me too though my circumstances were slightly different.

My old motherboard with integrated Nvidia graphics went bad and the replacement with integrated ATI graphics wouldn't do the dual display thing.

The solution was to delete the old xorg.conf file and create a new one with the default screen entry with my desired virtual resolution.

Thanks OP.

---

