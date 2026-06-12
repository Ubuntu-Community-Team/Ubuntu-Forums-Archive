---
title: "Can this card handle xgl or compiz???"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by shane634 on 2006-10-11
Linux noob here. Just wondering if this card can handle the new stuff. I don't really think it will, but never hurts to ask.  nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) is the card. I know it is old and I should upgrade, but hey it works. Thanks for any and all replies.

---

### Post by catanzag on 2006-10-11
It should be a problem of accelerated driver for card, but according to the following last nvidia drivers README 

```

Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.


    NVIDIA chip name                      Device PCI ID
    ----------------------------------    ----------------------------------
    RIVA TNT                              0x0020
    RIVA TNT2/TNT2 Pro                    0x0028
    RIVA TNT2 Ultra                       0x0029
    Vanta/Vanta LT                        0x002C
    RIVA TNT2 Model 64/Model 64 Pro       0x002D
    Aladdin TNT2                          0x00A0
    GeForce 256                           0x0100
    GeForce DDR                           0x0101 
    Quadro                                0x0103
    GeForce2 GTS/GeForce2 Pro             0x0150
    GeForce2 Ti                           0x0151
    GeForce2 Ultra                        0x0152
    Quadro2 Pro                           0x0153

```

your model is still supported in the legacy driver,.
I think that if you have installed and configurated nvidia-glx-legacy package, most of the new effects in compiz will work without affecting too much the system (I preferred, however, to disable some of them, though I have an accelerated GeForce4)

Regards and have a good job!!

---

