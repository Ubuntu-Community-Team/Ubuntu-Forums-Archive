---
title: "DVI-HDMI 1920x1080 underscan problem"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by keijonaama on 2008-01-14
Hi. I have a following problem. My TV (Samsung M87 40") is underscanning the picture on 1920x1080_60Hz resolution, when using the DVI-HDMI input. This can't be fixed with TV's "just scan"-option. When I'm using the VGA input the picture is normal.

When I choose a lower refresh rate (for example <30Hz), with DVI input the TV overscans the picture. TV also goes into 1080i mode. This overscanning can be fixed with this TV's "just scan"- option.

I'm using a ATI X1200- graphics card, which is intergrated to motherboard. I have installed the latest ATI fglrx driver.

Does anyone have any suggestions? I have tried a bunch of different modelines and options in xorg.conf. Now I'm leaning towards buying a new graphics card to fix this problem.

---

### Post by intel on 2008-01-19
have you tried the above with radeonhd?

you may find further help at the following support site for ATI RAdeon X1200 Series cards

https://groups.google.com/group/x1250

---

### Post by vvyytenk on 2008-02-12
I'm using ATI radeon 2600xt on ubuntu 7.10 amd64 with latest ATI linux driver. My TV monitor is a Samsung 40' 1080p LCD. and I'm experiencing underscan on 1920x1080 60hz as well, I tested 1920x1080 50hz, it's overscan in 16:9 mode, and looks OK after switch to Just scan mode. I think it might be a driver issue. In XP/Vista, the underscan/overscan ratio can be adjusted using slide bar in CCC. But in linux, this feature is missing, There are only 2 options to select under 'image scaling'. Neither 'scale image to full panel' or 'no scaling' will fill the screen.

---

### Post by JarrettV on 2008-06-10
any solution to this?  After installing latest ATI driver (8.5) I now have underscan problems as well on a 1360x768.  Note the previous drivers filled the whole screen.

---

### Post by mojopej on 2008-06-20
I have the same problems. 8.5 Catalyst Driver:Fgxlr. HDMI>DVI Card:RadeonHD 2400 
Anyone found a solution.

---

### Post by mojopej on 2008-06-21
Just tried 8.6. Still underscan.

---

