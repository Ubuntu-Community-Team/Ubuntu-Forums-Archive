---
title: "Adjusting EDID to fix overscan?"
date: 2012-12-03
forum: Multimedia Software
---

### Post by manthony121 on 2012-12-03
I have a system running Ubuntu 12.04 with an Nvidia GeForce 8200 graphics card hooked up to a Sony Bravia 40" TV through an HDMI cable.  Since the recent upgrade to 12.04, the display has started to overscan, so the edges of the display are off the edge of the physical screen.  In earlier versions of the Nvidia X server configuration, there was a selection of overscan compensation.  That button is no longer available.

After reading many threads, and trying many drivers, I am starting to suspect that tweaking the settings in the EDID table may be necessary to fix the problem.  I have seen reference to an EDID editor that runs well under wine, that others have used (Phoenix).

Before I start digging into the format of the EDID table, and figuring what numbers may need to be tweaked, is there anything else I could look at?  Any tips on EDID wrangling?

The current NVIDIA Driver Version is 304.43.  Interestingly, the Display comes up on the Ubuntu "Displays" configuration utility as a Sony 32" (it is actually a 40")

TIA

---

### Post by BicyclerBoy on 2012-12-04
Overscan compensation still exists by a new name "ViewPortOut".

The best overscan correction is to set the TV to "justscan" or direct-pixel mapping. Every vendor has a diff name.

You can roll the driver back to 295.xxx, that's what I use.

Failing that the viewport setting is required, unfortunately nVidia decided we had to do it the hard way now..

(assuming DFP-1 is your affected display)..
```

nvidia-settings --assign CurrentMetaMode="DFP-1: 1920x1080 { ViewPortOut=1880x1040+20+20, ViewPortIn=1920x1080 }"

```
I believe it is possible to add to:
~/.nvidia-settings-rc

Or to /etc/X11/xorg.conf:
```
Option "MetaModes" "DFP-1: 1920x1200 { ViewPortIn=1920x1080, ViewPortOut=1880x1040+20+20 }"

```

Apparently the new nvidia-settings will have a GUI interface again..

---

### Post by mcduck on 2012-12-04
> **BicyclerBoy said:**
> 
The best overscan correction is to set the TV to "justscan" or direct-pixel mapping. Every vendor has a diff name.


+1 to this.

Adjusting this stuff from the computer's end can never give as good result as doing it from the display itself, if the display is scaling the image instead of mapping it pixel-per-pixel onto the display panel.

---

### Post by manthony121 on 2012-12-04
Firstly, thank you for your help.  I've done a little more digging, looking at forums related to overscan issues with the Sony Bravia HDTV series.  There are references to setting the display area to "FULL PIXEL", however, on my set, the only options are Normal, -1, and -2.  It is currently set to "Normal", and the other two settings make the overscan even worse!

Now, I'm finding indications that the FULL PIXEL option may appear with the right combination of display settings.  So, I will try fiddling with that next.

Regarding rolling back the driver: I tried that, and it fixed the overscan, but I lost the sound, which was another dragon that took some time to slay.  I am currently using the "post release update" driver, as the older ones (including the recommended, current one), will not recognize the display, shows it as a generic "laptop", and tells me that my driver is not new enough to support the nvidia-settings Display Configuration page.  I was hoping the newer driver would have the "correct overscan" button, but it doesn't.  The driver I'm using now at least identifies the display as a Sony, even if it gets the size wrong.

---

### Post by BicyclerBoy on 2012-12-04
The roll back suggested was meant to try versions in 295- 302 range...
It is possible it is to late to find or pin..I had to compile nvdia-
settings to match my driver version.

What version did you need up with ?
(I do **not** suggest trying nVidia installer method)

Some TVs require the elevated privilege of "professional" mode to allow direct-pixel mapping..(Pana plasma)
Some have:-
- pre-defined user preset restrictions (need custom preset)
- diff HDMI port settings (hdmi1 /== hdmi2)
- need a special name for port "PC input" or "PC"
- hidden in another obfuscated menu location/label
- cheap TVs don't have it..

---

### Post by manthony121 on 2012-12-08
nvidia-settings --assign CurrentMetaMode="DFP-0: 1920x1080 { ViewPortOut=1820x1020+50+30, ViewPortIn=1920x1080 }"

Wow.  Worked like a charm.  I did have to tweak the "ViewPortOut" settings a little more to get it to fit well, but the overscan is GONE!

Also, I did a little more research on the TV itself.  It is apparently too old to have a direct pixel mapping selection on the HDMI input.  It is a Sony KDL-40S2000.

So, now I'm off to learn a little more about "nvidia-settings" and "ViewPortOut".  Thanks for your help.

---

