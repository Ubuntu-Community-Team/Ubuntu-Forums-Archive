---
title: "Few resolutions available with ATI card"
date: 2009-01-08
forum: Multimedia Software
---

### Post by muadnu on 2009-01-08
I just installed Intrepid using Wubi on my mom's laptop (a Sony Vaio VGN S350F) but cannot get the video card to work quite well. The video card model as per running "lspci | grep VGA" is
```
ATI Technologies Inc M9+ 5C61 (Radeon Mobility 9200 (AGP)) (Rev 01)
```

The problem is that I only see resolutions of 1024x768 and down on System->Preferences->Screen Resolution. In the past I would have fixed this through the xorg.conf file, but since now I think things are being done differently, I'm not sure this is the right way. In particular, the xorg.conf file is almost empty (there is no list of available resolutions there).

The laptop's native resolution 1200x800 

I'm not sure how to fix this.

---

### Post by sonu 1807 on 2009-01-08
Open Terminal and type

sudo apt-get install envyng-core

Then sudo envyng -t

follow instructions... appropriate driver will be installed

---

### Post by muadnu on 2009-01-08
I didn't work. I run it but it rendered the video unusable. Maybe the video card is too old? After uninstalling the ATI driver I was left with resolutions only up to 800x600.

---

### Post by muadnu on 2009-01-08
I didn't work. I run it but it rendered the video unusable. Maybe the video card is too old? After uninstalling the ATI driver I was left with resolutions only up to 800x600.

---

