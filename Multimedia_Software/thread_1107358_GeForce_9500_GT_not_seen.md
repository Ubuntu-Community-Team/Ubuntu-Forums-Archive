---
title: "GeForce 9500 GT not seen"
date: 2009-03-26
forum: Multimedia Software
---

### Post by ewe on 2009-03-26
Greetings! I have an hp which came with a GeForce 6150SE nforce 430 preinstalled. I was recently given a new GeForce 9500 GT.

I would like to use this card for its HDMI capabilities.

I installed the new card, installed the nvidia accelerated graphics driver version 180 (got that going), I did dpkg-reconfigure xserver-xorg went through that process, but I cannot get the computer to read the new card.

Any help would be greatly appreciated.

Thanks,
ewe

---

### Post by norwoods on 2009-03-26
could you express this  in other words, "but I cannot get the computer to read the new card."
open System-->Administration-->Hardware Drivers.
if there is an active video driver, click on it and then click Deactivate
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

---

### Post by wolfen69 on 2009-03-26
you have to disable the preinstalled video card first, in the BIOS.

just in case you are not aware of how to get into the BIOS, just hit del, F2, or F10 (just hit all 3 real quick) at initial bootup. then navigate to integrated peripherals (or something similar) and disable onboard video. hit F10 to save, then reboot and ubuntu should see the new video card. i have the exact same card and it works perfect for me.

---

### Post by ewe on 2009-03-27
> **wolfen69 said:**
> you have to disable the preinstalled video card first, in the BIOS.

just in case you are not aware of how to get into the BIOS, just hit del, F2, or F10 (just hit all 3 real quick) at initial bootup. then navigate to integrated peripherals (or something similar) and disable onboard video. hit F10 to save, then reboot and ubuntu should see the new video card. i have the exact same card and it works perfect for me.Thanks wolfen69, that worked.

For those that may have the same issue, its important to change the setting in the bios before installing the upgrade card. Otherwise the default will remain. I found this out the long way.

Also, when changing the nvidia x server settings, you must do it as root
```
sudo nvidia-settings
```in order to save the new config file.

The monitor looks amazing via HDMI. I didn't expect it to look this good. Now I have to work on getting my digital audio going.

Someone may mark this thread as "SOLVED"

---

