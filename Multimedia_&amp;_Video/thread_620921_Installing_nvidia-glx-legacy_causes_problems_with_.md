---
title: "Installing nvidia-glx-legacy causes problems with screen resolution"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by tr333 on 2007-11-23
I installed the NVidia legacy driver (nvidia-glx-legacy) via the Restricted Drivers Manager.  After installing it wouldn't let me set the screen resolution above 800x600, when it had previously been at 1280x1024.  xorg.conf still seemed to contain 1280x1024 for a video mode, so I don't know why I couldn't select it from the GUI.  Uninstalling the driver via the Restricted Drives Manager seemed to put the resolution back to 1280x1024.

dmesg shows the NVidia driver being loaded:
```

[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
[   59.217591] nvidia: module license 'NVIDIA' taints kernel.
[   59.245836] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7185  Mon Apr  2 18:29:54 PDT 2007

```

---

### Post by tr333 on 2007-11-23
It seems to give me the 1280x1024 screen resolution when I add "HorizSync" and "VertRefresh" to the "Monitor" section in xorg.conf.  How do I determine the correct values for these?

---

