---
title: "Radeon HD 2400 PRO tvout on Jaunty"
date: 2009-06-12
forum: Multimedia Software
---

### Post by spidie on 2009-06-12
Anyone had any success getting the TV out working on the Radeon HD 2400 PRO???

lspci shows 

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

I am using the restricted drivers and Catalyst Control Centre works fine and shows all the 3D stuff - so the driver is obviously loaded. I just don't see the TV as a monitor in there, just my primary monitor.

I've tried rebooting with just the TV attached (no monitor) and I don't get anything (this has worked for me before with other cards).

Any ideas? I also tried it with the envy driver with same effect (except catalyst didn't load) - I think the driver in envy is the same as the restricted driver in jaunty anyway.

I haven't touched my xorg.conf - it just has the standard stuff in there:

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
        Load    "dri"
        Load    "GLcore"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
EndSection
```


Thanks in advance,
Steve

---

### Post by spidie on 2009-06-19
Anyone?.... looks like I'll just have to keep plugging away... it's the only low-profile graphics card I have at the moment... so it's this or nothing.

---

### Post by gekaare on 2009-07-07
Just paste this in terminal

aticonfig --initial=dual-head --screen-layout=right

Change the layout to whatever.

Afterwards you can enable xinerama in control center if you wish 

sudo amdcccle

That last part didn't work for me, neither do playback or fullscreen flash and I think this card we've got is poor supported. Don't expect the world....

---

