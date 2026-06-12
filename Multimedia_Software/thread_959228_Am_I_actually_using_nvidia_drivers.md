---
title: "Am I actually using nvidia drivers?"
date: 2008-10-26
forum: Multimedia Software
---

### Post by lemonsCC on 2008-10-26
Sorry it has been a long while since I played in the linux realm and this is probably a really silly question, but I would like to know how to know if I am indeed using the nvidia driver (nvidia-glx-new).  In the HardWare Drivers panel it says "In Use" but the enabled box is unchecked.

---

### Post by darthshak on 2008-10-26
Well, you should have nvidia-settings in /usr/bin if you have the nvidia drivers installed.

That said, I would recommend you to get the nvidia drivers off the Nvidia site. The drivers in the repo tend to be very old.

---

### Post by lemonsCC on 2008-10-26
running ```
sudo lshw -C display
```

gives me the results
```

*-display               
       description: VGA compatible controller
       product: NV31 [GeForce FX 5600]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia

```

With that said I am installing nVidia drivers now, from the site.

---

