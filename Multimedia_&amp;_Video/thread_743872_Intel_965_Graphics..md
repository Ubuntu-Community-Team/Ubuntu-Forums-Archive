---
title: "Intel 965 Graphics."
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by jonathangillings on 2008-04-03
Hi Ubuntu specialist dudes. 

I am running 7.10. I have a new Lenovo R61i with an Intel 965 graphics chipset (X3100). My friend as a 945 chipset on his HP notebook. Compiz aside (I can live without it - it runs perfectly on the 954), his graphics work properly and mine do not. I cannot increase my resolution and video playback is not ideal (I notice a difference between video's played on VLC in windows and on my Ubuntu install). My machine is using the experimental modesetting driver for Intel onboard graphics. 

The thing is that my 965 chipset is quite substantially superior to the 945. In windows I have just loaded a newish driver (Driver Revision: PV 14.33) which has got my hardware T&L working and all round given me pretty impressive performance (for a jutsy Intel notebook graphics chipset).

My question is when will my graphics work, or is there something I can do to sort it out. As far as I can see Intel have released the Linux driver for my chipset but I assume it has not been built in or something along these lines. I read somewhere that I would have to wait for version 8.10. Is this true? could I upgrade my kernel? is this safe and is it complicated?

Thanks a lot.
Jonathan.

---

### Post by Thelasko on 2008-04-07
7.10 has the latest and greatest Intel driver.  You probably have to reconfigure your X to use a higher resolution.  There is a chance that if you don't configure X correctly it will crash X and you will be stuck in the command prompt.  The easiest way to configure X is to use the command
```
sudo dpkg-reconfigure xserver-xorg
```
It guides you through and if you screw up just try it again. 

Hint: write it down!

---

### Post by jonathangillings on 2008-04-17
I am still having issues with my graphics. Whenever I attempt to run any application with 3D effects X crashes and restarts. 
I have included a section of my Xorg.0.log file - the section at which X crashes. Perhaps you can pick up what is going wrong from this. Any assistance with this would be greatly appreciated.



(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0077f000 (pgoffset 1919)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02148000 (pgoffset 8520)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x02158000 (pgoffset 8536)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x02798000 (pgoffset 10136)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x02dd8000 (pgoffset 11736)
(WW) intel(0): ESR is 0x00000001
(WW) intel(0): Existing errors found in hardware state.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0): [drm] dma control initialized, using IRQ 19
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: LEN  Model: 4050  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1408 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
(II) intel(0):  154WX4-TLA6
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae504000000000
(II) intel(0): 	0011010380211578eab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	36004bcf100000192617008050201030
(II) intel(0): 	182036004bcf100000190000000f0081
(II) intel(0): 	0a32810a28140100320c010b000000fe
(II) intel(0): 	003135345758342d544c41360a2000ca
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync
(II) intel(0): Modeline "1280x800"   59.26  1280 1304 1336 1408  800 803 809 816 -hsync -vsync
(II) intel(0): EDID vendor "LEN", prod id 16464
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x800"x51.6   59.26  1280 1304 1336 1408  800 803 809 816 -hsync -vsync (42.1 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Manufacturer: LEN  Model: 4050  Serial#: 0
(II) intel(0): Year: 2007  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) intel(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 59.3 MHz   Image Size:  331 x 207 mm
(II) intel(0): h_active: 1280  h_sync: 1304  h_sync_end 1336 h_blank_end 1408 h_border: 0
(II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
(II) intel(0):  154WX4-TLA6
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0030ae504000000000
(II) intel(0): 	0011010380211578eab3409959538d27
(II) intel(0): 	25505400000001010101010101010101
(II) intel(0): 	010101010101bc1b00a0502017303020
(II) intel(0): 	36004bcf100000192617008050201030
(II) intel(0): 	182036004bcf100000190000000f0081
(II) intel(0): 	0a32810a28140100320c010b000000fe
(II) intel(0): 	003135345758342d544c41360a2000ca
(II) intel(0): Printing DDC gathered Modelines:

---

### Post by Thelasko on 2008-04-17
Please post the contents of /etc/X11/xorg.conf.
Also try opening the terminal and typing:
```
glxgears -printfps
```
and
```
glxinfo
```

Pleae post the output of the two programs.  Let me know if X crashes with glxgears (it might if there is a problem).

3D in Ubuntu is handled by a program called OpenGL.  These two programs are useful in troubleshooting OpenGL problems.

---

### Post by jonathangillings on 2008-04-18
Hi Thelasko,
glxgears crashed X as you suspected it would and thus I did not get any screen output to post. I have attached my xorg.conf file and as follows was the screen output for glxinfo 
Thanks for your help.

name of display: :2.0
display: :2  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
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

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by Aryding on 2008-04-18
I think we have the same problem.  I have the G35, registered as the 965 and no video playback... except youtube :(

---

### Post by Tomatz on 2008-04-18
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then select:

**intel**

**Then the resolutions your screen supports**

Should work fine now as xorg has probably defaulted to the vesa driver;)

---

### Post by jonathangillings on 2008-04-18
OK I tried the sudo dpkg-reconfigure -phigh xserver-xorg and I am still having the same issue. It is definitely using the Intel driver as can be seen in this section of my xorg.conf


-------------------------------------------
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection


-------------------------------------------------------------

glxgears and all other 3d / opengl type apps still crash X.

---

### Post by Tomatz on 2008-04-18
> **jonathangillings said:**
> OK I tried the sudo dpkg-reconfigure -phigh xserver-xorg and I am still having the same issue. It is definitely using the Intel driver as can be seen in this section of my xorg.conf


-------------------------------------------
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection


-------------------------------------------------------------

glxgears and all other 3d / opengl type apps still crash X.


Are you using xserver-xgl as that can slow things down? Have a look in system monitor to see if its running.

---

### Post by jonathangillings on 2008-04-18
Xgl is running, as well as Xgl-lockfile-wr.

---

### Post by Tomatz on 2008-04-18
In a terminal:

```
sudo apt-get remove xserver-xgl
```

Reboot

Now things should run smoothly ;)

---

### Post by jonathangillings on 2008-04-18
Dude - Problem solved. So it was xgl causing my headaches all along. 

Is xgl a part of compiz? Will I be able to run compiz without it? 

I am not at all unhappy without Compiz, just very chuffed that my machine is FINALLY behaving. I have tested video playback, Scorched3D, openarena - all running perfectly.

Thanks to you all for all of your help.

Chuffed.

---

### Post by Tomatz on 2008-04-18
> **jonathangillings said:**
> Dude - Problem solved. So it was xgl causing my headaches all along. 

Is xgl a part of compiz? Will I be able to run compiz without it? 

I am not at all unhappy without Compiz, just very chuffed that my machine is FINALLY behaving. I have tested video playback, Scorched3D, openarena - all running perfectly.

Thanks to you all for all of your help.

Chuffed.

You don't necessarily need xgl to run compiz with the intel driver. I find xgl more trouble than its worth.

Try this in a terminal:

```
compiz --replace
```

And see how it goes ;)

