---
title: "nVidia kernel module in gutsy"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by rad-x on 2007-10-19
I upgraded from feisty to gutsy tonight after removing my manually installed nvidia drivers (100.14.xx) which I needed for my geforce 8600 gts to work. After I installed nvidia-glx-new I still couldn't run X with nvidia-drivers. 

I think I figured out the problem: I found out when (re)loading the module the following line appears in the syslog:

```
NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
```

I don't know why this version of the drivers are loaded. What can be the cause for this?

---

