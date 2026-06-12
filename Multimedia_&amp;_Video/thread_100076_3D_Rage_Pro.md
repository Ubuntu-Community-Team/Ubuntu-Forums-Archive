---
title: "3D Rage Pro"
date: 2005-12-06
forum: Multimedia &amp; Video
---

### Post by shaggydoo on 2005-12-06
I just got another old computer and decided to install Ubuntu on it. It's running well with one exception: it doesn't seen to use hardware opengl. It's using a 3D Rage Pro card and also has some onboard card (don't know what it is, haven't checked it out).

The onboard seems to be used during bootup and if the xserver isn't running. When the xserver is up, the rage card is used.

How do I get 3D acceleration to work on the 3D Rage Pro card? I looked everywhere but couldn't figure it out. I read that it might not be supported unless I install Utah-GLX or [DRI](http://dri.freedesktop.org), which I couldn't figure out how to install either.

---

### Post by Teroedni on 2005-12-07
How do you know its not?

Open a program named terminal
You find it in the Ubuntu menu
Yust search tru it;)

write
```
glxinfo
```

and press return

what does it report?

---

### Post by shaggydoo on 2005-12-07
I know it's not because I already checked with "glxinfo | grep direct" :)
glxinfo tells me it's using mesa indirect, direct rendering: no.

Besides, I screwed it up completely after playing around with X, now even uninstalling xorg and reinstalling it doesn't help. I've got to wipe it and install Ubuntu again.

---

### Post by peter_m on 2005-12-07
[QUOTE=Teroedni]
write
```
glxinfo
```

and press return

what does it report?[/QUOTE]

I just did that and I get:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
```

I think I have about the same VGA, ATI Rage Pro Turbo PCI. I dont remember where but I saw it being refered to 3D Rage Pro and also ATI Mach64 and it has no hardware accellaration. Can I tweek it in any way? I am running on an older iMAC (PPC) if that helps. Would really like to get some kind of 2D/3D hardware accellaration.

Edit: Are these instructions going to help me speed things up?  [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)

---

### Post by ranf on 2005-12-07
[QUOTE=peter_m]
I think I have about the same VGA, ATI Rage Pro Turbo PCI. 
[/QUOTE]
Find out what it is:
```

lspci | grep -i vga

```
[QUOTE=peter_m]
Edit: Are these instructions going to help me speed things up?  [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)[/QUOTE]
These instructions tell you how to rebuild the X server. A bit oversized.

---

### Post by shaggydoo on 2005-12-07
Not sure about that guy, but I just reinstalled Ubuntu on the PC. I decided to see what the onboard card was, and what a coincidence, I've got another PC here with the same chipset (although I never tried to get 3d accel on that one). I looked around and didn't manage to get either the 3D Rage Pro or the onboard SiS 630 to get direct rendering/3d accel.


```
root@ubuntu:~# glxinfo | grep direct
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```



```
root@ubuntu:~# lspci | grep -i vga
0000:00:09.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)
```



```
root@ubuntu:~# X -version
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
```

---

### Post by ranf on 2005-12-07
[QUOTE=shaggydoo]
```
root@ubuntu:~# lspci | grep -i vga
0000:00:09.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)

```
[/QUOTE]
Looks like the mach64 stuff would work:
[http://dri.freedesktop.org/wiki/ATIMach64](http://dri.freedesktop.org/wiki/ATIMach64)

I've used the savage Howto in the "Customization Tips & Tricks" section.

---

### Post by peter_m on 2005-12-07
[QUOTE=ranf]Find out what it is:
```

lspci | grep -i vga

```
[/QUOTE]

and my result is:```

