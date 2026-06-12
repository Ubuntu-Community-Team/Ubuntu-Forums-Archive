---
title: "Disable EDID with Intel Driver"
date: 2009-05-04
forum: Multimedia Software
---

### Post by TRON NZ on 2009-05-04
Hi,

Is it possible to disable the EDID detection on the i2c bus with the latest jaunty Intel driver within my xorg.conf. I have tried a number of options to disable the EDID and have also tried to force a modeline without any luck. My understanding is the option to disable EDID was removed from the intel driver?

The screen with the problem is a small 7" lcd touch screen, unbranded. This is the same problem when using KVM units which dont report there EDID, however I have not found a work around.....

Below is my Xorg log:

(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): Resizable framebuffer: not available (1 3)
(II) intel(0): Output VGA disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Thanks,

Tron

---

### Post by marleaux on 2009-11-12
Hi TRON NZ,

where you able to find a solution for your problem? If yes, please let me know.[-o<
(That problem drives me nuts.)

best regards,
marleaux

---

### Post by marleaux on 2009-11-17
This solved my problem:
[http://ubuntuforums.org/showthread.php?t=1292212](http://ubuntuforums.org/showthread.php?t=1292212)

---

