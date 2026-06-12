---
title: "How can I enable dvi-d output on Radeon 7500"
date: 2009-08-12
forum: Multimedia Software
---

### Post by alleycatuk on 2009-08-12
Hi,

I recently installed 9.04 Jaunty. My monitor works well using the standard d-sub vga output but I need now to use the Pc with another monitor which just has dvi-d.

Under windows, both outputs on my card are enabled and work fine. Under Ubuntu, the dvi-d doesn't seem to be enabled and I can't see how to do it - other forums don't seem to cover it

The output from lspci shows

[COLOR=Blue]01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV200 QW [Radeon 7500] [1002:5157]
[/COLOR]
I saw some forums saying I need to do something with /etc/X11/xorg.conf but I'm not sure what!
My xorg.conf doesn't have much in it...

[COLOR=Blue]Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    3360 1050
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection[/COLOR]

If I go into System -> Preferences -> Display, it does identify the monitor correctly (VGA) so I'm not sure where it gets that from!

I'd be grateful for any pointers or suggestions how to get it working. Thanks in advance.

---

