---
title: "Mythfrontend Display Problem"
date: 2009-01-26
forum: Mythbuntu
---

### Post by Eric Boring on 2009-01-26
I am trying to use mythtvfrontend on a laptop with ubuntu 8.10 installed on it (via Wubi). When I open mythfrontend, the display gets messed up, as shown in the attached image.  Here are some other bits of information that suspect are related to this:

[LIST]I can't enable any of the desktop effects on this laptop now, but I had been using the medium desktop effects for a while before I noticed this problem. I think this problem occurred after I changed to no desktop effects.[/list][list]
I tried to do a print screen to grab this image, but the image that it grabbed was perfectly clear. I wound up taking this picture with a camera.
[/LIST]

Any ideas as to what I need to do to fix this?

Thanks!
-josh

---

### Post by jeremystaples on 2009-01-26
Hi Eric.  I take it this is a new install?  I'm new to mythtv, nythbuntu, and linux in general, but I had this problem on an 8.10 system I installed yesterday and resolved it to by deactivating the restricted hardware driver my onboard ATI Radeon 3200 and installing the latest one from here:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Not sure if you have ATI graphics, but if you do maybe that will work for you.

---

### Post by Eric Boring on 2009-01-26
Fastest Ubuntu Fix ever!

Actually, all I needed to do was disable the proprietary driver. (I'm not really interested in 3D graphics acceleration.) Mythtv works great now. Thanks!

---

### Post by Eric Boring on 2009-01-26
> **jeremystaples said:**
> Hi Eric.  I take it this is a new install?  I'm new to mythtv, nythbuntu, and linux in general, but I had this problem on an 8.10 system I installed yesterday and resolved it to by deactivating the restricted hardware driver my onboard ATI Radeon 3200 and installing the latest one from here:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Not sure if you have ATI graphics, but if you do maybe that will work for you.

Say, can anyone tell me how to thank jeremystaples and mark this thread as resolved? I can't find the appropriate buttons.

---

### Post by Def13b on 2009-01-26
> **Eric Boring said:**
> Say, can anyone tell me how to thank jeremystaples and mark this thread as resolved? I can't find the appropriate buttons.

Currently disabled unfortunately,

[http://ubuntuforums.org/showthread.php?t=1044714](http://ubuntuforums.org/showthread.php?t=1044714)

---