0000:00:12.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (rev 5c)
```

What does that tell me? Can I improve this turtle box?

[QUOTE=ranf]Looks like the mach64 stuff would work:
[http://dri.freedesktop.org/wiki/ATIMach64](http://dri.freedesktop.org/wiki/ATIMach64)
[/QUOTE]

I've loolked at that link before, it says: 
> How do I build the mach64 branch?

Follow the instructions on the Building page. Mach64 is now on the DRI trunk. 
 and it link to [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)  That's the link you called "A bit oversized" What does that mean? Anything else I could try?

---

### Post by ranf on 2005-12-07
[QUOTE=peter_m]
I've loolked at that link before, it says: 

 and it link to [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building)  That's the link you called "A bit oversized" What does that mean? Anything else I could try?[/QUOTE]
You can download 2 files from their snapshots directory, look up that savage HowTo I referred to and compile 2 kernel modules. And hopefully it will work.

---

### Post by shaggydoo on 2005-12-08
Well, I tried that a few times, here are the errors I get after compiling (snipped to the last few lines):

```
...(tons of warnings and errors about XF86VMode.c)...<snip>
XF86VMode.c:1164: error: 'red' undeclared (first use in this function)
XF86VMode.c:1165: error: 'green' undeclared (first use in this function)
XF86VMode.c:1166: error: 'blue' undeclared (first use in this function)
XF86VMode.c:1171: error: 'True' undeclared (first use in this function)
XF86VMode.c: At top level:
XF86VMode.c:1174: error: syntax error before 'XF86VidModeGetGammaRampSize'
XF86VMode.c:1175: error: syntax error before '*' token
XF86VMode.c:1179: warning: return type defaults to 'int'
XF86VMode.c:1179: warning: function declaration isn't a prototype
XF86VMode.c: In function 'XF86VidModeGetGammaRampSize':
XF86VMode.c:1184: error: 'size' undeclared (first use in this function)
XF86VMode.c:1193: error: 'xReply' undeclared (first use in this function)
XF86VMode.c:1193: error: syntax error before ')' token
XF86VMode.c:1193: error: 'xTrue' undeclared (first use in this function)
XF86VMode.c:1201: error: 'True' undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:84: Error: symbol `y' is already defined
{standard input}:102: Error: symbol `protocolBug' is already defined
{standard input}:108: Error: symbol `oldreq' is already defined
{standard input}:114: Error: symbol `oldreq' is already defined
{standard input}:120: Error: symbol `oldreq' is already defined
{standard input}:126: Error: symbol `oldreq' is already defined
{standard input}:150: Error: symbol `protocolBug' is already defined
{standard input}:162: Error: symbol `dotclock' is already defined
make[4]: *** [XF86VMode.o] Error 1
make[4]: Leaving directory `/root/xc/lib/Xxf86vm'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/root/xc/lib'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/xc'
make[1]: *** [World] Error 2
make[1]: Leaving directory `/root/xc'
make: *** [World] Error 2

```

So there seems to be a lot of fuss about **lib/Xxf86vm/XF86VMode.c**. Any ideas? Just for reference, here's my host.def for it:

```
#define XFree86CustomVersion "Minimal DRI build from X.org tree"

/* Compiler options */
#define DefaultGcc2i386Opt -O2 -gstabs+ -pipe

/* DDX drivers to build: trim this list to your needs */
/*define XF86CardDrivers tdfx i810 mga ati glint vga sis savage via*/
#define XF86CardDrivers ati sis
#define DRMSrcDir /root/drm/

/* DRI drivers are built from Mesa CVS */
#define DriDrivers /**/
#define DevelDRIDrivers /**/

/* Build development (insecure) DRI-aware 2D drivers */
#define BuildDevelDRIDrivers YES

/* Only shared libGL */
#define NormalLibGlx NO

/* Link the drivers against static libexpat to make binary snapshots
 * more usable and to reduce build problems on Linux machines without
 * expat.
 */
#if defined(LinuxArchitecture) && !defined(AMD64Architecture)
# define ExpatLibrary		StaticLibrary($(BUILDLIBDIR),expat)
# define NormalLibExpat 	YES
#endif

/* Optionally turn these on for debugging */
/* #define GlxBuiltInTdfx YES */
/* #define GlxBuiltInI810 YES */
/* #define GlxBuiltInMga YES */
/* #define GlxBuiltInR128 YES */
/* #define GlxBuiltInRadeon YES */
#define DoLoadableServer YES

/* Optionally turn this on to change the place where you install the build.
 * Warning: trailing blanks will cause build failures.
 */
