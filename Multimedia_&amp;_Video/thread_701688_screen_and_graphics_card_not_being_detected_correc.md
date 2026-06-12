---
title: "screen and graphics card not being detected correctly"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by SRG8 on 2008-02-19
im a linux newbie and a couple days ago i tired setting up a second screen but it never worked, instead when i rebooted a pop up tells me the screen and graphics card cannot be detected correctly forcing me into low resolution and graphics mode (600x800). i managed to fix the low resolution problem and i'm now back to the correct resolution, however im still stuck in low graphics and the same message pops up everytime time i reboot. i tried downloading envy but that didnt work and according to synaptic i have the appropriate drivers installed for my graphics card.
is there anything else i can do to try and change from the default driver "vesa" to my actual one, changing in it in the screen and graphics manager doesnt work, it just gets reset to the vesa driver everytime.

please anyone?

---

### Post by kyphi on 2008-02-19
It would be helpful if you declared what graphics card you have installed.

---

### Post by SRG8 on 2008-02-19
sorry, im in a hp pavilion v2000 and it has a NVIDIA GeForce Go 7200 video adapter and an intel 945 card. the drivers i have installed are: xserver-org-video-i810 and xserver-org-video-intel, nvidia-glx-new, nvidia-glx-new-dev and xserver-org-video-nv.

i dont know what i could've done, it was working beautifully before.

---

### Post by kyphi on 2008-02-20
The only way I know of changing the vesa driver to nvidia is to go through the long path of reconfiguring the graphics adapter. ```
sudo dpkg-reconfigure xserver-xorg
```

Before you do that, you could try  ```
sudo nvidia-glx-new-config enable

```

---

### Post by SRG8 on 2008-02-21
thnx, i see why you meant long path, i managed to change the driver and i dont get that low graphic mode pop up anymore. however when i went into appearance to enable my custom visual effects, i was not able to select anything but the lowest option of no desktop effects.
what do i need to do now? did i do something wrong?

---

### Post by kyphi on 2008-02-21
If you now have your nvidia graphics adapter set up you should have a menu entry in Applications, System Tools, NVIDIA Settings.  You can make adjustments there.

I do not have Appearance, Desktop effects on my menus.

---

