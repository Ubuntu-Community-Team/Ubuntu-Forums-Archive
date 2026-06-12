---
title: "Can't install drivers for XFX Radeon R7 250A ZLF4."
date: 2019-04-07
forum: Multimedia Software
---

### Post by prokopcampos on 2019-04-07
Trying to install the drivers for my video card I've runned into several dead-ends: amdgpu dkms failed for running kernel, after I reverted the kernel to one that is comproved to work with these drivers (4.15.0-45) came the log in screen loop and after the re-configuration/uninstallation and installation of lightdm came (literally) nothing: black screen with a white undescore flickering, I can't even type anything in there. Then i twinkled around in the GRUB, some log in screen appears. And it's also looped. Went to the terminal with Ctrl+Alt+F3 in the log in screen and uninstalled the drivers and rebooted to normal Ubuntu, fully working.
Can anybody help me to install these drivers?

---

### Post by Autodave on 2019-04-13
Were you having a particular problem with the way the graphics card was running before you tried all of this? 'buntu comes pretty much ready to use the Radeon cards without adding any other driver.

---