/* #define ProjectRoot /usr/X11R6-XORG */

/* Don't install anything outside the ProjectRoot directory */
#define NothingOutsideProjectRoot YES

/* #define UsrLibDir /usr/X11R6/lib */

/* Optionally build the Xnest, Xvfb and Xdmx servers */
#define XnestServer NO
#define XVirtualFramebufferServer NO
#define BuildDmx NO

/*
 * Build as little as possible (usually no need to change anthing here)
 */
#define BuildServersOnly YES
#define BuildLibraries NO
#define BuildLibrariesForXServers NO
#define BuildLibrariesForConfigTools NO
#define BuildXIE NO
#define BuildPexExt NO
#define XF86AFB NO
#define XprtServer NO
#define BuildXprint NO
/* HasFontconfig avoids installing a new libfontconfig with its own
 * configuration files. This way you keep your font configuration without
 * copying configuration files around after make install. */
#define HasFontconfig YES

/*
 * Don't change anything below or the build will fail.
 */
#define BuildXF86DRI YES
#define BuildXDriInfo YES
#define BuildGLXLibrary YES
#define BuildXdmcpLib YES
#define BuildXInputLib YES
#define BuildXvLibrary YES
#define BuildXF86VidModeLibrary YES
#define BuildXvMCLibrary YES
#define BuildExpatLibrary YES
#define SharedLibFont NO
#if DoLoadableServer
#undef XF1Bpp
#undef XF4Bpp
#define XF1Bpp NO
#define XF4Bpp NO
#endif

```

---

### Post by jecos on 2005-12-08
When I have time i'll see how good that driver is on my 3D Rage Pro AGP 2X.

---

### Post by Killgore on 2005-12-08
Ive been looking around on a lot of other forums and websites and it seems that there have been a lot of issues with this particular video card. Would i be right in saying that? Im only wondering because im considering purchasing one for my old rig and it would be helpful to know if it will be problematic.

---

### Post by jecos on 2005-12-08
[QUOTE=Killgore]Ive been looking around on a lot of other forums and websites and it seems that there have been a lot of issues with this particular video card. Would i be right in saying that? Im only wondering because im considering purchasing one for my old rig and it would be helpful to know if it will be problematic.[/QUOTE]

Stay away from anything NOT named Radeon or Geforce.. as anything else is bound to be to old/slow or unsupported..

---

### Post by shaggydoo on 2005-12-08
Why buy a 3D Rage Pro? It'd cost you about $10 to get a 64mb Geforce card.

---

### Post by shaggydoo on 2005-12-08
**Edit: Nevermind! Got it working!**

Okay, I googled like a furious madman, redownloaded and recompiled, changed configs, but I STILL couldn't figure this out. The only thing that's left is to compile the Mesa drivers. Here's what happens when I try:

```
s@ubuntu:~/Mesa$ make linux-dri-x86
(cd configs && rm -f current && ln -s linux-dri-x86 current)
make default
make[1]: Entering directory `/home/s/Mesa'
make[2]: Entering directory `/home/s/Mesa/src'
Making sources for linux-dri-x86
make[3]: Entering directory `/home/s/Mesa/src/glx/x11'
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi -I../../../src/mesa/drivers/dri/common `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM -std=c99 -ffast-math  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER clientattrib.c -o clientattrib.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi -I../../../src/mesa/drivers/dri/common `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM -std=c99 -ffast-math  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER compsize.c -o compsize.o
compsize.c:44: warning: no previous prototype for &#8216;__glElementsPerGroup&#8217;
compsize.c:109: warning: no previous prototype for &#8216;__glBytesPerElement&#8217;
compsize.c:151: warning: no previous prototype for &#8216;__glImageSize&#8217;
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi -I../../../src/mesa/drivers/dri/common `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM -std=c99 -ffast-math  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER eval.c -o eval.o
gcc -c -I. -I../../../include -I../../../include/GL/internal -I../../../src/mesa/main -I../../../src/mesa/glapi -I../../../src/mesa/drivers/dri/common `pkg-config --cflags libdrm` -I/usr/X11R6/include -Wall -Wmissing-prototypes -g  -m32 -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM -std=c99 -ffast-math  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DHAVE_ALIAS -DXF86VIDMODE -D_REENTRANT -UIN_DRI_DRIVER glxcmds.c -o glxcmds.o
glxcmds.c:51:38: error: X11/extensions/xf86vmode.h: No such file or directory
glxcmds.c:1726: warning: no previous prototype for &#8216;glXSwapIntervalMESA&#8217;
glxcmds.c:1758: warning: no previous prototype for &#8216;glXGetSwapIntervalMESA&#8217;
glxcmds.c:1788: warning: no previous prototype for &#8216;glXBeginFrameTrackingMESA&#8217;
glxcmds.c:1808: warning: no previous prototype for &#8216;glXEndFrameTrackingMESA&#8217;
glxcmds.c:1829: warning: no previous prototype for &#8216;glXGetFrameUsageMESA&#8217;
glxcmds.c:1857: warning: no previous prototype for &#8216;glXQueryFrameTrackingMESA&#8217;
glxcmds.c: In function &#8216;glXGetMscRateOML&#8217;:
glxcmds.c:2274: error: &#8216;XF86VidModeModeLine&#8217; undeclared (first use in this function)
glxcmds.c:2274: error: (Each undeclared identifier is reported only once
glxcmds.c:2274: error: for each function it appears in.)
glxcmds.c:2274: error: syntax error before &#8216;mode_line&#8217;
glxcmds.c:2282: warning: implicit declaration of function &#8216;XF86VidModeQueryVersion&#8217;
glxcmds.c:2283: warning: implicit declaration of function &#8216;XF86VidModeGetModeLine&#8217;
glxcmds.c:2284: error: &#8216;mode_line&#8217; undeclared (first use in this function)
make[3]: *** [glxcmds.o] Error 1
make[3]: Leaving directory `/home/s/Mesa/src/glx/x11'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/s/Mesa/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/s/Mesa'
make: *** [linux-dri-x86] Error 2

```

