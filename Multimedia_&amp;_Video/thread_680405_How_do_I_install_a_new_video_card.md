---
title: "How do I install a new video card?"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by prickett on 2008-01-27
Hi,
My ATI card just died and I installed an old Nvidia Geforce2 I found laying around.  When I try starting Ubuntu it complains about the video driver being incorrect.  I manually edited xorg.conf to try to make my new card a VESA, but get the same video driver error.  

I've seen suggestions to use various utilities, but they seem to be fore folks already successfully in Ubuntu's gui.

Can anyone point me in the right direction (using small words that my Noobie brain can understand)?  

TIA

---

### Post by tommcd on 2008-01-28
Boot to recovery mode from the grub menu and type at the terminal prompt <sudo dpkg-reconfigure xserver-xorg>. This will take you through a long series of questions. You can just choose the defaults for all, say no when asked if you want to use the frame buffer, select "nv" for the driver, and at the end select your monitor's refresh rates. Then type reboot at the end. This will get you 2D graphics. For the nvidia 3D driver, first back up your now working xorg.conf like this <sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak> in the terminal (applications >accessories > terminal). Then follow this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
Or install the nvidia driver by going to system >administration > restricted drivers manager, and install it from there.
And welcome to the ubuntu forums!

---

### Post by prickett on 2008-01-28
Thanks, once I selected VESA as my card rather than NV it worked like a charm!

---

### Post by tommcd on 2008-01-28
> **prickett said:**
> Thanks, once I selected VESA as my card rather than NV it worked like a charm!

For a nvidia video card you will likely get better performance by choosing "nv". That's a lowercase "nv". Remember, linux is case sensitive. Then for 3D graphics follow the advice in my last post for the nvidia driver.

---

