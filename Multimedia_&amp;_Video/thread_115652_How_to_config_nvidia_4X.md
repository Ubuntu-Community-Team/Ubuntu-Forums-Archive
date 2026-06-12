---
title: "How to config nvidia 4X"
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by Omnios on 2006-01-11
Hi I have a 8x card but my motherboard only supports 4x. I installed the nvidia-glx package and enabled it but am not getting any resuts from glxgears, its spinning but has no output. I just did a reinstall and glx was working before so the only thing I could think about was the 8x.
 
 ANy help would be apreciated.

---

### Post by Omnios on 2006-01-11
Im having config broblems there is some information I just noticed some odd stuff.

 ```
tom@reboot:~$  lsmod |grep -i agp
intel_agp              21276  1
agpgart                32328  2 intel_agp,nvidia
tom@reboot:~$

```

```
tom@reboot:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
tom@reboot:~$

```

```
tom@reboot:~$ cat /proc/driver/nvidia/cards/0
Model:           GeForce4 MX 4000
IRQ:             11
Video BIOS:      04.18.20.36.00
Card Type:       AGP
tom@reboot:~$

```

---

