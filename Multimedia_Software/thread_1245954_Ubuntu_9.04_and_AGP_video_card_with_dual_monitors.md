---
title: "Ubuntu 9.04 and AGP video card with dual monitors"
date: 2009-08-21
forum: Multimedia Software
---

### Post by trb61 on 2009-08-21
Hi,

I have a Intel P4 machine with an AGP8x slot.

I want to use dual monitors in my system.

I tried SAPPHIRE HD 2400PRO AGP, however, I got a lot of problems when enabling dual monitors.

I don't need a very powerful video card since I am developing non-GUI software applications.

What AGP8x video card can you suggest to install in Ubuntu 9.04 which will smoothly detect the dual monitors and enable them ?

It may have one VGA and one DVI outputs. (2 in total)

Thanks.

---

### Post by markbuntu on 2009-08-21
WHich driver are you using with that card?
The driver from hardware manager (9.4) had some issues with randr1.2 which made enabling dual monitors difficult but that is fixed with the latest 9.7 or 9.8 driver from ati. No need to spend any money, just get the latest driver.

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.1&lang=English)

Be sure to remove the driver you are using before installing a new one. You can configure dual monitors easily with the Catalyst Control Center which comes with the driver.

---

