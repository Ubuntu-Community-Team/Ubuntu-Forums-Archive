---
title: "Can't raise resolution"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by lordhedgehog on 2006-07-13
I'm running an old NVIDIA GForce 2 DDR using the legacy drivers, and everything works....  almost.

For the last year the machine has been running Mandrake, and I just reformatted and put Ubuntu on.  I can't raise the resolution beyond 1600x1200.  I've manually added higher resolutions to xorg.conf, and even removed lower resolutions.  It stays at 1600x1200, and Settings->Display Settings continues to list lots of resolutions at 1600x1200 and below but nothing higher.

My only thought is that my monitor claims to only support 1600x1200, but I've run it for years at various higher resolutions.  I tried adding modelines for higher resolutions to the monitor portion of xorg.conf, but they appear to be ignored.

Any ideas on why Ubuntu insists it can't even try a higher resolution?

---

### Post by legesh on 2006-07-13
Did you see [this]("http://doc.gwos.org/index.php/ChangeResolution")

---

### Post by lordhedgehog on 2006-07-13
> **legesh said:**
> Did you see [this]("http://doc.gwos.org/index.php/ChangeResolution")

Yes, none of it worked.  I forgot to mention that I tried dpkg-reconfigure, but that link was where I figured out how to create custom modelines.

---

### Post by cacharreo on 2006-07-13
It could be possible to rise the resolution beyond 1600x1200 if you change the refreh rate of your monitor, but you must be sure that this one support it

dpkg-recongigure xserver-xorg   (monitor section in advanced mode)

---

### Post by lordhedgehog on 2006-07-13
Tried that too, didn't work either.

---

### Post by lordhedgehog on 2006-08-05
Three weeks late, but if anyone else with an NVidia card is having the same problems....

Try
Option "NoDDC" "true"

In the /etc/X11/xorg.conf

My monitor was lying about its supported resolutions.  Many monitors claim to not handle as high as they can actually go, and I knew this monitor could (and had) gone much higher.  

WARNING -- Check the specs from your monitor, and look at its horizontal and vertical refresh rates.  If you exceed those, you run the risk of breaking the monitor!

---

