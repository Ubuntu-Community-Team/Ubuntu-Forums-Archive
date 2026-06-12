---
title: "Screen Shearing Problem"
date: 2009-04-21
forum: Mythbuntu
---

### Post by tobiz on 2009-04-21
Posts: 18
	
I'm running the Nvidia 177.82 driver on my Mythbuntu 8.10 AMD2 64 system and get a momentary 'shearing' screen effect when watching TV and the scene pans; the effect does not happen unless the scene pans. The effect is as if the screen is monentarily out of sync about 2/3rds of the way down by a 'z' like shear between the top and bottom sections. The shear pattern is always in the same position and same size (but difficult to confirm since it only lasts milliseconds). The screen resolution reported by nvidia-settings is 1680x1050 for the HDMI connected Samsung 22 inch LCD TV. I've tried changing most things for both the nvidia driver and MythTV but the problem remains. Has anyone else seen this effect and is there a solution?

---

### Post by jbman on 2009-04-22
Put this in your xorg.conf

```

Section "Extensions"
      Option  "Composite"     "Disable"
EndSection

```

should stop the issue

---

### Post by tobiz on 2009-04-22
jbman,
Thanks, will try.

---

### Post by tobiz on 2009-04-23
> **jbman said:**
> Put this in your xorg.conf

```

Section "Extensions"
      Option  "Composite"     "Disable"
EndSection

```

should stop the issue
Excellent!  That seems to fix it both for SD & HD TV. Thanks.

---

