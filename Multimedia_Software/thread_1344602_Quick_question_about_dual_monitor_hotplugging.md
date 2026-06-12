---
title: "Quick question about dual monitor hotplugging"
date: 2009-12-03
forum: Multimedia Software
---

### Post by humphreybc on 2009-12-03
Hey so at the moment I have dual monitors working fine with my laptop and an external Dell 24" LCD via HDMI. My laptop has an HD2600 in it, with the open source radeon driver. I'm using experimental xorg-edgers PPA, with a newer kernel (2.6.32-rc8 ) to enable 3D effects under my card (r600/r700). Anyway, that should be irrelevant - just background info.

When I plug in my monitor, nothing happens. I have to go to System > Preferences > Display, and the instant I click this it all gets set up and my wallpaper expands to the right, I can drag windows across... etc etc

When I unplug, nothing happens, I still have this big virtual space out to the right of my laptop screen where my mouse can get lost. But if I open up the Display menu again, it'll fix itself.

Is there a script or something that I can write, that basically uses xrandr to tell when HDMI is plugged in, and automatically do whatever opening the Display menu does to expand my desktop? And then the reverse when it's unplugged?

Thanks!
Benjamin

---

