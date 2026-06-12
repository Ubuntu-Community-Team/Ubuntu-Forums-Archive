---
title: "HDMI resolution unable to change to 1920x1080 with intel n2600 processor"
date: 2014-02-17
forum: Multimedia Software
---

### Post by Rogerchen on 2014-02-17
Hi,

Although i had probe the driver for my cedarview chipset with n2600 processor, which the VGA module is shown as below:

kernel moduls: cedarview_gfx

But my HDMI still unable to change resolution to 1920x1080 while there is no problem when using VGA.
Is there any direction to troubleshoot this issue? HDMI works great on win7 but cannot work on either saucy or precise.

Thanks a lot.

---

### Post by Rogerchen on 2014-02-18
Well, i think this issue could be something with LVDS. For instance when my LVDS detection has been turned off from OS side by typing video=LVDS-1:d in /etc/default/grub,  my HDMI cannot detect the signal anymore. And the maximum resolution that HDMI able to output is the same with LVDS. Does it close to Hardware issue?

---

