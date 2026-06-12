---
title: "Newbie problem: aspect ratios, TVs and no xorg.config"
date: 2010-08-30
forum: Multimedia Software
---

### Post by pjm1 on 2010-08-30
Hi all

First post, so please be gentle... :D

I have installed Ubuntu (Lucid) onto my Dell Optiplex GX280 successfully - very pleased with it and it's so much better (in every way) than Windows.  I am using Gnome as well as XBMC.  The onboard graphics is "integrated Intel Extreme Graphics".

Plugging it into my Dell monitor (just a regular 1280x1024 panel) everything works fine, including XBMC, Totem and... well, everything.  However, when I move the box through to my living room and plug into my Panasonic X10 HD ready plasma (using VGA cable - my box doesn't have an HDMI or DVI output) the aspect ratio seems to be wrong.

The X10 is a funny beast as it's a 16:9 TV with a native resolution of 1024x768, so distinctly rectangular pixels.  I want to allow for this in linux (both Gnome and XBMC) when I play DVDs and display photos.

I've done a fair bit of googling but haven't found a solution I'm competent enough to perform (remember I'm a complete newbie and am still getting to grips with sudos and apt-gets and the like!).  It seems some solutions involve editing an xorg.config file - but my install doesn't generate/use one of these.  Alternatively, xrandr seems to have some funky options but even after reading the man page, I'm stuck as to what I should do.

Just to be clear, the system is working - the resolution is correct, it's just I'm not sure how to configure it to recognise that i have pixels which are wider than they are high... it means I basically can't use the machine to watch DVDs or display pictures at the moment (one of the purposes!)

I'm sure I haven't given enough information, so let me know if there's anything else needed but I'd be very grateful for any help or guidance from those more experienced and knowledgable than me!!

TIA...

Paul

---

### Post by pjm1 on 2010-08-30
Update:

I stopped X from a tty and ran sudo X -configure which has generated a fresh xorg.conf file.  The display sections are as follows:

```
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82915G/GV/910GL Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
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

```But now I'm stuck again... I don't really want to b*gger up my system my making changes which will give me the dreaded black screen...

Any tips?  At the moment the config file above is not even in /etc/X11 - it's where X dumped it, i.e. in my ~

TIA.

Edit: further update:

I bit the bullet and copied the xorg.conf file into /etc/X11 and edited it.  I stuck in a DisplaySize 400 225 which, I think, corresponds to 16:9.  It has had no effect!  Not sure whether this is a good or a bad thing, mind, as most of the "effects" I've been able to conjure up have involved rebooting or worse ;)

However, in Totem I can set the aspect ratio to 4:3 and it seems to make an anamorphic film stretch properly to fill the screen (somewhat counterintuitive, though...).  Even better, in XBMC I've found you can calibrate the video settings to ensure things are displayed square and true.  This has fixed the issues for all the programs I need (as well as displaying pictures in XBMC) so I'm happy for now.

---

