---
title: "How I got ATI drivers to work"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by disturbed1 on 2006-06-08
There are so many threads about the ATI drivers not working. I haven't had an issue with the drivers, so I decided to layout what I did, and maybe someone will be able to gather some information from this.

My hardware details.
Motherboard - Nvidia NForce 3
Graphics Card - ATI x1600 Pro AGP 8x

I did this install 4 times, with out at a problem on any of them.

First off, this was a fresh install of Dapper using the Live CD. When the Live CD loads, choose safe graphics mode vesa. This will cause Xorg to use the Vesa driver instead of ATI or Raedon. I could not correctly install the fglrx drivers if I did not choose safe graphics mode, nor if I used the *alternate* install CD. Xorg would notice I have an ATI card, and attempt to use the ATI driver. Then problems would be abound, Xorg won't load using "ati" with my x1600, attempting to install the fglrx driver after Xorg has identified my card as an ATI caused numerous hard locks and instability problems.

Once the live session loads, procede to install as normal. Once my pc restarted, I entered recovery mode, (BTW, what is up without needing a password here?) I checked my xorg.conf to make sure it still had "vesa" listed as the driver.

```

nano /etc/X11/xorg.conf
``` 
All was fine, so I typed exit to continue with the boot. I went straight to synaptic did a reload to refresh the package list, marked the 11 updates, and marked my kernel and restricted modules for my kernel (K7 kernel for me), that was it, nothing more, no fglrx driver yet ;). Restart PC. Open a terminal and type this

```

sudo apt-get install xorg-driver-fglrx fglrx-control libqt3-mt
``` 
then I enabled the ati driver
```

sudo  aticonfig --initial --overlay-type=Xv

``` 
Kill the X session with ctrl-alt-backspace. Give it a couple of seconds, GDM will reload, and all is well and fine. Another fglrx install without any problems =D>

```

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

``` 
```

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
``` 
```

$ lsmod | grep -i fglrx
fglrx                 391980  8
agpgart                37072  2 fglrx,amd64_agp

``` 


A final note on the fglrx drivers, if you have an older card (chipset less than R300) Xorg has built in 2d and 3d hardware acceleration using the Radeon driver. So if you have something like a 9200 you would be better off using the Xorg driver, since these cards also support AIGLX.

---

### Post by Ivhassel on 2006-06-08
[QUOTE=disturbed1]
A final note on the fglrx drivers, if you have an older card (chipset less than R300) Xorg has built in 2d and 3d hardware acceleration using the Radeon driver. So if you have something like a 9200 you would be better off using the Xorg driver, since these cards also support AIGLX.[/QUOTE]

[SIZE="4"]**Short note for those that fall under this 'older card' category:**[/SIZE]
You can check what chipset you have with
```

lspci | grep ATI

```

If you indeed have a **chipset less than R300**, try this solution to get your 3D working:

[http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)

---

### Post by Dillius on 2006-06-08
I've got an ATI Radeon X800 GTO and I can't even get the display to function properly booting in safe mode. I hear the sound of the Live CD, but I have no display whatsoever.

---

### Post by Vincent_Lin on 2006-06-08
Thanks for this method.

It works for me - IBM T42 with ATI 9600m, on 686 kernel.

I have tried all other methods (Method1, Method2, etc... ) non worked.
I have tried using older fglrx drivers, non worked.

Based on your procedure, it seems to me that oss ati driver is leaving something that prevent fglrx driver from working.  Funny that back to Flight4 or 5 nothing like this was there and my installation of fglrx onto this machine was so straightforward.

Thanks again.

Vincent

---

### Post by acankat on 2006-06-08
Same hardware
same steps

no fglrx](*,)

---

### Post by Ivhassel on 2006-06-09
[QUOTE=acankat]Same hardware
same steps

no fglrx](*,)[/QUOTE]

Please post the following info:

