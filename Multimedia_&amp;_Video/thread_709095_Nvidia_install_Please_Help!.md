---
title: "Nvidia install Please Help!"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by reaper739 on 2008-02-27
I've been trying to install the Nvidia driver for a week now, and I can't make the nvidia-glx-new install properly.  I've tried a half dozen different how-to guides, and I think I've mucked up my video driver pretty well.  anyone have any advice to fix this?

---

### Post by em3raldxiii on 2008-02-27
You are probably in luck.  There is a fellow named Alberto Milone who has been a very positive force here on the 'forums, and he has developed a little program that you need :D

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Hope it helps!

---

### Post by renzokuken on 2008-02-27
to restore your grafix to a failsafe state run

```
sudo dpkg-reconfigure xserver-xorg
```

selecting the **vesa** driver and appropriate resolutions, leaving the rest as default.

then you should have a working GUI from which you can repair/remove the nvidia driver and try again

---

### Post by reaper739 on 2008-02-27
- To em3raldxiii-
I tried to run the envy program, but I got a dpkg error; my computer could not process msttcorefonts (I don't even know what 'msttcorefonts' is).  Any idea what went wrong?

-To renzokuken-
Your advice at least restored my GUI, so that's a step in the right direction.  Thanks!

---

### Post by renzokuken on 2008-02-27
i really wouldn't use envy if i was you, it's not ideal and does things that cannot be undone easily.

now you have a working gui, try installing the drivers through System -> Admin -> Restricted Drivers Manager. It may be that you have to undo everything you did previously, but i cant say how without knowing what you did

FYI, msttcorefonts is a package in synaptic containing various Windows fonts......

---

### Post by reaper739 on 2008-02-27
I tried to run the restricted drivers manager, and I received this error message:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-xconfig

Thanks on the FYI, though.

---