Ahhhh! Any more of this and I'll have to kill myself.

---

### Post by zhooibaal on 2005-12-27
I have a Rage Pro agp 2x card too and it doesn't work too well either and reading all this confuses me quite a lot. Maybe I'm too new to linux to understand all this, but I really want to get it working properly. As I understand is that the card will never deliver anything fast (it's not an old and slow card for nothing) but at least I'd like to get rid of the extremely slow desktop graphics in gnome.

As for my current linux knowledge: I'm in the stage of starting to understand how to work with gnome and browsing through directories using the terminal goes quite well too.
So if someone is willing to help me, I'd be very gratefull as it will probably also help me understand a bit more of linux. And please don't blame me for being a n00b (as in being completely new to all this), believe me, I already know.

Maybe this info might help you help me:
Mobo: DFI P61 rev2
Proc: P3 533
Mem: 256MB PC133 SDRAM
Video: ATI Rage Pro AGP 2x
Sound: SB 128 PCI
HDD: 1x 10GB + 1x 40GB
Optical: 2x cdrom (40x and 52x)
no floppy drive (floppy controller is fubar, I know this, because in Windows it generates nothing but errors and it does so in Ubuntu too)
Network: sitecom 10/100Mbit + Conceptronic 54Mbit wifi (RaLink)

regards.

---

### Post by pek on 2005-12-27
i have one of those cards (an all in wonder pro) and a s3 pci card, wich do you think is better to give a try?

---

### Post by az on 2005-12-27
[QUOTE=shaggydoo]
How do I get 3D acceleration to work on the 3D Rage Pro card? I looked everywhere but couldn't figure it out. I read that it might not be supported unless I install Utah-GLX or [DRI](http://dri.freedesktop.org), which I couldn't figure out how to install either.[/QUOTE]


In breezy, it should work out of the box if the card has enough memory.

You can reconfigure the xserver to use a lower color depth and screen resolution to get it working.  On a 8MB such card, I need to set the screen to 16-bit, 800x600 for dri to work.

---