[LIST]
[*]Output of
```
lspci | grep ATI
```
[*]Output of
```
fglrxinfo
```
[*]Output of
```
glxinfo
```
[*]Your /etc/X11/xorg.conf
[*]What error messages do you get? Possibly this: [fglrx] API ERROR: could not register entrypoint for *$API*
[/LIST]

I might not be able to help, but I can compare it with my working config, or someone else might be able to help, based on your info

---

### Post by Wolf359T on 2006-06-09
```
root@LCARS:/home/claudiu# lspci |grep ati 0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
```

```

root@LCARS:/home/claudiu# fglrxinfo

[...]
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[...]

```

What's wrong?...

---

### Post by Ivhassel on 2006-06-10
[QUOTE=Wolf359T]```
root@LCARS:/home/claudiu# lspci |grep ati 0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
```

```

root@LCARS:/home/claudiu# fglrxinfo

[...]
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB

<cut>

[...]

```

What's wrong?...[/QUOTE]

The **latest** ATI drivers don't work with **R280** chips. Install the previous ATI drivers. Howto is around somewhere.
Good luck :)

---

### Post by evil_elman on 2006-06-10
What about those that have problems with 2D?

Whenever I move a window, scroll text, minimize or otherwise do the usual stuff, the CPU usage is alot higher than in Windows. 3D works fine (tried several 3D games).

