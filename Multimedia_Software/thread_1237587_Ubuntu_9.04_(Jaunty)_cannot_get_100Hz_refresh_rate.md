---
title: "Ubuntu 9.04 (Jaunty) cannot get 100Hz refresh rate @ 1600x1200 Resolution on CRT"
date: 2009-08-11
forum: Multimedia Software
---

### Post by kosaiy71 on 2009-08-11
I am doing visual research and need a [high resolution[IMG]http://images.intellitxt.com/ast/adTypes/2.gif[/IMG]]("http://www.nvnews.net/vbulletin/showthread.php?t=137195&highlight=jaunty#")/high refresh rate combo.  I have an older machine with Fedora Core 3 and a 6600 GT nVidia [chipset]("http://www.nvnews.net/vbulletin/showthread.php?t=137195&highlight=jaunty#") video card running at these specs (1600x1200 @ 100Hz) on the CRT (ViewSonic G225f) monitors I use. 

However, for my new machine (Ubuntu 9.04) even editing the xorg.conf file with modelines and turning off EDID doesn't seem to allow me to select 100Hz with a 1600x1200 resolution. I can add certain combinations (1280x1024 @ 118Hz, etc.) to the modelines and metamodes to get them to show up as options in nvidia-settings. My current [video]("http://www.nvnews.net/vbulletin/showthread.php?t=137195&highlight=jaunty#") card on the Ubuntu machine is a 8400 GS GeForce 512MB from [ASUS]("http://www.nvnews.net/vbulletin/showthread.php?t=137195&highlight=jaunty#"). I have the 173 glx drivers (I have tried 180.xx driver as well) for my machine as well. Can someone help me set up this refresh rate for this certain resolution? I seem to be capping out at 85Hz at this resolution.

---

### Post by markbuntu on 2009-08-12
That is most likely a limitation of the driver. You should ask the nvidia devs about it.

---

### Post by kosaiy71 on 2009-08-12
Figured it out. It was a problem with the drivers.  I upgraded to the 185.xx driver, synaptic manager only has up to 180.xx so I installed manually from the nVidia website package. Thanks.

---

