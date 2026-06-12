---
title: "Color Shifts in 8.10 Video Display"
date: 2008-12-14
forum: Multimedia Software
---

### Post by dlfuller on 2008-12-14
I have a new installation of 8.10 using the proprietary hardware driver nVidia accelerated graphics driver (version 177) for a GeForce 8500 GT (rev a1) graphics card.

Displayed colors seem fine for the desktop and most applications.  But video color is all screwed up with drastic color shifts. The strange part is just opening System > Administration > nVidia X Server Settings immediately corrects the colors.

I did make a change earlier to the nVidia X Server Settings > X Screen 0 to increase the Brightness setting.  And, then the Save Current Configuration button in the nVidia-Settings Configuration.

After quitting a video application the screwed up colors will return when the application is restarted later. Again the step of simply opening the nVidia X Server Settings brings the colors back to normal and that also includes the adjustment in the Brightness setting.

I don't understand why the difference between video and other graphics to the X Server, but assume some configuration file is not being loaded. And, it is not a codec problem since only opening X Server Settings will immediately correct the colors.

Suggestions to resolve this would be appreciated.

---

