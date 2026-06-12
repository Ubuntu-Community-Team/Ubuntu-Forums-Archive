---
title: "Partial desktop"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by headshrinker on 2006-09-28
I have just installed 6.06 and am having some monitor problems - I was only seeing part of the desktop - the resolution was set to 1280x1024 but only 1024x768 was actually displaying on my monitor. Here is a bit more background:

I'm using:
1) a laptop with an S3 ProSavage DDR K4M266 graphics card
2) a Samsung 920N SyncMaster
3) the vesa driver

Some behaviour:
1) When I open up the "System->Preferences->Screen Resolution" dialog and set the resolution to anything other than 1280x1024, the screen flickers, goes blank and then the login screen appears
2) When looking at the OSD menu on the monitor (the one you get by pressing the buttons on the monitor itself), the display claims to be set to 1024x768 60Hz
3) Hitting the PrtScr button to do a screen dump gives an image of the correct size i.e. 1280x1024. On the image you can see the parts of the desktop that I can't see on my monitor.

Can anyone help me please?

---

### Post by headshrinker on 2006-09-28
Interesting development:

I have changed the driver from "vesa" to "savage". Now I get the full desktop viewing on my monitor. However, I am now limited to 1024x768.

According to the "System->Preferences->Screen Resolution" I am running at 1024x768x75Hz. The OSD on the monitor says I'm running at 1024x768x60Hz.

Looking in my /var/log/Xorg.0.log, I see:

(--) SAVAGE(0): Detected current MCLK value of 14.318 MHz
(--) SAVAGE(0): 1024x768 TFT LCD panel detected and active
(--) SAVAGE(0): - Limiting video mode to 1024x768
(--) SAVAGE(0): Found 13 modes at this depth:
    [10f] 320 x 200, 70Hz
    [112] 640 x 480, 60Hz, 72Hz, 75Hz, 85Hz
    [115] 800 x 600, 60Hz, 72Hz, 75Hz, 85Hz
    [118] 1024 x 768, 60Hz, 70Hz, 75Hz, 85Hz
    [11b] 1280 x 1024, 60Hz, 75Hz
    [11e] 640 x 400, 70Hz
    [124] 1600 x 1200, 60Hz
    [134] 320 x 240, 72Hz
    [13e] 1400 x 1050, 60Hz, 75Hz
    [144] 400 x 300, 72Hz
    [154] 512 x 384, 70Hz
    [175] 720 x 480, 75Hz
    [17f] 720 x 576, 75Hz

Note in particular the line "Limiting Video Mode to 1024x768".

At least I can now see my whole desktop - but I would really like to be looking at a 1280x1024 screen.

---

