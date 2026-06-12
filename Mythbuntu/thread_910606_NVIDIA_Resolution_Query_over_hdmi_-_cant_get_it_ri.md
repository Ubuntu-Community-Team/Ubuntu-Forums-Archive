---
title: "NVIDIA Resolution Query over hdmi - cant get it right"
date: 2008-09-04
forum: Mythbuntu
---

### Post by bob808 on 2008-09-04
I have an onboard nvidia 8200 gfx with my motherboard, and I have installed 8.10 alpha 4.

The standard install worked with the generic driver, but I installed the nvidia 177.67 driver to get full support for my chipset.

Now I have a screen that shows some overscan where some detail is lost off the edge of the tv.

I am trying to connect via hdmi to a 720p/1080i television (samsung 32") so would like to get a full 720p resolution, but the best I am offered is 800x600 in the nvidia panel.

Anyone know if there is anything I can do to get this sorted?

thanks

bob808

---

### Post by ctucker10 on 2008-09-07
I had a problem like that and fixed it by manually editing my /etc/X11/xorg.conf file.

In the "Screen" section, on the "Modes" line, I added the resolution that I needed, 1360x768 in my case.  Saved the file, then restarted gdm: sudo /etc/init.d/gdm restart

Hope this helps.

---

