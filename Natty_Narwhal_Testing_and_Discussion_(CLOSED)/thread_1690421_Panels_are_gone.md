---
title: "Panels are gone"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 1/0 on 2011-02-18
I've had natty now for a few weeks and things were ok. Just the regular minor bugs but then yesterday after updating and rebooting, the panels stopped loading. Alt + F2 doesn't work but Ctrl + Alt + T does. I can manually start gnome-panel.

The FAQ mentions 3D drivers. My laptop is an Aspire One A110.

In xorg.0.log there's warnings when loading /usr/lib/xorg/modules/drivers/intel_drv.so and its falling back to first vesa, then fbdev and lastly to fbdevhw. 


lsmod shows i915 and the xorg-server-video drivers seems to be installed. Glxgears works at about 61 FPS.

Halp plz!

---

