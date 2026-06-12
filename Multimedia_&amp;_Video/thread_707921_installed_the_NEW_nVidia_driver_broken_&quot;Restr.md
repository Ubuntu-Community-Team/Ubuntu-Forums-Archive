---
title: "installed the NEW nVidia driver broken &quot;Restricted Drivers Manager&quot; and 3D (Gutsy)"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by xiao_wen on 2008-02-25
I installed Ubuntu(7.10) on my Toshiba Pro 6100 laptop, first all I updated my video card driver to the latest version for my video card which is GeForce4 420 Go. 

```

toshiba@laptop:~$ lspci -nnv -s 01:00.0

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go] [10de:0175] (rev a3) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device [1179:0001]
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 10
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at dc000000 (32-bit, prefetchable) [size=64M]
        Memory at dbf80000 (32-bit, prefetchable) [size=512K]
        [virtual] Expansion ROM at dbf00000 [disabled] [size=128K]
        Capabilities: <access denied>



```

I did some google search and fixed some EDID problem and let the new driver run.

```

toshiba@laptop:~$ lsmod | grep nvidia
nvidia               4718704  22 
i2c_core               26112  1 nvidia
agpgart                35016  2 nvidia,intel_agp


```

And I run the glxinfo

```

toshiba@laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation server glx version string: 1.4 server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap
client glx vendor string: NVIDIA Corporation client glx version string: 1.4 client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap GLX version: 1.3 GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_get_proc_address OpenGL vendor string: NVIDIA Corporation OpenGL renderer string: GeForce4 420 Go/AGP/SSE2 OpenGL version string: 1.5.8 NVIDIA 96.43.05 OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
 ……



```


**direct rendering: Yes**
 Is that meaning my 3D accelerated driver running on my machine?



From nvidia point of view, YES. 
But from Ubuntu point of view maybe NOT.


When I open “Restricted Drivers manager”, the nvidia driver’s status is “in use” and “enabled” unticked. I could NOT enable it, because said nvidia-glx not enabled. That’s right , because it’s recommended to remove when I install the new version of driver. 
My question here:

Is this one bug in “Restricted Drivers Manager”? How is RDM working to turn “ENABLED” on?

If this not fixed, I couldn’t turn on 3d desk effects in my Ubuntu, maybe other 3D application?

I know when I run “sh NVIDIA*.run” to install new driver, the system would install Nvidia kernel and nvidia provided OpenGL library. Is Ubuntu provide it’s own OpenGl libray for video card driver install? Is it possible to create link point to NVIDIA version openGL lib? How where are they?

When I install new nvidia driver, it’s compiled/build for my Ubnutu. Is it possible copy them to the ubuntu version in somewhere rather than install?

Thanks for help,

---

### Post by pdub on 2008-02-25
After you install the nvidia binary driver, make sure that this file:

/etc/default/linux-restricted-modules-common

Contains

DISABLED_MODULES="nv nvidia_new"

You may also need to remove the file /lib/linux-restricted-modules/.nvidia_new_installed

```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```


Then reboot.

More info is available here:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by xiao_wen on 2008-02-26
thanks for your apply, but I followed the instruction and got driver installation successful.
I have no problem with new driver install.

The question is how could make "Restricted drivers Manager" detect my new accelerated driver installed? any source code i could change, sounds like just check "nvidia-glx" install or not. But after manually install the latest driver from nvidia, it's no nividia-glx in the machine.

thanks for your help,

---

### Post by pdub on 2008-02-26
I search around a bit and noticed that people with that card have had problems.

As a point of reference, here are some items from my configuration. I have a GeForce Go 7400.

I noticed the size of your driver is very small. Here is the output from lsmod on my computer using the latest binary drivers from nvidia.

```
nvidia               7822336  36 
i2c_core               26112  1 nvidia
agpgart                35016  2 nvidia,intel_agp

```

When I look in the restricted drivers manager, Nvidia Accelerated Graphic Driver have a green check mark but the enable box is NOT checked. It has been that way since I installed the binary driver. Compiz works fine, GLX works fine.

What happens when you do the following?

```
sudo lsmod | grep nvidia
```

Note the size of the driver.

```
sudo rmmod nvidia

sudo modprobe nvidia

sudo lsmod | grep nvidia
```

Does the driver size change?

---

### Post by xiao_wen on 2008-02-27
GOOD POINT!!!!!!!!!!

my video card has 32MB ram, so it's no enough to run compiz. I did reload mod again, but got the same out put.
```
toshiba@laptop:~$ lsmod | grep nvidia
nvidia               4718704  22 
i2c_core               26112  1 nvidia
agpgart                35016  2 nvidia,intel_agp

```

QUESTION:
How could I get 4718704 not 32MB for nvidia? Could I assign more ram to video card?

So I tried this
```
toshiba@laptop:~$ compiz --help
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0175 (rev a3) (prog-if 00 [VGA]) Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory .......................

```

that's mean I need more ram for video card.

**alternative fixed** would be put

```
SKIP_CHECKS=yes
```

in your ~/.config/compiz/compiz-manager file.

NOW I can run compiz by ```
compiz --replace ccp &
```

ALL good for my compiz.
But i still want to know how to assign more physic memory to video ram.

NEXT question:
I couldn't turn on other 3D effect from System->Preference->Apprearance, because in the "Restricted Drivers manger" the nvidia card si still not enabled , just "in use".

I think this is bug in "RDM", because only check package "nvidia-glx" running or not. Who can tell me where I can find this code and fixed it. because manually installed driver did not install this "nvidia-glx".
we can check something else.


thanks for your help,

---

### Post by pdub on 2008-02-27
The driver will not show enabled when you are using the binary driver from the nvidia site. That is not a problem.

As far as the driver size goes, it likely has nothing to do with the amount of video ram as I get the same size driver on all of my computers that have various amount of video ram.

From everything that you posted, it appears as though glx is running. You should only need 

```
        Load            "glx"
```

In your xorg.conf file.

---

### Post by xiao_wen on 2008-02-28
Load glx

it's already in my xorg.conf.

is it possible some shared memory to video card to fix this problem rather than "SKIP_CHECKS=yes"?

do you know what's "videoRam" for in xorg.conf?


thanks, at lease compiz could run on my box.

---

### Post by pdub on 2008-02-28
The only time I have seen VideoRam used in an xorg config is when the driver does not see the proper amount of video ram. I supose it can't hurt.

With only 32MB of video ram I am not sure what you should expect in terms of performance.

---

### Post by xiao_wen on 2008-02-28
I tried CUBE effect, it's good , just getting hot quickly and crashed because it's too hot, I will try it in winter. :-)

thanks,

BTW, not possible assign shared memory to video RAM?

---

