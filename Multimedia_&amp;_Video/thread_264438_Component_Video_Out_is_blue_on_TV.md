---
title: "Component Video Out is blue on TV"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by clarke.rainey on 2006-09-24
I have an nVidia 6600GT with one of those dongles for TV output... it has plugs for S-Video, composite, and Component.. with component output there is no overscan, everything is sync'd up correctly, etc... however... everything on the screen is blue... I have tried every combination of plugging up the cables... and it works fine in windows... does anyone know why it may be showing up as blue?.. you can operate the computer perfectly fine... it is just that everything has a very, very, strong blue tint to it...

---

### Post by kvonb on 2006-09-24
Do you turn the TV on before turning on the computer?

I have to do that with all the TV out cards I have tried.

It also might be a PAL/NTSC thing, but almost certainly is the fault of the drivers for Linux being rather spartan.

Regards,

Kev :)

---

### Post by NT4usB on 2006-09-25
I had the same thing. After much googling, came up with this tweak to my xorg.conf:
```
Section "Screen"
Identifier "Screen[0]"
Device "Device[0]"
Monitor "Monitor[0]"
DefaultDepth 24
[COLOR="Red"]Option "TVStandard" "HD480i"[/COLOR]
Option "ConnectedMonitor" "Monitor[0]"
SubSection "Display"
Depth 24
Modes "720x480_60" "800x600_60" "640x480_60"
EndSubSection
EndSection
```

Seems the [COLOR="Red"]HD480i[/COLOR] was the key to keep my pos Panasonic 27" TV from being so blue.
The rest of it may be irrelevant as my xorg.conf is a hacked up version of the one I used for dual LCD/TV display.

---

