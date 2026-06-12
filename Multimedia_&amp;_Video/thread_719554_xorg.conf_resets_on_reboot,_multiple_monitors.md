---
title: "xorg.conf resets on reboot, multiple monitors"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by Roemer on 2008-03-09
Hello,

I'm running Ubuntu Gutsy 7.10 on my laptop, with a broken screen. The native resolution of that screen was 1280*800 and it has an Intel 915 chipset (Graphics Intel® Graphics Media Accelerator (GMA) 900) . At home I use an external Compaq CRT monitor, with a resolution of 1280*1024. Once a week I use a LCD monitor at work which I use at 1440*900.

If I boot, the resolution on the external monitor is very poor, something like 800 or even less. Then I replace /etc/X11/xorg.conf by a version I keep at my desktop, once made by the ubuntu LiveCD. Then I have to reboot, and manually set the resolution from 1280*800 to 1280*1024. To be able to do this, I first need to set the driver to i180 instead of the experimental intel driver.

If I reboot again, all the settings are reset.

To also be able to use the LCD monitor, i created two places which i can choose at "screens and resolutions". But then i do have to use the experimental driver; the i810 doesn't works.

If i've set everything ok for myself, and switch to another user, the resolution is low again. If I switch back, the resolution is again 1280*1024.

So: how can i prevent that xorg.conf is overwritten, make it for all users work and be able to switch fast between two external monitors (not connected at the same time)

---

### Post by Roemer on 2008-03-10
anybody?

---

