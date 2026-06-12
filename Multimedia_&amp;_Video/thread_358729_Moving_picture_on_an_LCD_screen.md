---
title: "Moving picture on an LCD screen"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by Rob_Quads on 2007-02-11
I have managed to get my graphics card (Nvidia 6600GT) to display onto my Sammy LE32R41B using almost native resolution of 1360x768 @ 60Hz. The problem I have is that the picture is offset slightly to the left so the edge of the screen is cutt off and I have a band of blank pixels on the right.

I have tried to use xvidtune to move the picture buy what ever I try I alway get told 
"Sorry: You have requested a mode-line That is not possible, or not supported by your hardware configuration"
I even get this is I apply the settings it starts up with.

Does anyone know how i can move the screen to the right?

Below is a copy of my xorg.conf

```


Section "Monitor"
        Identifier      "SAMSUNG LE32R41B"
        HorizSync       30-61
        VertRefresh     60-75
        Option          "DPMS"
        Modeline        "1360x768@60" 85.800 1360 1440 1552 1792 768 771 777 795 +hsync +vsync
EndSection

Section "Device"
        Identifier     "[0] NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
        Driver         "nvidia"
        Screen 0
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "[0] NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
        Monitor         "SAMSUNG LE32R41B"
        DefaultDepth    24
        SubSection     "Display"
                Depth           24
                Modes           "1360x768@60" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


```

---

