---
title: "TV-out with S-video and ATI Radeon"
date: 2008-11-08
forum: Multimedia Software
---

### Post by jeroenvrp on 2008-11-08
Hello,

I connected my neighbours PC to his television with S-Video. When I start up the PC the non-graphical screen output shows on the TV, but when Ubuntu starts up and when starting into Gnome it shows the output on the monitor, not on the TV. When I go to screen-resolution only the monitor is shown, not the TV.

It is a new fresh installed Ubuntu 8.10 and his xorg.conf looks very basic.

When I do a lspci I get:

ATI Radeon RV200QW [Radion 7500]

When I do a xrandr, it says that S-Video is disconnected.

When starting up Windows (dual boot) the output is shown on the TV.

Please help?!

---

### Post by jeroenvrp on 2008-11-12
Bump!

---

### Post by purduepilot on 2008-11-12
I've been trying to get s-video output to work for months.  Hope to see an answer to your question

---

### Post by ttr738 on 2008-11-13
This was on an nVidia 7300GS card, so might not work. Presume you'll need to leave the "driver" line as what it is in your xorg.conf already. I changed the "device" section to the below and the card now outputs only through s-video (it's connected just to a TV, not to a PC monitor)

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "TVStandard" "PAL-I"
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVOverScan" "0.6"
        Option  "ConnectedMonitor" "TV"
EndSection

```

The last 4 options are the important ones I presume. Everything else I left as it was. Only thing I did before was install the nvidia restricted drivers. Presume there's an ATI equivalent for them?

My whole xorg.conf is now this:

```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "TVStandard" "PAL-I"
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVOverScan" "0.6"
        Option  "ConnectedMonitor" "TV"
EndSection


```

Hope that helps :)

---

### Post by ttr738 on 2008-11-13
getting tv out to work has been a bitch for me too btw!
seems much better in Intrepid though - comparing that xorg.conf to the one I had in Gutsy which was about a million lines long and did nothing.

think part of the problem is that TV auto detection never seems to work (even in XP). Someone write a configuration utility that works already! :)

---

