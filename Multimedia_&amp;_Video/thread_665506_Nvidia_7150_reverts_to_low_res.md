---
title: "Nvidia 7150 reverts to low res"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by FlyingIsFun1217 on 2008-01-12
Hey!

I've got a new HP DV6704NR, everything seems to be supported so far (supported, not working), except for the wireless (which is something I want to work on after I figure out the graphics troubles). My main problem though, is that even after installing the proprietary Nvidia driver, the screen res is at best 800x600 (on a monitor that supports 1280x800).

After changing the resolution to 1280x800 using the Nvidia control panel, the screen looks really nice. Once I restart the xserver though, it reverts right back to the vesa driver and back to 800x600.

It seems like even when I change the xorg.conf file (to use driver nvidia and resolution 1280x800, it always reverts back to 800x600.

Is there an easy way for me to get the xserver to keep using the nvidia driver at a resolution of 1280x800? It seems like such a trivial thing.

Thanks so much!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-12
Anyone? It's somewhat unusable this way.

FlyingIsFun1217

---

### Post by RomeReactor on 2008-01-12
Hi. Please open a terminal (Applications->Accessories->Terminal) and run:
```
gksudo nvidia-settings
```
Select the resolution you want if it's listed there. This should set the resolution to be persistent between reboots.

---

### Post by Waldo2020 on 2008-01-12
yes, that would work if the "nvidia" driver wasn't buggy. It doesn't read EDIDs, and has some strange ideas as to what legal modes are - defaulting to lowest resolution..
"nv" has no such problem.

---

### Post by wolfen69 on 2008-01-12
i had a hell of a time getting the new drivers to play nice. i have a 7300GS and for some reason i keep getting random lockups and other graphics glitches. this also happened on 2 other 7300 cards. i dont think it's coincidence that 3 different cards didnt like the new nvidia drivers. my cards use to work great with feisty, but i dont plan on going back to it.

i just use the default nv drivers and live with it. besides, i have a 20gb partion of xp that's just for 3Dgaming.

---

### Post by FlyingIsFun1217 on 2008-01-13
Isn't the nv driver software accelerated? I would really like it to be hardware accelerated (hence my asking this question).

I'll try changing it to be persistant through boots with the control panel again.

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-13
It's still doing the same thing...

I'm going to try uninstalling the Nvidia driver, and install an old one (did previously and will do again through envy, since it works), and see if that helps. Funny I have this issue on this card, since it's supposedly identical to the 6150 LE, which my desktop has (and works flawlessly with).

Grr
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-13
> **RomeReactor said:**
> Hi. Please open a terminal (Applications->Accessories->Terminal) and run:
```
gksudo nvidia-settings
```
Select the resolution you want if it's listed there. This should set the resolution to be persistent between reboots.

> **FlyingIsFun1217 said:**
> After changing the resolution to 1280x800 using the Nvidia control panel, the screen looks really nice. Once I restart the xserver though, it reverts right back to the vesa driver and back to 800x600.

Although now it's staying with the nvidia driver.

Like I said, I'll try using an older driver. As long as I get decent 3D performance (I mean, come on, it's a laptop :P), I'm fine with using older drivers.

FlyingIsFun1217 :)

---

### Post by FlyingIsFun1217 on 2008-01-13
Ugghhh... Same trouble through the older driver (although it always let's me choose 1280x800 in the nvidia settings manager now, which is nice).

Just though; If either my monitor or the driver is messing up what the screen resolution is using EDID, can't I just set what I want my resolution to be in the xorg.conf file, and then use the option "useEDID" "FALSE"? If so what would I need to do to give the driver my own EDID info (through the xorg.conf file)?

Tried it, it gives me 6 sort of screen viewports on my physical screen. Obviously I need to do something else to pass along the correct information. How would I do that? Say, setting it to 1280x800, refresh rate of 60, etc.?

Thanks again for the help!
FlyingIsFun1217

---

