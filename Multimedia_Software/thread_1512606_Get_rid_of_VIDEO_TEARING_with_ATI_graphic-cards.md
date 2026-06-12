---
title: "Get rid of VIDEO TEARING with ATI graphic-cards"
date: 2010-06-18
forum: Multimedia Software
---

### Post by kopiwe on 2010-06-18
Install the SMPlayer video player (A frontend for the great mplayer)

```
sudo apt-get install smplayer
```Go to:
*Options > Preferences - (Video)*
 
And change *"Output driver"* to: "**gl (fast - ATI cards)**"


Play a video.
Hope this works for you!

*(only tested with the proprietary fglrx video driver from ati - installed through "System > Hardware Drivers")*

---

