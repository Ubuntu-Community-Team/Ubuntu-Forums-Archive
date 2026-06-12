---
title: "Ubuntu 16.04 AMD radeon HD 6750M support Question"
date: 2017-05-10
forum: Multimedia Software
---

### Post by bradleybare on 2017-05-10
Thanks for helping.

I am having trouble with GPU support for the above GPU.

At first, I had to disable to GPU with radeon.modeset=0 to get ubuntu to boot correctly, otherwise it would freeze at the last boot stage.

Now I want to know if I can install the correct GPU driver and get rid of radeon.modeset=0 and change it to radeon.modeset=1 so my GPU is used instead of the integrated graphics.

I would like to use my GPU because I am sure that will help with battery life, etc.

I also can't get the drivers to show in additional drivers because the GPU is disabled. Is there a way to enable the GPU after booting my system?

Thanks!

---

### Post by walterav on 2017-05-12
Try to look for a bios/efi setting to force one kind of GPU so the other one gets disabled. Normally the opensource intel/amd drivers automatically load and should work fine, but I'm not aware of any dual graphic notebook either intel&amd/nvidia that behave as good as the windows/mac OS counterparts.

However the proprietary AMD driver (deprecated for you gpu) will only give you better opengl performance but worse compatibility with video decoding or other display/resolution related tools, it should be available in the "Additional Driver" tool.

If you would like more technical support, you need to post more info about your hardware like brand/model and the following terminal command output will help.

```

uname -a #shows kernel version
lsb_release -a #shows ubuntu version
lspci -nn #shows devices and id's
cat /proc/cpuinfo #shows cpu

```

---

