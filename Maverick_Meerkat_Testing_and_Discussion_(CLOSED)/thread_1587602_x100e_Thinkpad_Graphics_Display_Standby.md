---
title: "x100e Thinkpad Graphics Display Standby"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mperry on 2010-10-03
Wondering if anyone has installed the RC on the Thinkpad X100e ultraportable. I upgraded the video drivers to the FGLRX driver to take advantage of better graphics speed. All packages are updated and this install was just done. When I let the screen blank out after 15 minutes or so using the screensaver application, the screen never does wake up again. I don't think I noticed this with the open source driver but I did see it on 10.4.1 previously. Any ideas why the screen goes completely away on this laptop?

Thanks a lot!

---

### Post by mperry on 2010-10-04
If you have an x100e and using the RC, there are a few things I've found after searching down the initial issues:

1. There is a new bios out dated August 2010 which fixes the power events when using the open source radeon driver. You can plug/unplug AC. Imagine that! :-).

2. The radeon driver now deals better with suspend/resume events with the new bios as well. Prior the screen backlight would kick on and then off and I was stuck power cycling. Hibernation appears to work fine. Just the suspend to ram seemed buggy on Maverick RC.

3. To get the internal mic working, you have to edit/add some lines to the /etc/modprobe.d/alsa-base.conf file

options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes

This appears to fix the internal mic. You have to reboot though.

4. The proprietary fglrx driver still does not deal well with suspend/resume events from what I can tell.

Hope that helps others trying to work things out with the driver.

---

