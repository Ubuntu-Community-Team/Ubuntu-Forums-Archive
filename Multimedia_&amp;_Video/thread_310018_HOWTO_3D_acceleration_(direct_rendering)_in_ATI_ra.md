---
title: "HOWTO: 3D acceleration (direct rendering) in ATI radeon mobility U1 (IGP 320m)"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by ]Nbx*cmD[ on 2006-11-30
Hi all,

I've got a Fujitsu Siemens Amilo A laptop with an ATI radeon mobility IGP 320 graphics card, also called U1.

People who owns this computer, or other laptops using the same card, will for sure know how weird it is and how difficult is to get it working with direct rendering.

Well, I've been looking up during months on hundreds of forums, mailing lists and IRC channels without coming up to a solution. The main problem with this laptop is that, if I understood well, it uses the same IRQ (irq 11) for different devices, resulting in a system crash when you try to configure the 3d acceleration.

I've found a pretty difficult solution for it in an [amilo gnu/linux users mailing list]("http://tech.groups.yahoo.com/group/amilo/message/530"), consisting in modifying the DSDT-table. For getting it to work you have to modify the kernel source code and compile it again, but I'm a very lazy person and I prefered to go on with the research.

Well, I'll stop talking about pseudo-solutions and go straight to the subject. Here you are a **VERY EASY HOWTO** for getting your U1 direct rendering enabled and being able to play Quake III for hours ;)

Only four steps, since the fifth one is just checking everything worked:


[LIST]
[*] **FIRST STEP**: Downloading the Alternate Install CD

Download the Alternate Ubuntu Edgy Eft Install CD from the official Ubuntu website. You can find it here: [DOWNLOAD]("ftp://ftp.rediris.es/sites/releases.ubuntu.com/releases/edgy/ubuntu-6.10-alternate-i386.iso")


[*] **SECOND STEP**: Installing Ubuntu Edgy Eft

Just burn the ISO and boot the cd in your laptop cd tray.

Choose the text-mode install and follow the instructions carefully.


[*] **THIRD STEP**: Booting Ubuntu Edgy Eft on recovery mode

Once the installation finished, your computer will reboot and you'll have some seconds to press the ESC key and enter grub.

Choose the RECOVERY MODE boot method.


[*] **FOURTH STEP**: Adding a flag to grub's menu.lst config file

Type the following in the terminal:

```
sudo vi /boot/grub/menu.lst
```

Change vi for your favourite text-mode editor, if you haven't realized yet that vi is simply the best one ;)

Go to the section looking similar to:

```

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

```

And change the kernel line as following:

```

kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash irqpoll

```

So, add the **irqpoll** parameter.

/* For spanish and catalan speakers, irqpoll will solve your IRQPOLLo :-# (bad joke, you're lucky if you didn't understand) */

Ok, all done. Just <esc> :wq (or write the changes and exit from your favourite editor) and reboot your machine:

```
sudo reboot
```


[*] **FIFTH STEP**: Feeling very happy and installing Quake III immediately

If you are as lucky as me, once your laptop rebooted, you'll be able to use direct rendering!

You can test it by typing the following command in a console:

```

glxinfo | grep direct

```

And you should get a line similar to the following one:

```

direct rendering= Yes

```

[/LIST]

That's all, easy isn't it?

In the kernel docs you can read 'The "irqpoll" boot parameter reduces driver initialization failures'.

Hope it worked!

---

### Post by Anthem on 2006-12-01
Amazing work, I look forward to trying this.

Have you tried using Compiz/Beryl with this yet?

EDIT:  Does this use the open-source radeon driver?

---

### Post by ]Nbx*cmD[ on 2006-12-01
I didn't try beryl, I just think if it's working... don't touch it :p

I don't exactly know which driver is it using, it's just the ati driver coming with ubuntu.

Oh btw I found out some "collateral effects" resulting in system crashes... you have to think you are ignoring some irq issues...

Anyway, I'm gonna put two entries in my grub, one using irqpoll and the other not using it, so I can choose when I want 3D and when I don't.

See you!

---

### Post by z!cHz@cH on 2006-12-03
=D> 

People who have problems with their 320/340m card; this solves a lot of problems!!

This also works for Fedora!

Thanks a lot for the good work ]Nbx*cmD[ :o

---

### Post by rlynch on 2006-12-12
Anthem, did this solve your issue? I know you have the same card as I do. . .


z!cHz@cH, did this work with beryl?


EDIT, do I have to do a 'text mode install'?

Anthem, edgy uses the propriety(sp)drivers, which normally breaks when i boot, but this walkthrough says to add that parameter in grub, which if it works would turn out to be quite nice.

Looks like I have something to do tomorrow.


EDIT2 - and just to be sure, in your Xorg.conf file it identifies your video card as this correct?
>         Identifier      "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"

---

### Post by rlynch on 2006-12-12
this did nothing for me. . .but then again i couldnt even get it to install with the alternate install cd. it kept freezing on differnt parts, used 2 freshly burned cds, both passing the integrity checks, so i dunno.

I grabbed the edgy desktop i386, burned it, and installed it that way. setup my xorg.conf to use 'flglx' driver, instead of ati. did your irqpoll kernel parameter, and rebooted, it scrolled a 'irq too many/much' something or another, then gave me the 'cant load xorg' error that it always does.


odd thing is when i do that command it's already showing that direct acceleration is running(even before the install on my last one as well)
but i know 3d accel isn't working, cause anything 3d just runs down my processor resources.

so then again, i dunno

---

### Post by rlynch on 2006-12-13
so, i found an older version of xorg by default supports the IGP chipset

[http://forums.fedoraforum.org/showthread.php?t=1740](http://forums.fedoraforum.org/showthread.php?t=1740)

there is where i found them takling about it for fedora. . .im running edgy now, any idea on how to revert back to xorg vers 6.8?

---

### Post by ]Nbx*cmD[ on 2006-12-14
Hi,

I've read about this solution as well... the way to revert back to x.org-6.8 is by removing your current one and then installing the old 6.8...

---

### Post by rlynch on 2006-12-14
I dunno enough to do this, hence why I asked.

I dunno if I should add the --purge command, where to get 6.8, etc

---

### Post by ]Nbx*cmD[ on 2006-12-14
Well...

I warn you you'll have to do all this from the console in text mode (tty), and it may require some x.org knowledge... You can break your system by trying this so... i'm not responsible of your acts hehehe

I guess the way to do it is: (it should work, but i didn't try it)

1 · Add an x.org-6.8 repository to sources.list, these commands will do it automatically:

```
 
sudo echo "deb http://debian.linux-systeme.com unstable main" >> /etc/apt/sources.list
sudo echo "deb-src http://debian.linux-systeme.com unstable main" >> /etc/apt/sources.list

```

2 · Comment ALL THE LINES but the last two ones in your sources.list. Just add a # at the line starting. You can do it by using your favourite text editor.

3 · From a tty, remove your current x.org

```

sudo apt-get remove xserver-xorg xserver-xorg-core

```

Apt will ask for your confirmation to erase LOTS of packages, say yes

4 · Install the old X.org-6.8

```

sudo apt-get install xserver-xorg xserver-xorg-core

```

I guess it'll ask for your confirmation to install lots of packages now... say yes again.

5 · Reboot and pray

Hope it helped... and hope you made a backup of your important configs and so

---

### Post by ]Nbx*cmD[ on 2006-12-14
Oops sorry!

For some weird reason, sudo echo "whateveryouwant" >> restricted_file is not working!
You should start by typing ```
sudo su
``` and then run the rest of the commands without sudo at the beggining of the line (or keeping it, doesn't really matter).

---

### Post by rlynch on 2006-12-19
I do thank you for the steps on how to do this, but i gotta say i am exhausted with breaking my laptop and having to reinstall ubuntu. I wanted my last install to be it but I got odd un-upgradable errors on a few repos, so I went ahead and put edgy back on.

If anyone has the spare time, and has the card we have, please try this and let me know how many FPS you get from 'glxgears -printfps' i get ~250 on default size, then ~80 when i full screen it. I hear you need about 500 to run beryl well enough. and **** this card has 256mb of ram(even tho it's shared), it should be able to run beryl without lag when playing video or doing anything else on the computer(i can play a video at about 480x350, but if i full screen it, it drops frames).

hopefully someone else out there has the time and patience to try this out. i just can't go through it anymore, i want a 'stable' OS, which is why i switched to linux.

---

### Post by daller on 2006-12-27
What driver do you suggest using?

radeon?

fglrx?

And does it have to be from the Alternate CD?

---

### Post by mayhemt on 2006-12-27
there are a bunch of HOWTOs for ATI drivers, follow them... 
shortly..download from ati.com, run with buildpkg option, install, change xorg.conf to pickup "fglrx", reboot, check fglrxinfo, glxinfo | render

& then finally if all the above doesnt help,...run  
```

$./ati-driver-......run 

```

& u will get the GUI installer,  select install driver 8.XXX on... 
this will overwrite the mesa files if they are installed..
without any parameters
good luck :-k

---

### Post by Anthem on 2007-01-06
> **mayhemt said:**
> there are a bunch of HOWTOs for ATI drivers, follow them... 
shortly..download from ati.com, run with buildpkg option, install, change xorg.conf to pickup "fglrx", reboot, check fglrxinfo, glxinfo | render

& then finally if all the above doesnt help,...run  
```

$./ati-driver-......run 

```

& u will get the GUI installer,  select install driver 8.XXX on... 
this will overwrite the mesa files if they are installed..
without any parameters
good luck :-k
The fglrx driver doesn't support the 320m.

---

### Post by Mike_Longbow on 2007-01-12
OMG... IRQPOLLo...
Surely that's a bad joke, buddy, hahaha
Spanish is my mother language ;)
Anyway, great howto! Worked with my friend's ATI. Too bad I got myself a pretty odd graphics card:
Silicon Motion Lynx EM+
Does anyone knows anything about this?
...Anything.

---

### Post by moshuptrail on 2007-01-18
Is Edgy REQUIRED for this solution?  
I tried irqpoll with Dapper and it didn't help my ATI card.  But the system did crash shortly after booting and paging to this forum!  :)

---

### Post by ]Nbx*cmD[ on 2007-01-25
Well... I finally gave up with my solution, I have to admit it's more a "crappy patch" than a real solution, since the system keeps on crashing all the time.

I went back to the old vesa times :(

Did somebody find a solution for the random crashes? Maybe it'd be easier to fix the crashes than to find a new solution for the direct rendering...

---

### Post by Anthem on 2007-02-08
Can't try it out right now, but I found a Gentoo howto that claims the 320m needs the following line added in x.org:

Option ColorTiling "no"

Like I said, I haven't tested it.  But I'll try it, next time around.  It's my wife's laptop now, and I'm not allowed to break it until April.

---

### Post by rlynch on 2007-02-08
so just add that line and change the driver over to flglx?

---

### Post by Anthem on 2007-02-09
> **rlynch said:**
> so just add that line and change the driver over to flglx?
No.  

The current problem is that the 320m isn't supported by ATI's proprietary driver or by the open-source driver.  Supposedly, it's possible to get the open-source driver to work, but nobody's had success with it.

---

### Post by marranzano on 2007-02-11
i have a  ATI Technologies Inc Radeon Mobility U1 [320m] on my presario 2110us and it works almost ok with ubuntu :) 
screen is 1024x768 (changed colors from 24 to 16 and got x2 fps boost)
(gnome+beryl+gkrellm):

[[IMG]http://img261.imageshack.us/img261/2721/screenshot1ry2.th.png[/IMG]](http://img261.imageshack.us/my.php?image=screenshot1ry2.png)  [[IMG]http://img112.imageshack.us/img112/4523/screenshot4co2.th.png[/IMG]](http://img112.imageshack.us/my.php?image=screenshot4co2.png)

glxgears -printfps (normal window)
libGL warning: 3D driver claims to not support visual 0x4b
3404 frames in 5.0 seconds = 680.406 FPS
3611 frames in 5.0 seconds = 722.138 FPS
3611 frames in 5.0 seconds = 722.169 FPS
3661 frames in 5.0 seconds = 732.141 FPS
3648 frames in 5.0 seconds = 729.546 FPS

glxgears -printfps (full screen window)
810 frames in 5.0 seconds = 161.855 FPS
811 frames in 5.0 seconds = 162.066 FPS
806 frames in 5.0 seconds = 161.050 FPS
809 frames in 5.0 seconds = 161.783 FPS
804 frames in 5.0 seconds = 160.795 FPS

```
$ cat /etc/X11/xorg.conf
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "dbe"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "synaptics"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
        Option          "XkbVariant"    "intl"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
#       Option          "Device"                "/dev/input/event2"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
    Option "MinSpeed" "0.09"
    Option "MaxSpeed" "0.18"
    Option "BottomEdge" "4100"
    Option "FingerLow" "25"
    Option "LeftEdge" "1700"
    Option "MaxTapMove" "220"
    Option "MaxTapTime" "180"
    Option "FingerHigh" "30"
    Option "VertScrollDelta" "100"
    Option "TopEdge" "1700"
    Option "AccelFactor" "0.0015"
    Option "RightEdge" "5900"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option  "DPMS"
        Option "XAANoOffscreenPixmaps" "1"

#       Option "AGPMode" "4"            # 1-8 Does not affect PCIE models.
#       Option "AGPFastWrite" "1"       # 1/0 Does not affect PCIE models.
#       Option "EnablePageFlip" "1"     # 1/0 Increases 3D performance substantially seemingly in XAA mode only
#       Option "backingstore" "1"
#       Option "AllowGLXWithComposite" "1"
#       Option "RenderAccel" "1"
#       Option "AGPSize" "64"           # 0-64 Megabytes of gart (system) memory used. Wrongly defaults to 8MB sometimes, see your logfile. Bigger seems better.
#       Option "AccelMethode" "EXA"     # XAA/EXA
#       Option "AccelDFS" "1"   # 1/0 On for PCIE, off for AGP Manpage: Use or don't use accelerated EXA DownloadFromScreen hook when possible.
#       Option "SubPixelOrder" "NONE"
#       Option "DynamicClocks" "1"
#       Option "bioshotkeys" "1"
#       Option "ColorTiling" "1"        # 1/0 Increases 3D performance substantially affected stability only positively on my system
#       Option "DRI" "true"
#       Option "OpenGLOverlay" "off"     #aggiunto io
#       Option "VideoOverlay" "on"       #aggiunto io
#       Option "mtrr" "on"               #aggiunto io

EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
    VendorName "Generic"
    ModelName "Flat Panel 1024x768"
    HorizSync 31.5-55
    VertRefresh 40-70
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard" "CoreKeyboard"
        InputDevice     "Configured Mouse" "CorePointer"
        InputDevice     "Synaptics Touchpad" "AlwaysCore"
#       Option          "AIGLX" "true"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
        Option "Composite" "Enable"
#       Option "RENDER" "Enable"
EndSection
```

```
$ cat .drirc 
<driconf>
    <device screen="0" driver="radeon">
        <application name="Default">
            <option name="force_s3tc_enable" value="false" />
            <option name="no_rast" value="false" />
            <option name="fthrottle_mode" value="2" />
            <option name="tcl_mode" value="3" />
            <option name="texture_depth" value="0" />
            <option name="def_max_anisotropy" value="1.0" />
            <option name="no_neg_lod_bias" value="false" />
            <option name="texture_units" value="3" />
            <option name="dither_mode" value="0" />
            <option name="hyperz" value="true" />
            <option name="round_mode" value="0" />
            <option name="color_reduction" value="1" />
            <option name="vblank_mode" value="0" />
            <option name="allow_large_textures" value="1" />
        </application>
    </device>
</driconf>
```

```
$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 4x NO-TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2f 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

---

### Post by rlynch on 2007-02-13
dunno how you got up to 700, but from using your xorg, i went from 220 to 310fps

---

### Post by marranzano on 2007-02-13
> **rlynch said:**
> dunno how you got up to 700, but from using your xorg, i went from 220 to 310fps

make sure you also use the .drirc file, if you have the same graphic card just copy and paste in your users home dir....
ps. the glxgears fps is after a fresh boot, after a day of pc usage it goes down to ~570fps

also I have the default module that came with 6.10 (i think the string 
[INDENT]Driver          "ati"[/INDENT]
is a bit missleading... i guess it reverts to the radeon module ???

this is the interested part of lsmod:
[INDENT]radeon                118816  2 
drm                    74644  3 radeon
ati_agp                10636  1 
agpgart                34888  2 drm,ati_agp[/INDENT]

---

### Post by rlynch on 2007-02-13
i just did the drirc file, and rebooted. same fps

when i do lsmod i dont see anything ati or radeon related

another thing, when i do 'glxinfo' it says 'direct rendering: no'

---

### Post by marranzano on 2007-02-13
> **rlynch said:**
> i just did the drirc file, and rebooted. same fps

when i do lsmod i dont see anything ati or radeon related

another thing, when i do 'glxinfo' it says 'direct rendering: no'
do you have mesa libs installed?
what video module are you using?

ps. i have ubuntu since only a few days (moved from mandriva) so i don't know how to use apt that well... if you can tell me how to check installed packages i'll list the relevant files i have installed on my pc ;)
edit: did it myself...

$ sudo dpkg --get-selections |grep mesa
[INDENT]libgl1-mesa-dev                                 install
libgl1-mesa-dri                                 install
libgl1-mesa-glx                                 install
libglu1-mesa                                    install
libglu1-mesa-dev                                install
mesa-common-dev                                 install
mesa-utils                                      install
[/INDENT]

i have also have
[INDENT]xserver-xorg-video-ati
driconf
xdriinfo[/INDENT]
packages installed...

pps. (just to make sure) the file is ".drirc" and not "drirc"

---

### Post by ]Nbx*cmD[ on 2007-02-25
Man, i'm impressed, you did what seemed impossible O_o'

Do you really have direct rendering? It doesn't randomly crash?

Really, congratulations, I've spent ages trying to fix it! Some weeks ago a huge speaker fell down over my poor old amilo-a laptop and crashed it completely, so i had to buy a new one. 

Fortunately I'm in China now and I found a really good laptop for just 460&#8364;, I could try some livecds before buying it so that i was absolutely sure everything would work. 

I really took this 320m thing as a personal challenge, a "pity" I can't test your solution now!!!

---

### Post by sonikokaruto on 2007-03-03
@marranzano

I have the same exact laptop, wich version of ubuntu are you using?

and if i want to enable the 3d acceleration like you did, do i just copy and paste the code you posted?

I'm asking because i still use knoppix 3.4 and i never got it working ^^U

thanks in advance

---

### Post by daller on 2007-04-06
> **marranzano said:**
> 

```
$ cat .drirc 
<driconf>
    <device screen="0" driver="radeon">
        <application name="Default">
            <option name="force_s3tc_enable" value="false" />
            <option name="no_rast" value="false" />
            <option name="fthrottle_mode" value="2" />
            <option name="tcl_mode" value="3" />
            <option name="texture_depth" value="0" />
            <option name="def_max_anisotropy" value="1.0" />
            <option name="no_neg_lod_bias" value="false" />
            <option name="texture_units" value="3" />
            <option name="dither_mode" value="0" />
            <option name="hyperz" value="true" />
            <option name="round_mode" value="0" />
            <option name="color_reduction" value="1" />
            <option name="vblank_mode" value="0" />
            <option name="allow_large_textures" value="1" />
        </application>
    </device>
</driconf>
```


Where did you place this file? - And what does it do?

---

### Post by bjohan on 2007-04-24
I finally think i got it to work. After trying all the things mentioned in this thread :) but not the .drirc-stuff since i did not find any information about this file. But what finally made it work is what is mentioned in the "amilo gnu/linux users mailinglist". This is how i did it:
```

sudo apt-get install iasl
sudo cat /proc/acpi/dsdt > DSDT.dat
iasl -d DSDT.dat

```

Now comes the somewhat sketchy bit, edit the file DSDT.dsl so that it compiles nicely using

```

iasl -tc DSDT.dat

```

This might sound terrifying, but it is not if you have a little bit of experience programming. There is not straight forward way to explain this since it might differ a bit between BIOS-versions and what amilo you have. I got one warning and two errors, The errors was due to "AnyAcc" being set where Byte access was required, Changing "AnyAcc" to "ByteAcc" on the two lines solved that problem, i then fixed the warning, Since it compiles with the warning you might leave it as is, but i dont know if it will cause any problems. 

Anyway, once it all compiles change the irq according to what he did in the mailinglist where there are multiple IRQ's separated by commas i just entered one irq between the {}'s and it appears to work for me. the hen save the file and compilet iagain using

```

iasl -tc DSDT.dat

```

Now to make the new DSDT be loaded at boot time

```

sudo cp DSDT.amp /etc/initramfs-tools/
sudo mkinitramfs -o /boot/initrd.img-`uname -r`
[\code]

then reboot :)

my xorg.conf uses the ati driver and i pass the irqpoll option to the kernel at boot time, i do not know if this is necesary or not. And also make sure you have Load "dri" in the Modules section. 

then reboot :)
This solution appears to be stable 
[code]
bjohan@kirk:~$ uptime
 21:51:58 up  2:38,  2 users,  load average: 2.27, 2.32, 2.30
bjohan@kirk:~$ 

```

before it crashed after 10-15 seconds if I had DRI enabled

btw, I'm using fiesty. Good luck and i hope this helps!

PS. There might be a finished customized DSDT at [http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php) for your computer

---

### Post by anseeuw.karel on 2007-04-25
Hi

I've also got a Fujitsu Siemens Amilo A laptop with an ATI radeon mobility IGP 320 graphics card. 
I'm running Feisty. I've got this card working by doing this:

First I added the irqpoll parameter like mentioned above.
Then i removed the propriertary fglrx driver like mentioned @ [https://help.ubuntu.com/community/RadeonDriver#head-a0bf0ca17168200ea3dd810ae505419bdc7f2e6d](https://help.ubuntu.com/community/RadeonDriver#head-a0bf0ca17168200ea3dd810ae505419bdc7f2e6d)

> 
**Removing the proprietary fglrx driver:**

fglrx is the name of the official, proprietary, Radeon driver from ATI. It conflicts with the open source "radeon" driver. If the "fglrx" kernel module is loaded at boot, X will be able to start using the "radeon" driver but "Direct Rendering" (DRI) will be disabled. This results in a severe performance reduction. If you previously used the proprietary "fglrx" driver it is highly recommended to unload the "fglrx" module if you wish to use the open source "radeon" driver. This can be done with:

```
sudo modprobe -r fglrx
```

To prevent the loading of this module at boot, you may blacklist it.

The libGL.so in /usr/lib might also still be the version installed by xorg-driver-fglrx. You can check that very easily, just run:

```
glxinfo |grep vendor
```

If you see: client glx vendor string: ATI, then the libGL.so is still from ATI. Just remove the xorg-driver-fglrx package and make sure libgl1-mesa-glx and libgl1-mesa-dri are installed:

```
sudo apt-get remove xorg-driver-fglrx
```
```
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```


After this I edited my xorg.conf so the radeon driver was loaded.

```
nano /etc/X11/xorg.conf
```

look for a section looking like this:

```
Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility U1"
        Driver          "radeon"
        BusID           "PCI:1:5:0"
        Option          "UseFBDev"              "true"
```


Make sure Driver is set to radeon (ati may also work, but with some crashes)

now reboot and try:

```
glxinfo | grep direct
```

it should say:

```
direct rendering= Yes
```



If something may go wrong you can always change Driver back to vesa. This will always work.
(eventually by rebooting in recovery mode... grub-escape-recovery mode- sudo nano /etc/X11/xorg.conf)

---

### Post by Stickee on 2007-04-25
Thanks, I now have direct rendering enabled:

```

mike@emachines-m5310:~$ glxinfo | grep direct
direct rendering: Yes

```

Now to get beryl going...

**edit**: Can't thank you enough, I've got avant-window-navigator now running and will try beryl tonight... :D :D :D

---

### Post by lylepratt on 2007-10-29
I was able to get this working following the advice of the various posts of this forum. At first, I was only getting ~240 FPS in glxgears. However, after adding the .drirc parameters in my /home directory, my FPS jumped to ~600. This SHOULD be enough to run beryl. 

I'll try tonight and post the results.

---

### Post by jetpeach on 2007-10-29
Running Gutsy 7.10 on a Compaq Presario 2100 with mobility U1. Adding the IRQpoll to the grub boot menu and using the radeon driver also worked for me, though my results only give around 500fps and the occational flicker. There were still some errors when I booted, something about "too much for IRQ3" or something, but I'm happy enough since this is an old laptop and has also been through many upgrades...

---

### Post by moshuptrail on 2008-01-08
Laptop: HP pavilion ze4125 (amd k7)
Video: Radeon 320M (RS200 IGP)
Gutsy
Driver: ati

After upgrading to Gutsy (7.10) my video got real slow and I realized the driver had been changed from vesa to ati.  So I started looking into the changes, which include a new ati driver, released after the last posting above.

To get it working I followed the instructions here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Then, I fooled with the xorg.conf a bit (did a LOT of reading) and that was it!  
I've uploaded my xorg.conf.   It's pretty minimalist.  That is, I only added things that were absolutely needed, although there may be some stuff I could have taken out.

A few notes.
If you are trying this and find that glxinfo is reporting Direct Rendering = No, make sure it's using the right display.  Mine was defaulting to :2, but when I explicitly named :0 in the command (glxinfo -display :0) it reported correctly.  

The same thing applies for glxgears.  It defaults to the wrong display and then crashes X.  Why?  But the command glxgears -display :0 works great.

Now, with this ancient laptop I'm only getting about 230-250 fps.  But it used to be 30!

> Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "RenderAccel"   "true"
        Option          "XAANoOffscreenPixmaps"
        Option          "DRI"   "on"
        Option          "mtrr"  "on"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
#               Virtual         1528 1024
        EndSubSection
EndSection

Section "ServerLayout"
        Option "AIGLX"  "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite"      "Enable"
EndSection


---

### Post by Noiano on 2008-04-27
Hello everybody,
I know this is not the proper tread to as about IGMP 320M and a projector but I though it was unuseful to open a new thread.
I have radeon IGP 320M on compaq evo n1015v and I cannot have a projector working on GDM. It only works on the console. When I try to switch to tty7 (the gdm one) the projector gets no signal. Xrandr says the projector is connected but it gets no signal. Any ideas?

---

### Post by michalpelszyk on 2008-07-13
> **moshuptrail said:**
> Now, with this ancient laptop I'm only getting about 230-250 fps.  But it used to be 30!
Try the ~/.drirc trick. I was surprised by the difference! ([http://ubuntuforums.org/showpost.php?p=2138073&postcount=22](http://ubuntuforums.org/showpost.php?p=2138073&postcount=22))
Thanks, marranzano!

---

