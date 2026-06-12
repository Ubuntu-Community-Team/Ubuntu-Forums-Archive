---
title: "Low Screen Resolution with Nvidia Drivers and 19in CRT"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by kandarz on 2006-12-10
I just upgraded to Edgy from Dapper (clean install) and am trying to get my nvidia drivers to work. I had them working in Dapper with Beryl fine after just an hour of tweaking but it seams that Edgy is causing me more problems.

I have a EVGA Nvidia Geforce 7600 GT KO graphics card and the nvidia drivers do seam to load but I'm unable to get a resolution above 800x600 @ 50 Hz, actually that's the only option at all.

My /etc/X11/xorg.conf file I believe is setup correctly. I've attached it to this message.

```
Section "Monitor"
    Identifier     "Optiquest Q95"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 100.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Nvidia GeForce 7600 GT KO"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia GeForce 7600 GT KO"
    Monitor        "Optiquest Q95"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    .....
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection
```

Now I'm running a Optiquest Q95 (Viewsonic tube) 19in CRT off my video card with a DVI to VGA adapter. The Q95 supports up to 1600x1200 @ 80 Hz and I'd like to run at 1280x1024 @ 80 Hz.

So in the end I'd like to be able to use 1280x1024 @ 80 Hz along with Beryl. Thanks in advance to anyone with information.

---

### Post by firenewt on 2006-12-10
maybe this option in the Monitor section

    Option	   "DynamicTwinView" "false"

---

### Post by edjayks on 2006-12-10
i believe you should log off and press CTRL+ALT+BACKSPACE to restart the xserver. Then you should be able to select the newly added resolution.

---

### Post by saffsd on 2006-12-13
I'm in exactly the same boat here!
Switching my driver from "nvidia" to "nv" gives me all the resolutions I want. Clearly my xorg.conf is correctly set up then, and there is some strange borkage going on in the nvidia binary drivers. Were you able to solve this "locked at 800x600" problem? I've seen a few references around already but no concrete "this fixed it" replies. Still experimenting on my end, trawling logs, trying to figure out what the hell is wrong. i've already tried several versions of the nvidia drivers to no avail.

---

