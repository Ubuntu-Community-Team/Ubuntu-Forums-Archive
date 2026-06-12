---
title: "640x480 but with full Compiz - NVIDIA Monitor Detection Issue?"
date: 2009-01-21
forum: Multimedia Software
---

### Post by bzoomer16 on 2009-01-21
I have Ubuntu 8.10 AMD64 and I've been running at 1680x1050. The problem is I'm stuck at 640x480 (or lower options) because any time I unplug my KVM switch, it does something weird and like resets the xorg.conf. I still have all my 3D acceleration with Compiz and stuff, but it just won't set above 640x480 through the nvidia-settings manager, the Ubuntu screen manager, or even manually editing the xorg.conf myself. I've tried envyng multiple versions multiple times, but nothing's changing. The part that I can't figure out is that after I turned the computer off, unplugged the monitor, set up another computer in the same place, plugged the monitor back in, and turned it back on, what changed? What would even affect that?

This used to happen before I reformatted my computer from 32-bit Hardy to move to 64-bit Intrepid, but I can't fix it the same way I used to by "sudo dpkg-reconfigure xorg-xserver" or through "sudo nvidia-xconfig". I have an nVidia 8400 GS (not sure on the letters, but it IS an 8400)

Thanks for any help or assistance you can provide, as I've spent several hours Googling and searching this forum. :)

---

### Post by VastOne on 2009-01-22
> **bzoomer16 said:**
> I have Ubuntu 8.10 AMD64 and I've been running at 1680x1050. The problem is I'm stuck at 640x480 (or lower options) because any time I unplug my KVM switch, it does something weird and like resets the xorg.conf. I still have all my 3D acceleration with Compiz and stuff, but it just won't set above 640x480 through the nvidia-settings manager, the Ubuntu screen manager, or even manually editing the xorg.conf myself. I've tried envyng multiple versions multiple times, but nothing's changing. The part that I can't figure out is that after I turned the computer off, unplugged the monitor, set up another computer in the same place, plugged the monitor back in, and turned it back on, what changed? What would even affect that?

This used to happen before I reformatted my computer from 32-bit Hardy to move to 64-bit Intrepid, but I can't fix it the same way I used to by "sudo dpkg-reconfigure xorg-xserver" or through "sudo nvidia-xconfig". I have an nVidia 8400 GS (not sure on the letters, but it IS an 8400)

Thanks for any help or assistance you can provide, as I've spent several hours Googling and searching this forum. :)

Sounds like you lost your nividia driver... Can you see if there is a nividia x server settings under applications system tools?  Have you recently had a kernel or driver update?

---

### Post by bzoomer16 on 2009-01-22
> **VastOne said:**
> Sounds like you lost your nividia driver... Can you see if there is a nividia x server settings under applications system tools?  Have you recently had a kernel or driver update?
Well it appears to be installed, and there is the nVidia server settings menu both in the GUI and the terminal "nvidia-settings". I haven't had any recent updates that I think affected this, it always does this when I unplug my monitor, it's just that now I can't fix it the same way I used to. I know it's working, otherwise 3D Compiz Fusion acceleration wouldn't be working.

---

### Post by markbuntu on 2009-01-22
I know the ati drivers have a force-monitor option that can prevent that sort of thing. You could probably do the same with the nvidia driver or in xorg.conf but I am not very familiar with those drivers.

---

### Post by bzoomer16 on 2009-01-25
Yeah I don't know how to do that... Google didn't help me.

---

