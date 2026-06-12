---
title: "I DID IT! fglrx 3D acceleration with ATI driver on feisty"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by mightyteegar on 2007-05-02
After searching all over these forums and scouring the rest of the Internet, I finally got my Radeon X300 card working with ATI's fglrx driver and I now have 3D acceleration.  Back story:

- I upgraded from edgy to feisty about a week after feisty came out.  I noticed some days later that my 3D acceleration was gone.  
- I had xorg-driver-fglrx installed from the Ubuntu repositories.  
- I tried every how-to I could find to get 3D working.  Nothing worked -- fglrxinfo always came back saying it was using the Mesa driver.
- /var/log/Xorg.0.log kept saying something along the lines of "GART could not initialize, DRI disabled" and I found no help on the Internet about this problem.

What I did:

+ Uninstalled the fglrx driver (ver. 8.34.x) from the Ubuntu repositories.
+ Uninstalled linux-restricted-modules-common.  
+ (Basically I uninstalled every possible package that might have had anything to do with the fglrx driver.  At this point I don't recall what all of them were.)
+ Installed the most recent fglrx driver (ver. 8.36.5) using Method 2 from the [Ubuntu Feisty Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide").  
 
After following all the instructions I still didn't have 3D acceleration, but I noticed in /var/log/Xorg.0.log a line that said:

"Kernel module version does *not* match driver." 

I also noticed that the Restricted Drivers Manager was now showing my newly installed driver.  So I realized that an older stray kernel module was still being called from somewhere, instead of the up-to-date module.  

The restricted drivers, I discovered, live in the **/lib/modules/(your kernel version)/misc** directory.  I guessed that my newly-created kernel module was the same as the fglrx.ko module I saw in the misc/ directory.  

+ Next I ran:
```
sudo rmmod fglrx
```
+ I then navigated to **/lib/modules/(your kernel version)/misc** and ran:
```
sudo insmod fglrx.ko
```

I then ran: 

```
modprobe fglrx
``` and restarted X... and it worked!  I now have 3D acceleration in Feisty.  

```
$modinfo fglrx
filename:       /lib/modules/2.6.20-15-generic/misc/fglrx.ko
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
depends:        agpgart
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           firegl:charp

```

**Please note** that I went through a lot of trial and error with this.  The steps I have outlined here are obviously hazy and without great detail, but the summary of what worked for me is this:

1. Purge out any trace of your fglrx drivers.
2. Install the latest ATI driver using Method 2 in the [Ubuntu Feisty Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide").  **Make sure to follow all the steps carefully!**
3. rmmod fglrx
4. insmod /lib/modules/(your kernel version)/misc/fglrx.ko
5. modprobe fglrx

If this works for anyone else, please let us know.  Hopefully my efforts can help someone else.  

**Disclaimer:** I am not a programmer, Linux expert or anything else other than a (formerly frustrated) user with a lot of determination.  If you try this, you do it at your own risk.

---

### Post by yogurtcz on 2007-05-08
Yep, I got exactly the same output of  &#8220;modprobe  fglrx&#8221; on mine 9800SE.
However, glxinfo shows:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x29 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x2a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2d  8 pc  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  0 0 None
0x2e  8 gs  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  0 0 None

```

(note **direct rendering NO**)

and fglrxinfo

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

is still stuck to mesa... :confused: 

Any ideas?

---

### Post by lebe0024 on 2007-05-08
Who ever said "linux is not user friendly" should be burned at the stake! LOL

---

### Post by Crankshaft on 2007-05-10
I followed your instructions and my resolution changed but I have no xorg and it says restricted drivers are in use.  I'm pretty new to linux so if you want any other info let me know.

thanks

---

### Post by penguins! on 2007-06-01
Hey, this worked great for me.

The only problem is that the old module is reloaded every time I reboot.

Any idea how to make the changes stick?

---

### Post by Franz1234 on 2007-06-02
> 4. insmod /lib/modules/(your kernel version)/misc/fglrx.ko

I needed to run insmod /lib/modules/2.6.20-16-generic/volatile/fglrx.ko.


Now i get the same output.

> filename:       /lib/modules/2.6.20-16-generic/volatile/fglrx.ko
depends:        agpgart
vermagic:       2.6.20-16-generic SMP mod_unload 586 
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany
parm:           firegl:charp 

But still get "mesa"

> franz@Lappi:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


---