If it compiz works smoothly add the command to *system, preferences, sessions, startup*

---

### Post by Thelasko on 2008-04-18
I'm confused.  Did you install xgl?  Should everyone with an Intel driver make this change or is this unique to your machine?

---

### Post by Dynaflow on 2008-04-20
Here's the scoop on that particular graphics card:

Intel, or whoever was subcontracted to put it together, did such a bizarrely shoddy job on the Linux driver for the 965 that the thing can't efficiently do 3D acceleration and video playback simultaneously.  By "efficiently," I mean do it without being either "balls-achingly slow," in the words of another poster, or just flat-out crashing.  

Because of this, the Compiz team has [blacklisted]("http://wiki.compiz-fusion.org/Hardware/Blacklist") that piece of hardware so that their software doesn't interfere with any of the core graphical functions most users probably expect their computers to be able to do, like playing back video.  (See the second post down, [here]("http://www.realistanew.com/2008/01/").)

You can "opt-out" of the blacklisting by following [these instructions]("http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php") if the video-playback conflict doesn't bother you.  

My work laptop has an Intel 965 card in it, and since it almost never has to do video playback, I de-blacklisted it to enable the Compiz desktop cube I find so useful for multitasking.  I haven't had a real problem with the arrangement yet.

---

### Post by jonathangillings on 2008-04-21
Hi Thelasko,
I did not manually install xgl insofar as recollection serves. I did a standard install from the live disk. I then installed Compiz (which did not work) and finally I did a full system update which pulled down just shy of 300mb of updates. After the update Compiz worked, but no other 3d acceleration did and even when I disabled Compiz my video playback was sketchy (which as it turned out was xgl).

At the moment everything that Dynaflow stated reigns true. If i bypass blacklisting and start Compiz with the following command
SKIP_CHECKS=yes compiz
then compiz works perfectly but video does not play at all (not even balls achingly slow - just crashes mplayer or VLC)
 
Obviously first prize would be to have both video and Compiz working together - but I can live with disabling Compiz when I want to watch a movie.

I wonder if there is any solution on the cards from Intels perspective regarding this dodgey open source driver?

J.

---

### Post by Thelasko on 2008-04-21
When I used feisty I changed my video output mode to xv or something like that.  It wasn't the best for full screen but it worked.

---

### Post by Tomatz on 2008-04-21
> **jonathangillings said:**
> Hi Thelasko,
I did not manually install xgl insofar as recollection serves. I did a standard install from the live disk. I then installed Compiz (which did not work) and finally I did a full system update which pulled down just shy of 300mb of updates. After the update Compiz worked, but no other 3d acceleration did and even when I disabled Compiz my video playback was sketchy (which as it turned out was xgl).

At the moment everything that Dynaflow stated reigns true. If i bypass blacklisting and start Compiz with the following command
SKIP_CHECKS=yes compiz
then compiz works perfectly but video does not play at all (not even balls achingly slow - just crashes mplayer or VLC)
 
Obviously first prize would be to have both video and Compiz working together - but I can live with disabling Compiz when I want to watch a movie.

I wonder if there is any solution on the cards from Intels perspective regarding this dodgey open source driver?

J.

To get compiz + video output working:


Open **vlc**   [I](**sudo apt-get install vlc** if you don't already have it installed)
[/I]
open **preferences**

check **advanced preferences** (bottom rh)

then drop down **video**

select o**utput modules**

and change to **X11**


Video output will work now.  Albeit a bit lower quality but not too noticeable ;)

---

### Post by jonathangillings on 2008-04-23
Hey, it works.
You the man Tomtaz.

---

### Post by Tomatz on 2008-04-23
> **jonathangillings said:**
> Hey, it works.
You the man Tomtaz.

Cool ;)

Glad i could help.

---

