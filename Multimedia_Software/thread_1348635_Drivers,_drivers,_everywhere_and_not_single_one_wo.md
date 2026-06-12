---
title: "Drivers, drivers, everywhere and not single one works (ATI HD 3400)"
date: 2009-12-07
forum: Multimedia Software
---

### Post by mdingler on 2009-12-07
For the sake of more compatibility with my co-workers, I've recently re-installed Ubuntu (Karmic, 386) on my work laptop. (Not entirely true, as this also should prevent me from fiddling too much with 'minimal' desktops).

Now some basic effects support wouldn't be bad, mostly for Docky, some transparency effects and a reasonable Expose clone. Now I've tried all three drivers available to me, each one has one or more flaws.

Basic Setup:
Sony Laptop FW190 - 1600x900 display, ATI Mobility HD 3400
Sony 23" LCD - 1920x1200, attached via HDMI cable
preferred configuration: laptop screen turned off.

Driver woes:
Radeon: Multiple displays work fine, but no effects, fan a bit too loud
FGLRX: Can't truly turn laptop screen off, it's just set to black (and a rather "bright" one, too). desktop effects work just fine.
Radeon HD: All attached displays appear as unknown, major flicker on external display, when I try to have just the external display running (via Gnome display preferences), I get no display at all (have to restart from command line)


FGLRX/Radeon driver ran with the bog-standard (near-empty) xorg.conf, for Radeon HD I had some options enable:

```
Section "Device"
       Identifier  "Radeon 3400"
       Driver      "radeonhd"
       Option      "DRI" "on" 
       Option      "DynamicPM" "on"
       Option      "ClockGating" "on"
       Option      "AccelMethod" "EXA"
       Option      "ScalerWidth" "2048"
       Option      "EnablePageFlip" "on"
       Option      "RenderAccel" "on"
       Option      "AccelDFS" "on"
EndSection
```

If it's possible to manually and truly turn off displays with the FGLRX driver, this would possibly be the easiest way out. I'd prefer a true open source option, though, so maybe there's a newer, experimental version or some ATI driver somewhere?

---

### Post by Yellow Pasque on 2009-12-07
You'll probably want to stick with fglrx for now, because it will give you the best battery life. For open-source drivers, Option "ForceLowPowerMode" might interest you if you don't do a lot of demanding tasks.

However, if you want to check out open-source 3D, here's the recipe:

1. Purge fglrx: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
2. Install a recent kernel and boot into it: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/)
3. Add the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
4. Restart X (log out). When you log back in check glxinfo and glxgears.

This will give you open-source 3D (enough to run desktop effects and some games)

---

### Post by mdingler on 2009-12-07
Well, battery life isn't an issue per se, as I mostly use the laptop in an office. The only power management issue would be the fan speed, as this can get somewhat annoying.

And thanks for the recipe, it seems to be working right now. Some of the effects are actually faster than with the FGLRX drivers, at least I don't get that silly delay when resizing windows anymore.

---

