---
title: "How to enable direct rendering?"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by echo $USER on 2006-07-18
How do I do this?

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6800 GS/PCI/SSE2

---

### Post by tseliot on 2006-07-18
1) Post the output of:
```
dmesg | grep NVIDIA
```

2) Which method did you use to install the Nvidia driver?

3) Are you using XGL?

---

### Post by echo $USER on 2006-07-18
> > dmesg | grep NVIDIA
[4294690.649000] nvidia: module license 'NVIDIA' taints kernel.
[4294690.653000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006

I installed the latest from nvidia.com, by stopping gdm, then running the shell script.  Alos this is the third kernel I have compiled, currently running 2.6.17.4.

I do not know if I am using XGL.  How do I find out?

Also, here is my module section of xorg.cong...

> Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Thanks for the help!  Oh, and nice website by the way.

---

### Post by tseliot on 2006-07-18
> **echo $USER said:**
> I installed the latest from nvidia.com, by stopping gdm, then running the shell script.  Alos this is the third kernel I have compiled, currently running 2.6.17.4.
Your kernel might be the problem.

Can you post the output of this command:
```
cat /boot/config-`uname -r` | grep "NVIDIA"
```


> **echo $USER said:**
> I do not know if I am using XGL.  How do I find out?
If you don't know what it is you're definitely not using it

---

### Post by echo $USER on 2006-07-18
> > cat /boot/config-`uname -r` | grep "NVIDIA"
CONFIG_AGP_NVIDIA=m
CONFIG_FB_NVIDIA=m
CONFIG_FB_NVIDIA_I2C=y

I have a eVGA 6800GS CO PCIe if that helps.

Thanks again for all the help...

---

### Post by echo $USER on 2006-07-19
Do you think the problem could be that i did not uninstall the nvidia driver to the default kernel once upgrading to 2.6.16?  I installed the driver from the repos orginally, but once upgrading the kernel to 2.6.16, I installed the latest from nvidia's site.  Same as when I upgraded to 2.6.17.  Thanks.

---

### Post by tseliot on 2006-07-19
> **echo $USER said:**
> Do you think the problem could be that i did not uninstall the nvidia driver to the default kernel once upgrading to 2.6.16?  I installed the driver from the repos orginally, but once upgrading the kernel to 2.6.16, I installed the latest from nvidia's site.  Same as when I upgraded to 2.6.17.  Thanks.

If you didn't remove the driver from the repos try this:
```
sudo apt-get --purge remove nvidia-kernel-common
```

It will ask you to remove several packages.


Then reinstall the Nvdia driver from the Nvidia installer

---

### Post by echo $USER on 2006-07-20
I have noticed that at UDSF the installation technique for installing the driver differs from the instructions at nvidia.com.  Nvidia states to just run sh N*; where you guys say to extract it and etc.  Is there any performance increases from the different install techniques?

---

### Post by tseliot on 2006-07-20
> **echo $USER said:**
> I have noticed that at UDSF the installation technique for installing the driver differs from the instructions at nvidia.com.  Nvidia states to just run sh N*; where you guys say to extract it and etc.  Is there any performance increases from the different install techniques?

The Nvidia website suggests a method which should work on any distro. However each distro has its way to install the driver.

The extraction is not necessary but it more flexible since it's easier to patch the Nvidia installer if for example you're using a version of the kernel or of the Xserver the Nvidia installer does not support natively.

In other words, no, there is not performance increase.

---

### Post by echo $USER on 2006-07-20
Nice, thanks for all the help and information.  It's people like yourself and this forum that make this distribution so attractive.

> ~$ uname -r
2.6.17


> ~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

Thanks again!

---