The desktop is not in 3D, though... :(

---

### Post by mms on 2006-06-10
Yes!  It worked (ATI RV350 Radeon 9600 M10).  Nice job, disturbed1 and thanks.

---

### Post by acankat on 2006-06-10
[QUOTE=Ivhassel]Please post the following info:

[LIST]
[*]Output of
```
lspci | grep ATI
```
[*]Output of
```
fglrxinfo
```
[*]Output of
```
glxinfo
```
[*]Your /etc/X11/xorg.conf
[*]What error messages do you get? Possibly this: [fglrx] API ERROR: could not register entrypoint for *$API*
[/LIST]

I might not be able to help, but I can compare it with my working config, or someone else might be able to help, based on your info[/QUOTE]

lspci | grep ATI :

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 71c2
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 71e2

fglrxinfo : 

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

glxinfo : 

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None



Heeeelllllllpppp....

---

### Post by deboring21 on 2006-06-10
Ok.. well, I followed the guide up to the part where I reboot and go into the recovery mode. But when I go into the recovery mode, it locks up on me and I get some errors about my PC trying to set up some timers.... not really sure what the timers are. I have an ATI Radeon 9100 PCI graphics card... not sure if having a PCI card will make a difference. I disabled the onboard video on my motherboard also, that got me past a problem with locking up I had before... I can't seem to find a solution... any suggestions out there?
-Ryan

---

### Post by disturbed1 on 2006-06-10
[quote=acankat]...............................................................................................
..............................................................................................................................


Heeeelllllllpppp....[/quote] 

:-k

Is this a fresh install from the live cd using safe graphics mode? Because there is no mesa drivers that have ever been loaded on my systems.

What does this give you?
**lsmod | grep fglrx**
**dmesg | grep fglrx**



[quote=deboring21]
Ok.. well, I followed the guide up to the part where I reboot and go into the recovery mode. But when I go into the recovery mode, it locks up on me and I get some errors about my PC trying to set up some timers.... not really sure what the timers are. I have an ATI Radeon 9100 PCI graphics card... not sure if having a PCI card will make a difference. I disabled the onboard video on my motherboard also, that got me past a problem with locking up I had before... I can't seem to find a solution... any suggestions out there?
-Ryan[/quote] 
A 9100 in less than RV300. The ati fglrx drivers are known to be even more buggie with those cards. Just use the Xorg "radeon" driver.

Errors about PC timings could be errors from the bios attempting to asign IRQs that are conflicting. You can try booting without ACPI enabled.

---

### Post by acankat on 2006-06-11
[QUOTE=disturbed1]:-k

Is this a fresh install from the live cd using safe graphics mode? Because there is no mesa drivers that have ever been loaded on my systems.

What does this give you?
**lsmod | grep fglrx**
**dmesg | grep fglrx**



 
A 9100 in less than RV300. The ati fglrx drivers are known to be even more buggie with those cards. Just use the Xorg "radeon" driver.

Errors about PC timings could be errors from the bios attempting to asign IRQs that are conflicting. You can try booting without ACPI enabled.[/QUOTE]

grep fglrx :


fglrx                 388908  0
agpgart                34888  2 fglrx,amd64_agp


dmesg | grep fglrx : 

[4294696.409000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294696.411000] [fglrx] Maximum main memory to use for locked dma buffers: 1172 MBytes.
[4294696.411000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294698.023000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[4294698.023000] [fglrx:firegl_unlock] *ERROR* Process 4356 using kernel context

Well, this is a fresh installation with stock ati drivers installed. I've tried every king of guide about the ati drivers, none seems to be working. Always the same problem.

By the way the card is a x1600 pro and the board is a nf3 and.

I'll try this acpi thing...

---

### Post by Poisonsnak on 2006-06-11
On my desktop I had to install ubuntu in "safe graphics mode" and after applying your fix my video looks a lot better.  I'm just wondering if my xorg.conf file is ok like this:

```
Section "Device"
        Identifier  "ATI Technologies, Inc. R480 [Radeon X850XT Platinum (PCIE)]"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection
```

I can still see that driver "vesa" thing in there, is that ok since the next one is fglrx?

---

### Post by disturbed1 on 2006-06-11
[quote=Poisonsnak]On my desktop I had to install ubuntu in "safe graphics mode" and after applying your fix my video looks a lot better.  I'm just wondering if my xorg.conf file is ok like this:

```
Section "Device"
        Identifier  "ATI Technologies, Inc. R480 [Radeon X850XT Platinum (PCIE)]"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection
``` 
I can still see that driver "vesa" thing in there, is that ok since the next one is fglrx?[/quote]

Your driver is fine ;)

Notice it says "aticonfig-Device[0]" under your screen section, you'll have an aticonfig-Device screen.

You can put fglrxinfo in the command line, it will tell you if the drivers are enabled or not.


@acankat, 

The acpi was for **deboring21.**
Are you restarting the PC after you install the restricted drivers? Or are you attempting to pass other commands into the xorg.conf?

---

### Post by evil_elman on 2006-06-11
Okay... Followed the guide... However, the xorg.conf still states the following:

Section "Device"
	Identifier  "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

2D is still sluggish... 3D works fine...

And... Is it still supposed to say 'Vesa'?

---

### Post by Dillius on 2006-06-11
I'm still unable to get ANY video with Vesa or VGA drivers using an X800 GTO. Anyone else use this card?

---

### Post by disturbed1 on 2006-06-11
[quote=evil_elman]Okay... Followed the guide... However, the xorg.conf still states the following:

Section "Device"
    Identifier  "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
    Driver      "vesa"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
EndSection

2D is still sluggish... 3D works fine...

And... Is it still supposed to say 'Vesa'?[/quote] 
Yes, look under your screen section, the aticonfig changes your xorg.conf file by putting in 2 new entries under the device section and screen section. And yes, 2d is sluggish, you can try to add this option

"NoDRI"  "yes"

ATI is working on improving the driver options and features. I have faith considering the amount of improvement from 8.24 to 8.25.

If you want to see exactly what Xorg is doing, type this in

cat /var/log/Xorg.0.log | grep fglrx

---

### Post by washman on 2006-06-11
when i tried:
[PHP]sudo apt-get install xorg-driver-fglrx fglrx-control libqt3-mt[/PHP]

it showed "Couldn't find package fglrx-control"
can you show me your source list pls?

---

### Post by disturbed1 on 2006-06-11
[quote=washman]when i tried:
[php]sudo apt-get install xorg-driver-fglrx fglrx-control libqt3-mt[/php] 
it showed "Couldn't find package fglrx-control"
can you show me your source list pls?[/quote] 
deb [http://us.archive.ubuntu.com/ubuntu/]("http://us.archive.ubuntu.com/ubuntu/") dapper main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/]("http://us.archive.ubuntu.com/ubuntu/") dapper main restricted
deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") dapper-security main restricted
deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") dapper-updates main restricted

I won't use non ubuntu.

```

$ sudo apt-cache search fglrx-control
Password:
fglrx-control - Control panel for the ATI graphics accelerators

``` 
It's in the restricted security repo.

---

### Post by gambal on 2006-06-12
Is there a way to use this method without a total clean insall? Can I just configure my xorg.conf again to use the safe mode vesa drivers and uninstall some packages and then try this? My system has a Raden 9550 AGP card.

I really don't feel like doing a clean install because I don't use Ubuntu fot games that much and I'm waiting/hoping for a driver update that will fix this problem.

---

### Post by cheema on 2006-06-12
[QUOTE=gambal]Is there a way to use this method without a total clean insall?[/QUOTE]

That was my reaction as well.  I did not want to re-install.  This is what I did and it worked for me:

1. Copy /etc/X11/xorg.conf to a safe place.
2. Edit the above file, locate the "Device" section that has the oss "ati" driver specified.
3. Replace the "ati" in the above section with "vesa".
4. Then apt-get the software as suggested in the original post.
5. sudo aticonfig --initial --overlay-type=Xv
6. Edit the /etc/X11/xorg.conf again.  Make sure that all your "Screen" sections (I had 2, one created by Ubuntu and the other by ATI) are pointing to the newly created "aticonfig-Device[0]" Device section.
7. Reboot.

Thats it.

Reboot was required for me.  Simply restarting the server wouldn't do it.  The kernel module was not loading, even when I tried to manually modporbe it.  However Reboot fixed it.  Its all good now.

Maybe one day ATI will get their act together.  Until then I will try to buy Nvidia whenver I can.

---

### Post by disturbed1 on 2006-06-12
Once you restart run these commands to make sure fglrx was loaded

lsmod | grep fglrx

If something went wrong post the output of this

 LIBGL_DEBUG=verbose fglrxinfo

---

### Post by mzembe on 2006-06-12
My X700 works, I have a few issues with the Xgl server but..... 

I've noticed the aticonfig script doesn't modify your xorg properly in some instances, it might need to be 'vesa' initially or something strange. When it edited mine the Identifier/Device pair didn't match so I had an unused fglrx profile still using the original 'ati' driver. 
Anyways - I thought I'd post my xorg.conf that has multiple video card profiles hopefully to illustrate what your config file should look like. Currently, the X700 is the active profile and the fglrx drivers work fine:
> 
Section "Device"
        Identifier      "9800Pro"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option "KernelModuleParm" "agplock=0"
        Option "UseInternalAGPGART"     "no"
EndSection

Section "Device"
        Identifier      "X700Pro"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        ChipId          0x5e4b
        Option "KernelModuleParm" "agplock=0"
        Option "UseInternalAGPGART"     "no"
EndSection

Section "Device"
        Identifier      "8500le"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option         "UseFBDev"      "true"
        Option          "AGPMode"       "4"
        Option         "DRI"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "X700Pro"
        Monitor         "CM2111"
        DefaultDepth    24
        SubSection "Display"
                Depth           24




Now, I can't remember if the 8500 & 9800 profiles are working... but if I wanted to switch cards I would only need to change the 'Device' in the 'Screen' section to the appropriate identification string for a different card. I just made up identifier names that were short and to the point. For instance, whenever I next check out the 8500, before rebooting I just need to change Screen's Device to 8500le and the other video card entries will be ignored and the 'ati' driver will load with Options specified in the 8500 section.

---

### Post by mzembe on 2006-06-12
I hope that's not too confusing, it's 5am and I should be sleeping already. :) When I say I 'just made those names up' - they're in there like that and they work, that wasn't part of the illustration it's really part of my xorg.conf. You can fill in your own identifiers and they'll be fine. 
Just don't get too imaginative with any of the other fields. ;)

---

### Post by mzembe on 2006-06-12
.....oh yeah, also - It seems like the driver options I'm using for the 8500 aren't legal 'ati' options ... they might be left over from an older configuration where I was using a 'radeon' driver. It's harmless, they'll just be ignored if thats the case.

---

### Post by gambal on 2006-06-12
Thanks a lot Cheema, now it works. I don't even want to think _WHY_ it has to be done this way...

---

### Post by Sandsound on 2006-06-13
[QUOTE=disturbed1]marked the 11 updates, and marked my kernel and restricted modules for my kernel (K7 kernel for me)[/QUOTE]

Sorry if this is a dumb question... but what kernel updates ?

Where do i find these, i assume that its the same as useing the Update maneger ?

btw... Im running a Athlon64 with a ATI radeon 9800 and have tryed several ways over the past days, but still no 3d :-(
My 64bit instalation is running fine (dont wanna spoil that running a chroot), but Id like to try run a dualboot with a 32bit so I can play some games.

sandy@sandy32:~$ dmesg | grep fglrx
[4294697.798000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294697.799000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[4294697.799000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294698.752000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294698.753000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294698.753000] [fglrx] AGP detected, AgpState   = 0x1f004e09 (hardware caps of chipset)
[4294698.753000] [fglrx:firegl_unlock] *ERROR* Process 4548 using kernel context 0

sandy@sandy32:~$ lsmod | grep fglrx
fglrx                 388908  0
agpgart                34888  3 fglrx,amd64_agp,sis_agp

---

### Post by Valshar on 2006-06-13
ok, after some hours and some headbanging, I think I got this to work, it finally recognizes the x700, and got to up the resolution to 1280x800, but the ATI Control Panel just vanished from the applications, at least the shortcut. How can I get to it again now?

---

### Post by ido_ofir on 2006-06-14
hey, disturbed1,

thanks a lot for the explantion. it worked.

so, thanx for your help.

---

### Post by n00bWillingToLearn on 2006-06-14
[quote=Sandsound]Sorry if this is a dumb question... but what kernel updates ?

Where do i find these, i assume that its the same as useing the Update maneger ?
[/quote]

Yes, I believe that he just wanted to install other things for himself but it had nothing to do with the ATI drivers. All you need to do is update your system so yes, just using the update manager should be fine.

---

### Post by Sandsound on 2006-06-14
Hmm... Think I'll by myself an Nvidia insted, just hate to give up on something :sad: 

What troubles me most, is that some people actualy DO get it up and running, and that I had no problems with my amd64 instalation :confused:

---

### Post by DonQuixote on 2006-06-16
Grrrr.... I followed these directions to the "t" and get the fatal double drum sound on the login screen (When I login the screen goes blank with the exception of the mouse pointer).

I begining to think that there is a conflict with the sound card...

Sager 5860 laptop with an ATI 9600 Radeon Mobility graphics card...

Back to Breezy...

---

### Post by Dubbayoo on 2006-06-17
I have Dapper Drake with a Radeon 8500 and the latest ATI driver. I can't run GoogleEarth or fglrx-gears. Any suggestions here? I am getting:

**steve@ubu-6:~/Desktop$ fglrxinfo**
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
......................continues on for quite a while.

------------------------------------------------------------------------

**steve@ubu-6:~/Desktop$ dmesg | grep fglrx**
[17179614.840000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179614.848000] [fglrx] Maximum main memory to use for locked dma buffers: 1414 MBytes.
[17179614.848000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0[17179615.892000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179615.892000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179615.892000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179615.892000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179615.908000] [fglrx] total      GART = 67108864
[17179615.908000] [fglrx] free       GART = 51113984
[17179615.908000] [fglrx] max single GART = 51113984
[17179615.908000] [fglrx] total      LFB  = 126169088
[17179615.908000] [fglrx] free       LFB  = 114274304
[17179615.908000] [fglrx] max single LFB  = 114274304
[17179615.908000] [fglrx] total      Inv  = 0
[17179615.908000] [fglrx] free       Inv  = 0
[17179615.908000] [fglrx] max single Inv  = 0
[17179615.908000] [fglrx] total      TIM  = 0

------------------------------------------------------------
**steve@ubu-6:~/Desktop$ lsmod | grep fglrx**
fglrx                 388908  8
agpgart                34888  2 fglrx,intel_agp

---

### Post by Klemik on 2006-06-18
[QUOTE=Ivhassel]The **latest** ATI drivers don't work with **R280** chips. Install the previous ATI drivers. Howto is around somewhere.
Good luck :)[/QUOTE]

Can you show where ? plz

I have same problem as most of users, I've installed newest ati drivers...

```

dmesg | grep fglrx
[17179718.480000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179718.484000] [fglrx] Maximum main memory to use for locked dma buffers: 679 MBytes.
[17179718.484000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179719.868000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179719.868000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179719.868000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179719.872000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179719.892000] [fglrx] total      GART = 67108864
[17179719.892000] [fglrx] free       GART = 51113984
[17179719.892000] [fglrx] max single GART = 51113984
[17179719.896000] [fglrx] total      LFB  = 59764736
[17179719.896000] [fglrx] free       LFB  = 49278976
[17179719.896000] [fglrx] max single LFB  = 49278976
[17179719.896000] [fglrx] total      Inv  = 0
[17179719.896000] [fglrx] free       Inv  = 0
[17179719.896000] [fglrx] max single Inv  = 0
[17179719.896000] [fglrx] total      TIM  = 0

```

```

lsmod | grep fglrx
fglrx                 391756  8
agpgart                36784  2 fglrx,intel_agp

```

```

fglrxinfo
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[...]

same for glxinfo

```

```

uname -a
Linux Klemik 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

```

```

Log from driver install:

cat /usr/share/fglrx/fglrx-install.log
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.15-25-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.15-25-686'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC4.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC4
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.15-25-686'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- recreating module dependency list
- trying a sample load of the kernel modules
done.

```

```

cat /etc/X11/xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "pl"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

Xorg 7.0.0
Radeon 9200 SE

I'm dealing with this problem for about 2 days, tried I think all tips and tricks avaible on forums, but they all give me same problem listed above :(

---

### Post by deboring21 on 2006-06-19
Ok, well I went through the install and when I reboot the system, I get past the part where its: "Uncompressing Linux... Ok, booting the kernel." Then I get a message: "[4294669.540000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC." It used to get past that part during the boot up with 5.10, but now it just hangs there... and its still hanging on my other PC as of 10 minutes so far... please help me
-Ryan

---

### Post by disturbed1 on 2006-06-19
You either have a buggy bios, or didn't update your kernel. Trying passing this boot option, then make sure you have the latest kernel.

acpi_skip_timer_override

---

### Post by Braino on 2006-06-21
Edit: nm, should have kept reading :P

---

### Post by rapido on 2006-06-25
disturbed1,

Thanks for the great how to.  Really helped me with getting the ATI card properly set up on my Macbook Pro.  

I do have a question though.  Everything looks great...except...menu fonts in certain applications.  I've installed xmms and emacs.  Both of these applications do not share the great looking, small fonts that the Desktop and majority of the applications now have.  xmms and emacs (gnu) both have much larger menus and fonts.  These look closer to the original VESA mode before instlaling fglrx.

Hope this makes sense.  Any ideas?

---

### Post by Vincent_Lin on 2006-07-05
Hi,

I have an IBM T42 with 9600M.

I followed the procedure at the start of this howto and it seems that fglrx is installed.  Really!  Because I can then proceed to install xgl/compiz and all the fancy stuff are working.  Cube is my favorite (Ctrl-Alt mouse drag over to another workspace)

However, the weird part is that when I glxinfo | grep rendering, and it says direct rendering is no.  fglrxinfo hangs the machine.  Neither Ctrl-Alt-F1 Ctrl-Alt-Backspace would do anything.

Tux-Racing (or planet-tux something) would not run at all, but hangs.

I could only say it is weird, because the only reason for me for fglrx driver installation is to run xgl/compiz, and as it is working, I do not worry too much about it.

Vincent

---

### Post by Braino on 2006-07-05
[QUOTE=Vincent_Lin]Hi,


However, the weird part is that when I glxinfo | grep rendering, and it says direct rendering is no.  fglrxinfo hangs the machine.  Neither Ctrl-Alt-F1 Ctrl-Alt-Backspace would do anything.

Vincent[/QUOTE]

That's what threw me off too. It works differently for people who have ati cards, because this is all running on display 1.0, not 0.0 (some work-around that I don't know much about). So what you'll have to do is specifiy the display like so:
```

fglrxinfo -display :1.0

```

---

### Post by c45p31 on 2006-07-19
Hi,
I have an ATI RADEON Mobility 9000 Pro. I read a lot of your replyes here and I partialy did it.

I say partialy because of some errors. The errors are in 3 txt files attached.

CAN YOU hELP ME?

Thank you.

---

### Post by Sonic Alpha on 2006-07-20
I'm trying to get my 9800 pro working properly.  I thought I'd followed this to the letter, however when I do an fglrxinfo I get this: -

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

However, I do have the ati control panel working fine.

---

### Post by Braino on 2006-07-20
As I mentioned before Sonic Alpha, if you are using an Ati card, you will probably need to tell fglrxinfo to look at display 1.0, not 0.0

-Braino

---

### Post by jrjr on 2006-07-20
When I try that command these 2 ways I get

jack@gigabyte:~$ fglrxinfo -display :1.0
Error: unable to open display :1.0

jack@gigabyte:~$ sudo fglrxinfo -display :1.0
Password:
Error: unable to open display :1.0


Do you know why?

---

### Post by Mats962004 on 2006-07-20
I have just installed dapper but have had no luck getting my 9200 working with fglrx.As soon as i try to load fglrx I am not able to start x.The only errors I get is from xorg.log.
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers/fglrx_drv.so [0xb73c1530]
3: /usr/bin/X(LoadModule+0xa79) [0x80a2b56]
4: /usr/bin/X(xf86LoadModules+0x96) [0x809d990]
5: /usr/bin/X(InitOutput+0x2e2) [0x809dcc3]
6: /usr/bin/X(main+0x292) [0x806debe]
7: /lib/tls/libc.so.6(__libc_start_main+0xd4) [0xb7dcdea4]
8: /usr/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 4.  Server aborting
The drivers are 8.24 installed wih build-pkg.I have tried different versions and the one from repo but it is always the same error.The radeon driver starts no problem.If anyone has seen this or no what it is please let me know.Thanks.

---

### Post by adwb on 2006-09-03
This method worked on my MSI MS-1039 notebook with a Radeon Mobility X1600.

Thanks

---

### Post by jubilee33 on 2006-09-03
I have a laptop with Radeon Xpress 200m (128mb shared memory) on board.  I just did a fresh Ubuntu Dapper install and my x server won't start.  I already tried asking the question and I got a suggestion which I followed.

> dpkg-reconfigure xserver-xorg

I tried changing the driver to "ati" the first time and then when I failed, I changed it to "radeon" as mentioned in other threads.  I also did the following:

> sudo nano /etc/X11/xorg.conf

changing to "radeon" in the device section.  I got the same result: no x server.  I'm still very new in Ubuntu so I'm at a loss as what to do next.  What can I do to troubleshoot step by step?

---

### Post by ppuppet on 2007-11-03
Hi all,

I'm having some issues trying to configure my x700 :(

When I try to aticonfig the output is something like this:

> pedro@orion:~$ sudo aticonfig --initial --overlay-type=Xv
Uninitialised file found, configuring.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbf9e09dd ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7cf692b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c9f050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:06 133122     /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:06 133122     /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c7b000-b7c7c000 rw-p b7c7b000 00:00 0 
b7c7c000-b7c7e000 r-xp 00000000 08:06 99247      /lib/tls/i686/cmov/libdl-2.6.1.so
b7c7e000-b7c80000 rw-p 00001000 08:06 99247      /lib/tls/i686/cmov/libdl-2.6.1.so
b7c80000-b7c81000 rw-p b7c80000 00:00 0 
b7c81000-b7c85000 r-xp 00000000 08:06 131891     /usr/lib/libXdmcp.so.6.0.0
b7c85000-b7c86000 rw-p 00003000 08:06 131891     /usr/lib/libXdmcp.so.6.0.0
b7c86000-b7c88000 r-xp 00000000 08:06 131880     /usr/lib/libXau.so.6.0.0
b7c88000-b7c89000 rw-p 00001000 08:06 131880     /usr/lib/libXau.so.6.0.0
b7c89000-b7dcd000 r-xp 00000000 08:06 99241      /lib/tls/i686/cmov/libc-2.6.1.so
b7dcd000-b7dce000 r--p 00143000 08:06 99241      /lib/tls/i686/cmov/libc-2.6.1.so
b7dce000-b7dd0000 rw-p 00144000 08:06 99241      /lib/tls/i686/cmov/libc-2.6.1.so
b7dd0000-b7dd3000 rw-p b7dd0000 00:00 0 
b7dd3000-b7df6000 r-xp 00000000 08:06 99249      /lib/tls/i686/cmov/libm-2.6.1.so
b7df6000-b7df8000 rw-p 00023000 08:06 99249      /lib/tls/i686/cmov/libm-2.6.1.so
b7df8000-b7ee5000 r-xp 00000000 08:06 131874     /usr/lib/libX11.so.6.2.0
b7ee5000-b7ee9000 rw-p 000ed000 08:06 131874     /usr/lib/libX11.so.6.2.0
b7ee9000-b7ef6000 r-xp 00000000 08:06 131895     /usr/lib/libXext.so.6.4.0
b7ef6000-b7ef7000 rw-p 0000d000 08:06 131895     /usr/lib/libXext.so.6.4.0
b7ef7000-b7ef8000 rw-p b7ef7000 00:00 0 
b7ef8000-b7eff000 r-xp 00000000 08:06 131917     /usr/lib/libXrender.so.1.3.0
b7eff000-b7f00000 rw-p 00006000 08:06 131917     /usr/lib/libXrender.so.1.3.0
b7f00000-b7f05000 r-xp 00000000 08:06 131915     /usr/lib/libXrandr.so.2.1.0
b7f05000-b7f06000 rw-p 00005000 08:06 131915     /usr/lib/libXrandr.so.2.1.0
b7f06000-b7f10000 r-xp 00000000 08:06 65347      /lib/libgcc_s.so.1
b7f10000-b7f11000 rw-p 0000a000 08:06 65347      /lib/libgcc_s.so.1
b7f11000-b7f14000 rw-p b7f11000 00:00 0 
b7f14000-b7f2e000 r-xp 00000000 08:06 65300      /lib/ld-2.6.1.so
b7f2e000-b7f30000 rw-p 00019000 08:06 65300      /lib/ld-2.6.1.so
bf9cc000-bf9e1000 rw-p bf9cc000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
 
Then it just deletes the xorg.conf file... I'm stuck with this problem.. Can anyone help me out on this?

Cheers

---

### Post by Yellow Pasque on 2007-11-04
ppuppet, Try using the ```
dpkg -reconfigure -phigh xserver-xorg
``` command to auto-generate your xorg.conf

---

