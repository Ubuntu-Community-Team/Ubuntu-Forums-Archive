---
title: "I deleted /usr/lib/dri how can I get it back?"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by jaywhy13 on 2006-11-12
Hey I was trying to make some symlinks and was moving my fingers a bit too fast.... "rm -r /usr/lib/dri... ENTER" ooops... is there neway I can get back that directory... I know it was stupid but I was trying to get dri enabled, so I can reinstall xgl... I'm using Edgy now. I have inspiron 9400 x1400 ati video card (256 mb)

---

### Post by catlett on 2006-11-12
rm is just what it says, remove. It's gone. You need to reinstall the package that put dri in /usr/lib to begin with. To find out the package that /usr/lib/dri came with, enter 
```
dpkg -S /usr/lib/dri
``` When it returns the package you can apt-get it, or what I would do,  open Synaptic package manager, search for the package  and select 'reinstall package'. Synaptic is an apt-get front end but in this instance I like the fact hat it says 'reinstall'. It may mean nothing but that is what you want, to reinstall the package. You don't want apt-get to return 'package already installed'

---

### Post by kerry_s on 2006-11-12
Try reinstalling xserver-xorg or xserver-xorg-core. I tried zipping it up for you but it's to big to upload.

---

### Post by jaywhy13 on 2006-11-13
Reinstallation of xorg-driver-fglrx is not possible, it cannot be downloaded.

---

