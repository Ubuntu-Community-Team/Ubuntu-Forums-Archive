---
title: "How can I install SiS 630 3d video hardware drivers?"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by ropers on 2006-09-21
Hi, 
First, a disclaimer: 
I am a *complete* Linux n00b and this is my first post here.
I've used DOS, Windows, Mac OS, Mac OS X, [OpenBSD]("http://www.openbsd.org/") (which I especially love) and to some extent even older Atari/Amiga/C64 operating systems. I claim to know a little bit about computers and operating systems, but I have no past Linux experience whatsoever. Except for booting Knoppix here and there, and doing several test installations of various distros, Ubuntu is the first Linux distro I have installed and actually used. Consequentially, I may sound and/or be **very** clueless here. While I have some UNIX knowledge (see OpenBSD above), it is very likely that there are A LOT of Linux basics that I just don't know. 
</disclaimer>

I have a PC that's basically built from scrappage. The mainboard is a SiS 630 mini ATX Socket 370 board with a 1000 MHz PIII and onboard VGA/LAN/Sound. I am running a default desktop Dapper Drake 6.01 LTS install.
After installing the Google Earth Linux beta ([http://earth.google.com/](http://earth.google.com/)) and seeing it be very slow and having it crash Ubuntu a few times, I determined that I need to install OpenGL support. This is from the Google Earth readme: > Google Earth can be run with "Mesa" (all software-rendered OpenGL), but the experience is sub-optimal. If you have 3D-accelerated video hardware, please install its drivers. Many distributions do not correctly install 3D drivers for even popular, mainstream hardware. If this is the first 3D application you've tried and it's very slow, it's likely that you don't have drivers installed at all. Please refer to your GNU/Linux distribution vendor for information on getting your video card drivers correctly installed.

**First question**: How do I find out whether OpenGL support is enabled or not? 
I did the below acting on the assumption that it isn't.

The motherboard "documentation" I have consists of this URL: [http://tinyurl.com/kn6mp](http://tinyurl.com/kn6mp)
I have downloaded the 786LCD-5.25 Linux driver there and found that it essentially contains a sis_drv.o file.

However this page: 
[http://www.winischhofer.at/linuxsispart4.shtml](http://www.winischhofer.at/linuxsispart4.shtml)
told me that I needed to install a sis_drv.so, because I'm running X.org's X11 rather than the XFree86 one.

Again, this is a default Dapper Drake install, but anyway: here is the precise X.org version I am running:

```
me@mycomputer:~$ X -version

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux mycomputer 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
```

My (default) Linux kernel was compiled with gcc version 4.0.3:

```
me@mycomputer:~$ cat /proc/version
Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
```

I do not currently have gcc installed, but I am aware that I could install it via: ```
sudo apt-get install build-essential
```
**Do I need to** install it for things to work here?

I confirmed that I do indeed have a SiS 630 (which is what it also says on the chip -- d'oh!):
```
me@mycomputer:~$ lspci -v | head
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 10)
        Flags: bus master, medium devsel, latency 32
        Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
        Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
        Flags: bus master, fast devsel, latency 16, IRQ 14
        I/O ports at <ignored>
        I/O ports at <ignored>
```

I then duly downloaded and extracted the "**X.org 6.9.0 (gcc 4.x; should work for 7.0 as well)**" sis_drv.so from [http://www.winischhofer.at/linuxsispart4.shtml](http://www.winischhofer.at/linuxsispart4.shtml). 

I backed up the old sis_drv.so and installed the one I downloaded like so:
```
sudo mv /usr/lib/xorg/modules/drivers/sis_drv.so /usr/lib/xorg/modules/drivers/sis_drv.so.orig
sudo cp -p sis_drv.so /usr/lib/xorg/modules/drivers/sis_drv.so
```
(instructions from [http://www.lemis.com/grog/HOWTO/mythtv-setup.html](http://www.lemis.com/grog/HOWTO/mythtv-setup.html))
NB: It's better to close all programs, log out and press Ctrl-Alt-F1 and log in at the text mode prompt to do this. Doing this from a regular shell will kill the X11 server without warning.

I rebooted and retried Google Earth -- it still is very slow/crashes, so I'm assuming that things didn't work and that hardware OpenGL support is still disabled. 
I am totally stumped.
**Can anyone suggest what I could do to get OpenGL support to work?**

Please let me know if I should provide more details.
Any help with this one is VERY welcome. :)

--ropers

---

### Post by ropers on 2006-09-21
I should add that the forum at [http://www.winischhofer.at/sisforum/](http://www.winischhofer.at/sisforum/) is currently unavailable, which is why I am posting here. 
--ropers

---

### Post by ropers on 2006-09-21
After finding out some more info, I've now done:

```
me@mycomputer:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-DRI)
  Minor opcode of failed request:  5 ()
  Value in failed request:  0x4b
  Serial number of failed request:  23
  Current serial number in output stream:  23
```
and 
```
me@mycomputer:~$ grep -i video /etc/group
video:x:44:ropers
```

Presumably the glxinfo results mean that OpenGL support is horribly broken for me. Does anyone have any ideas on how to fix it?

---

### Post by ropers on 2006-09-21
More progress, limited success:

I have found the X11 log files:

```
me@mycomputer:/var/log$ ll /var/log/Xorg.*
-rw-r--r-- 1 root root 33888 2006-09-21 19:21 /var/log/Xorg.0.log
-rw-r--r-- 1 root root 34217 2006-09-21 19:19 /var/log/Xorg.0.log.old
```

I've also found this page: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
So just to verify that none of this applied to my SiS 630 integrated graphics hardware I did:
```
me@mycomputer:~$ lspci | grep -i matrox
me@mycomputer:~$ lspci | grep -i nvidia
me@mycomputer:~$ lspci | grep -i ati
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 10)
```
The last output is misleading: The word "compatible" contains the string "ati" -- that obviously doesn't mean that my SiS 630 was ATI compatible.

The interesting thing is that [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
doesn't contain any SiS instructions. So if we can get this SiS 630 to work then we could add what we did to the BinaryDriverHowto for the benefit of future users. I hear SiS 630 was not uncommon with laptops. So please help this effort! Join me in this quest and improve the reach of Ubuntu!

---

### Post by ropers on 2006-09-21
I just looked inside the X11 log file:
```
me@mycomputer:~$ vi /var/log/Xorg.0.log
```NB: If you're new to vi and stuck, just press [ESC]:q![ENTER] to quit. 

I searched for SiS a couple of times in vi (I entered /SiS[ENTER], /[ENTER], /[ENTER], /[ENTER]). That's how I found this:
```
(II) SIS(0): SiS driver (2005/12/09-1, compiled for X.org 6.8.99.901)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See http://www.winischhofer.at/linuxsisvga.shtml
(II) SIS(0): *** for documentation, updates and a Premium Version.
(WW) SIS(0): This driver binary is not compiled for this version of X.org
(II) SIS(0): RandR rotation support not available in this version.
(II) SIS(0): Dynamic modelist support not available in this version.
(II) SIS(0): Screen growing support not available in this version.
(II) SIS(0): Advanced Xv video blitter not available in this version.
(II) SIS(0): Advanced MergedFB support not available in this version.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xD000
```

We can probably ignore the (WW) warning; the driver is the most recent one and the author anticipates it to work with X.org's X11 version 7.0 (cf. [http://www.winischhofer.at/linuxsispart4.shtml](http://www.winischhofer.at/linuxsispart4.shtml))

NB:```
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
```

However, the sisfb not found might be a clue. Maybe the instructions on [http://www.winischhofer.at/linuxsispart4.shtml](http://www.winischhofer.at/linuxsispart4.shtml) were not complete or I didn't read them right.

I didn't however pursue that lead further at this time. Instead, I installed the compiler/build tools, by going to Applications -- Add/Remove... -- Advanced -- Search "build-essentials". That seemed to fix OpenGL somehow. That, or the fact that I also dropped down to a text based command prompt via Ctrl-Alt-F1 and killed gdm and X (ps ax|more, kill -KILL <taskid-number>) and then once again copied sis_drv.so to the right place.```
cd <whereever-sis_drv.so-was-extracted>
sudo cp -p sis_drv.so /usr/lib/xorg/modules/drivers/
```I restarted after that, and now glxinfo says (emphasis added):```
me@mycomputer:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Eric Anholt
OpenGL renderer string: Mesa DRI SiS 20051019 AGP 1x
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_transpose_matrix,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_polygon_offset,
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_OES_read_format, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```

However, Google Earth still crashes Ubuntu, even when launched (as per the Google Earth README-linux) like thus:```
me@mycomputer:~$ cd google-earth
me@mycomputer:~/google-earth$ export LD_ASSUME_KERNEL=2.4.10
me@mycomputer:~/google-earth$ ./googleearth

```

This might be a Google Earth beta problem and might be related to the fact that my 1000MHz PIII is not the fastest box by today's standards. If Google Earth was at all faster after launching it with OpenGL enabled, then I found it not very noticable. Also, to be fair, Google Earth never  crashes the PC immediately, only when it's zooming in upon loading a location. To test whether OpenGL was really working now, I installed the (unsupported) game Chromium, which is known to be horribly slow with OpenGL disabled (I know this from past Knoppix exposure) and will only work properly if OpenGL support is enabled. It was unplayable and that proved to me that OpenGL support was not working properly. 

So I ask again: Any ideas? Anyone?

---

### Post by ropers on 2006-09-21
I just went back to follow the sisfb lead. I found that I don't need sisfb, because I'm running Linux 2.6.15. From *man sis*:```
3. 300 series specific information

       DRI  is  supported  on  the  300 series only. On Linux, prior to kernel
       2.6.3, DRI requires the kernel’s SiS framebuffer driver ( sisfb ).  The
       SiS DRM kernel driver as well as the SiS DRI client driver are required
       in any case.
```Interesting. From what I understand, the sis_drv.so I installed earlier is either the SiS DRM kernel driver or the SiS DRI client driver. Only which is it?

I found [http://www.winischhofer.net/sisdri.shtml](http://www.winischhofer.net/sisdri.shtml) (which was kinda hidden between winischhofer.net, winischhofer.at and winischhofer.eu and a link to it was wrong). It explains these things. The DRI (Direct Rendering Infrastructure) driver is sis_dri.so, the DRM (Direct Rendering Manager) driver is sis.ko, the X11 driver is sis_drv.so (formerly sis_drv.o).

I have the DRI driver:
```
me@mycomputer:~$ sudo find / -name sis_dri.so 
Password:
/usr/lib/dri/sis_dri.so
```

I also have the DRM driver:
```
me@mycomputer:~$ sudo find / -name sis.ko
/lib/modules/2.6.15-26-386/kernel/drivers/char/drm/sis.ko
/lib/modules/2.6.15-27-386/kernel/drivers/char/drm/sis.ko
me@mycomputer:~$ sudo find / -name sis.o
me@mycomputer:~$

```

We already talked about and installed the X11 driver above.

As per the instructions (Variant 3) on [http://www.winischhofer.net/sisdri.shtml](http://www.winischhofer.net/sisdri.shtml), I edited /etc/X11/xorg.conf (it's xorg.conf, not Xorg.conf unlike the webpage would make you believe), searched for /Section "Device" and added: 
```
Option "MaxXFBMem" "12288" # added by me according to http://www.winischhofer.net/sisdri.shtml
```
(I like to add comments when I'm editing such stuff, so it can be seen later that things were changed from the default. Everything after # is a comment and thus ignored.)
I then rebooted, but things still don't work. I see now that glxinfo actually tells me that we're still using MESA (ie. non-hardware accelerated OpenGL) -- cf. the above glxinfo output.

Close, but no cigar. 

To revisite the Variant 3 section on [http://www.winischhofer.net/sisdri.shtml:](http://www.winischhofer.net/sisdri.shtml:)
- I am running Linux 2.6.15.
- I have configured 64MB of shared memory as video RAM in the BIOS. 
- I am not using sisfb.
- I have sis_drv.so (previously sis_drv.o) installed and have the MaxXFBMem option set.
- I do not however understand the below parts of what it says there:
> * Enable SiS DRM support in the kernel configuration. Choose the SiS DRM to be compiled as a module (not statically into the kernel). The module will be loaded automatically, no need to modprobe it.
* Enable AGP support in your kernel configuration (not for PCI versions of SIS 300/305 cards). It is recommended to compile AGP statically into the kernel. Note: The AGP driver to use depends on what host chipset you have. On SiS 630/730 and assumingly 540, this is "SiS generic". If you use a SiS 300/305 (AGP) in a non-SiS mainboard, check the manufacturer of your AGP host controller.
* Recompile and install the kernel and the modules
Do I have to do that? 
How do I do that?
Where do I find my "kernel configuration"?

Any ideas, anyone?

---

### Post by ropers on 2006-09-21
Not sure if this info might help (I don't really know what lsmod is and its manpage is not very verbose):

```
me@mycomputer:/etc/X11$ lsmod
Module                  Size  Used by
nls_cp437               5888  1
isofs                  37688  1
udf                    88580  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
sis                    10304  1
drm                    73236  2 sis
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
af_packet              22920  0
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
tsdev                   8000  0
floppy                 62148  0
pcspkr                  2180  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_mpu401              6728  1
analog                 12320  0
psmouse                36100  0
sis_agp                 8708  1
agpgart                34888  2 drm,sis_agp
rtc                    13492  0
serio_raw               7300  0
snd_trident            44196  2
gameport               15496  3 analog,snd_trident
snd_ac97_codec         93216  1 snd_trident
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  3 snd_pcm_oss
snd_pcm                89864  3 snd_trident,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_page_alloc         10632  2 snd_trident,snd_pcm
snd_util_mem            4608  1 snd_trident
snd_mpu401_uart         7808  2 snd_mpu401,snd_trident
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_trident,snd_rawmidi
snd                    55268  12 snd_mpu401,snd_trident,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
sis900                 22912  0
i2c_sis630              7948  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
soundcore              10208  3 snd
mii                     5888  1 sis900
i2c_core               21904  2 i2c_acpi_ec,i2c_sis630
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci_hcd               21892  0
usbcore               130820  2 ohci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  4
sis5513                17032  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
```

It says here ([http://www.linuxquestions.org/questions/showthread.php?t=323729](http://www.linuxquestions.org/questions/showthread.php?t=323729)) that ```
Section "dri"
    Mode 0666
EndSection
``` should possibly be in my xorg.conf (though I'm not having the issue described there). **Should I add that?**
Does anybody know if that would help?

After reading this ([http://www.winischhofer.eu/sisforum/viewtopic.php?t=94&sid=c0468ae9d7aa8369729fdf778b552909](http://www.winischhofer.eu/sisforum/viewtopic.php?t=94&sid=c0468ae9d7aa8369729fdf778b552909)) I downloaded [http://dri.freedesktop.org/snapshots/sis-20060403-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/sis-20060403-linux.i386.tar.bz2) from [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/). That archive contains an install script. **Should I try running that?** Does anyone know?

I have installed SiSCtrl as per the **4. SiSCtrl (SiS/XGI Display Control Panel)** instructions on [http://www.winischhofer.eu/linuxsispart4.shtml](http://www.winischhofer.eu/linuxsispart4.shtml). I added ```
Option "EnableSiSCtrl" "yes" 
``` under Section "Device" in /etc/X11/xorg.conf as prompted by the app after installing (baby steps: 1. added repositories to sources.list 2. installed sisctrl via System -- Administration -- Synaptic Package Manager 3. launched Applications -- SisCtrl and was prompted to add said option, which I did. 4. Restarted). SisCtrl now works, as does the ```
me@mycomputer:~$ glxgears
``` demo. But glxinfo is telling me that OpenGL is still running via MESA/software, not hardware enabled:```
OpenGL vendor string: Eric Anholt
OpenGL renderer string: Mesa DRI SiS 20051019 AGP 1x
OpenGL version string: 1.2 Mesa 6.4.1
```

**What am I missing?**

---

### Post by ropers on 2006-09-21
Here is my dmesg, in case it helps:

```
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000fff3000 - 0000000010000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65520
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 AWARD                                 ) @ 0x000f6120
[17179569.184000] ACPI: RSDT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3000
[17179569.184000] ACPI: FADT (v001 AWARD  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3040
[17179569.184000] ACPI: DSDT (v001 AWARD  AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x5008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 996.931 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.248000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.252000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.288000] Memory: 249140k/262080k available (1976k kernel code, 12356k reserved, 606k data, 288k init, 0k highmem)
[17179569.288000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.368000] Calibrating delay using timer specific routine.. 1994.73 BogoMIPS (lpj=3989463)
[17179569.368000] Security Framework v1.0.0 initialized
[17179569.368000] SELinux:  Disabled at boot.
[17179569.368000] Mount-cache hash table entries: 512
[17179569.368000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.368000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.368000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179569.368000] CPU: L2 cache: 256K
[17179569.368000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.368000] mtrr: v2.0 (20020519)
[17179569.368000] CPU: Intel Pentium III (Coppermine) stepping 0a
[17179569.368000] Enabling fast FPU save and restore... done.
[17179569.368000] Enabling unmasked SIMD FPU exception support... done.
[17179569.368000] Checking 'hlt' instruction... OK.
[17179569.384000] checking if image is initramfs... it is
[17179571.012000] Freeing initrd memory: 6617k freed
[17179571.076000] ACPI: Looking for DSDT ... not found!
[17179571.076000] ACPI: setting ELCR to 0200 (from 0a28)
[17179571.084000] NET: Registered protocol family 16
[17179571.084000] EISA bus registered
[17179571.084000] ACPI: bus type pci registered
[17179571.100000] PCI: PCI BIOS revision 2.10 entry at 0xfb2f0, last bus=1
[17179571.100000] PCI: Using configuration type 1
[17179571.100000] ACPI: Subsystem revision 20051216
[17179571.112000] ACPI: Interpreter enabled
[17179571.112000] ACPI: Using PIC for interrupt routing
[17179571.112000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.112000] PCI: Probing PCI hardware (bus 00)
[17179571.112000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.116000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:00.1
[17179571.116000] Uncovering SIS18 that hid as a SIS503 (compatible=0)
[17179571.116000] Enabling SiS 96x SMBus.
[17179571.116000] Boot video device is 0000:01:00.0
[17179571.116000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.140000] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 10 11 12 14 15)
[17179571.140000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179571.140000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179571.140000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[17179571.144000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.144000] pnp: PnP ACPI init
[17179571.152000] pnp: PnP ACPI: found 13 devices
[17179571.152000] PnPBIOS: Disabled by ACPI PNP
[17179571.152000] PCI: Using ACPI for IRQ routing
[17179571.152000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.208000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[17179571.208000] PCI: Bridge: 0000:00:02.0
[17179571.208000]   IO window: d000-dfff
[17179571.208000]   MEM window: e1000000-e10fffff
[17179571.208000]   PREFETCH window: d8000000-dfffffff
[17179571.208000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179571.208000] audit: initializing netlink socket (disabled)
[17179571.208000] audit(1158889956.208:1): initialized
[17179571.208000] VFS: Disk quotas dquot_6.5.1
[17179571.208000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.208000] Initializing Cryptographic API
[17179571.208000] io scheduler noop registered
[17179571.208000] io scheduler anticipatory registered
[17179571.208000] io scheduler deadline registered
[17179571.208000] io scheduler cfq registered
[17179571.208000] isapnp: Scanning for PnP cards...
[17179571.564000] isapnp: No Plug & Play device found
[17179571.604000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.604000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.604000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.604000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.604000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.612000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.616000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.616000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.616000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.616000] mice: PS/2 mouse device common for all mice
[17179571.616000] EISA: Probing bus 0 at eisa.0
[17179571.616000] Cannot allocate resource for EISA slot 4
[17179571.616000] Cannot allocate resource for EISA slot 5
[17179571.616000] EISA: Detected 0 cards.
[17179571.616000] NET: Registered protocol family 2
[17179571.644000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.656000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.656000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.656000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.656000] TCP: Hash tables configured (established 16384 bind 16384)
[17179571.656000] TCP reno registered
[17179571.656000] TCP bic registered
[17179571.656000] NET: Registered protocol family 1
[17179571.656000] NET: Registered protocol family 8
[17179571.656000] NET: Registered protocol family 20
[17179571.656000] Using IPI Shortcut mode
[17179571.656000] ACPI wakeup devices:
[17179571.656000] PWRB PCI0 USB0 USB1 MAC0 AUD0 UAR1 ECP1
[17179571.656000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.656000] Freeing unused kernel memory: 288k freed
[17179571.784000] vga16fb: initializing
[17179571.784000] vga16fb: mapped to 0xc00a0000
[17179571.860000] Console: switching to colour frame buffer device 80x25
[17179571.860000] fb0: VGA16 VGA frame buffer device
[17179572.948000] Capability LSM initialized
[17179573.020000] ACPI: Fan [FAN] (on)
[17179573.032000] ACPI: Thermal Zone [THRM] (48 C)
[17179574.344000] SIS5513: IDE controller at PCI slot 0000:00:00.1
[17179574.344000] ACPI: PCI Interrupt 0000:00:00.1[A]: no GSI - using IRQ 14
[17179574.344000] PCI: setting IRQ 14 as level-triggered
[17179574.344000] SIS5513: chipset revision 208
[17179574.344000] SIS5513: not 100% native mode: will probe irqs later
[17179574.344000] SIS5513: SiS630 ATA 66 controller
[17179574.344000]     ide0: BM-DMA at 0x4000-0x4007, BIOS settings: hda:DMA, hdb:DMA
[17179574.344000]     ide1: BM-DMA at 0x4008-0x400f, BIOS settings: hdc:DMA, hdd:DMA
[17179574.344000] Probing IDE interface ide0...
[17179574.632000] hda: IC35L020AVER07-0, ATA DISK drive
[17179575.080000] hdb: Pioneer DVD-ROM ATAPIModel DVD-116 0122, ATAPI CD/DVD-ROM drive
[17179575.136000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.136000] Probing IDE interface ide1...
[17179575.424000] hdc: QUANTUM FIREBALL ST2.1A, ATA DISK drive
[17179575.704000] hdd: ST38641A, ATA DISK drive
[17179575.760000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.776000] hda: max request size: 128KiB
[17179575.796000] hda: 39102336 sectors (20020 MB) w/1916KiB Cache, CHS=38792/16/63, UDMA(33)
[17179575.796000] hda: cache flushes not supported
[17179575.796000]  hda: hda1 hda2 < hda5 >
[17179575.836000] hdc: max request size: 128KiB
[17179575.836000] hdc: 4124736 sectors (2111 MB) w/81KiB Cache, CHS=4092/16/63, UDMA(33)
[17179575.836000] hdc: cache flushes not supported
[17179575.836000]  hdc:<6>hdb: ATAPI 126X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179575.836000] Uniform CD-ROM driver Revision: 3.20
[17179575.844000]  hdc1
[17179575.844000] hdd: max request size: 128KiB
[17179575.844000] hdd: 16809660 sectors (8606 MB) w/128KiB Cache, CHS=16676/16/63, UDMA(33)
[17179575.844000] hdd: cache flushes not supported
[17179575.844000]  hdd:
[17179576.392000] usbcore: registered new driver usbfs
[17179576.392000] usbcore: registered new driver hub
[17179576.420000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.420000] **** SET: Misaligned resource pointer: cfbddf02 Type 07 Len 0
[17179576.420000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179576.420000] PCI: setting IRQ 11 as level-triggered
[17179576.420000] ACPI: PCI Interrupt 0000:00:01.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.420000] ohci_hcd 0000:00:01.2: OHCI Host Controller
[17179576.424000] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[17179576.424000] ohci_hcd 0000:00:01.2: irq 11, io mem 0xe1103000
[17179576.480000] hub 1-0:1.0: USB hub found
[17179576.480000] hub 1-0:1.0: 3 ports detected
[17179576.584000] ACPI: PCI Interrupt 0000:00:01.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.584000] ohci_hcd 0000:00:01.3: OHCI Host Controller
[17179576.584000] ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
[17179576.584000] ohci_hcd 0000:00:01.3: irq 11, io mem 0xe1100000
[17179576.640000] hub 2-0:1.0: USB hub found
[17179576.640000] hub 2-0:1.0: 2 ports detected
[17179576.896000] Attempting manual resume
[17179576.964000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.000000] kjournald starting.  Commit interval 5 seconds
[17179593.300000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.304000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.620000] **** SET: Misaligned resource pointer: cd30db22 Type 07 Len 0
[17179593.620000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179593.620000] PCI: setting IRQ 5 as level-triggered
[17179593.620000] ACPI: PCI Interrupt 0000:00:01.4[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179594.068000] input: PC Speaker as /class/input/input1
[17179594.112000] Real Time Clock Driver v1.12
[17179594.124000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.128000] agpgart: Detected SiS 630 chipset
[17179594.136000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179594.144000] sis900.c: v1.08.09 Sep. 19 2005
[17179594.144000] **** SET: Misaligned resource pointer: cd30d222 Type 07 Len 0
[17179594.144000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179594.144000] ACPI: PCI Interrupt 0000:00:01.1[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179594.144000] 0000:00:01.1: SiS 900 Internal MII PHY transceiver found at address 1.
[17179594.152000] 0000:00:01.1: Using transceiver found at address 1 as default
[17179594.164000] Floppy drive(s): fd0 is 1.44M
[17179594.184000] FDC 0 is a post-1991 82077
[17179594.228000] parport: PnPBIOS parport detected.
[17179594.228000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179595.300000] MC'97 1 converters and GPIO not ready (0x1)
[17179595.316000] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2593kHz
[17179595.340000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179596.260000] ts: Compaq touchscreen protocol output
[17179596.320000] ac97 codec read TIMEOUT [0x54/0x1c0d4]!!!
[17179596.348000] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 11, 00:10:c6:02:ce:67.
[17179597.024000] lp0: using parport0 (interrupt-driven).
[17179597.160000] Adding 835340k swap on /dev/hda5.  Priority:-1 extents:1 across:835340k
[17179597.284000] EXT3 FS on hda1, internal journal
[17179597.632000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179597.632000] md: bitmap version 4.39
[17179598.524000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179598.664000] eth0: Media Link On 100mbps full-duplex
[17179599.076000] NET: Registered protocol family 10
[17179599.076000] lo: Disabled Privacy Extensions
[17179599.076000] IPv6 over IPv4 tunneling driver
[17179602.488000] NET: Registered protocol family 17
[17179607.984000] ACPI: Power Button (FF) [PWRF]
[17179607.984000] ACPI: Power Button (CM) [PWRB]
[17179608.224000] ibm_acpi: ec object not found
[17179608.280000] pcc_acpi: loading...
[17179609.704000] eth0: no IPv6 routers present
[17179613.408000] [drm] Initialized drm 1.0.1 20051102
[17179613.456000] **** SET: Misaligned resource pointer: caf863a2 Type 07 Len 0
[17179613.456000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[17179613.460000] PCI: setting IRQ 3 as level-triggered
[17179613.460000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[17179613.460000] [drm] Initialized sis 1.1.0 20030826 on minor 0
[17179613.464000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179613.464000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179613.464000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179616.316000] ppdev: user-space parallel port driver
[17179616.828000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179616.832000] apm: overridden by ACPI.
[17179624.356000] Bluetooth: Core ver 2.8
[17179624.356000] NET: Registered protocol family 31
[17179624.356000] Bluetooth: HCI device and connection manager initialized
[17179624.356000] Bluetooth: HCI socket layer initialized
[17179624.472000] Bluetooth: L2CAP ver 2.8
[17179624.472000] Bluetooth: L2CAP socket layer initialized
[17179624.484000] Bluetooth: RFCOMM socket layer initialized
[17179624.484000] Bluetooth: RFCOMM TTY layer initialized
[17179624.484000] Bluetooth: RFCOMM ver 1.7
[17179648.692000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179648.792000] ISOFS: changing to secondary root
```

The ****** SET: Misaligned resource pointer:** error messages do seem to indicate some kind of problem. As to what they really say, I don't have the slightest clue. (Any ideas anyone?)

---

### Post by ropers on 2006-09-22
I installed driconf via the Synaptic Package Manager (cf. [http://dri.freedesktop.org/wiki/DriConf)](http://dri.freedesktop.org/wiki/DriConf)). Now I can launch driconf by typing driconf at the Terminal prompt. That application however doesn't seem to get me any closer to getting HW accelerated OpenGL to run.

---

### Post by ropers on 2006-09-22
Upon reading [http://www.winischhofer.eu/linuxsispart2.shtml](http://www.winischhofer.eu/linuxsispart2.shtml) I added 
```
Option "AGPSize" "32"
``` into the Device section in /etc/X11/xorg.conf and rebooted. This also didn't help.

---

### Post by ropers on 2006-09-22
I added 
```
Load    "GLcore" #added-cf. www.winischhofer.net/sis/XF86Config-4.simple
```to /etc/X11/xorg.conf as per [http://www.winischhofer.net/sis/XF86Config-4.simple](http://www.winischhofer.net/sis/XF86Config-4.simple). No joy.

---

### Post by ropers on 2006-09-22
as per the above, I also added:```

        Load    "dbe" #same as above
        Load    "record" #as above
        Load    "speedo" #as above

```

It's *still* not playing ball though.

---

### Post by dannyboy79 on 2006-09-22
I hate to tell you that on board graphics aren't open gl supported. I ended up going out and buying a GeForce 6200 for 29.99 after rebate and I am super happy with it, none of my dvd's skip anymore. It's awesome. I am a newbie so I can't help I can only tell you that I tried to follow instructions from [www.winischhofer.net](www.winischhofer.net) but I couldnt get it to work! Sorry man and good luck

---

### Post by laurentgo on 2006-09-22
Hi,

In fact you had 3D support from the beginning like glxinfo told you with direct rendering:Yes

With my SiS 650 (which has no 3D support) I have the following lines.

```

direct rendering:No
...
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

It is explicitly written that Mesa provides indirect rendering. In your case, Mesa provides a 3D driver for your graphic card. Your poor performances with Google Earth are caused by the poor performance of your SiS 630 3D engine.

By the way, last driver from Thomas is from 2005 so the driver included with Ubuntu is more recent. No need to replace it.

---

### Post by ropers on 2006-09-22
Dannyboy79, laurentgo: many thanks for your replies. :)

I'm not sure if I understand you correctly. My (possibly false) understanding was that Mesa was essentially a software OpenGL implementation so owners of non-OpenGL capable hardware can run --albeit slowly-- software that requires OpenGL. That's also how I understand [http://en.wikipedia.org/wiki/Mesa_3D](http://en.wikipedia.org/wiki/Mesa_3D). 

My current goal thus was (still is) to somehow enable proper hardware accelerated OpenGL and thus get rid of Mesa. I was under the impression that my SiS 630 was fundamentally (non-Mesa) OpenGL capable. Do you think that it isn't? Are you really, truly, positively certain of that? Or am I not understanding you correctly?

Cheers, ropers

---

### Post by laurentgo on 2006-09-22
I'm almost positive that you have hardware accelerated 3D.
One of the purpose to Mesa is to provide an OpenGL engine for non-accelerated chipsets but it also acts as the core for open-source drivers: drivers implements low-level commands, Mesa implements the upper parts.

It is hinted into Mesa's faq: [http://www.mesa3d.org/faq.html](http://www.mesa3d.org/faq.html) and also from the wikipedia article:
```

Whilst Mesa 3D supports several hardware graphics accelerators, it may also be compiled as a software-only renderer. Since it is also Open Sourced, it is possible to use it to study the internal workings of an OpenGL-compatible renderer.

```

In my case, I only a software-only renderer. In your case, Mesa takes advantage of your hardware to provide a hardware renderer.

---

### Post by ropers on 2006-09-22
> **laurentgo said:**
> I'm almost positive that you have hardware accelerated 3D. (...)

If true, does anyone have any ideas how hardware "accelerated" 3D could end up being totally dog slow? And when I say "slow" I don't mean "low framerate", I mean "slideshow". It's not just the admittedly beta Google Earth program. The Chromium game for instance is a hideously bad joke.

---

### Post by grizzly on 2006-09-28
I think I know why.. [http://www.opensubscriber.com/message/dri-devel@lists.sourceforge.net/3643455.html](http://www.opensubscriber.com/message/dri-devel@lists.sourceforge.net/3643455.html) 

its seems to be a bug in xserver-xorg and/or mesa

---

### Post by rhapsody2000 on 2007-01-28
:-k 
Any news my friend ?

i've also a Sis630 video card and it's  very  slow on ubunto.
It' s a shame because it's a well spread card around here.

Also my Linsys wifi card wasn't properly handled, so i've installed ndiswrapper and xp drivers. Now it's ok.

But wasn't it 15 years ago when an OS needed the drivers to be installed by hand ? hum linux haven't progress so much. :confused: 

but let's be positive, any one have a working Sis630 that isn't slow on Linux ?

thx

---

### Post by uways on 2007-01-30
i*m currently running debian testing and facing the same issues with the sis630 card. although all the configurations seem to say that the card*s hardware acceleration is enabled, running applications and games seem to tell an entirely different story. funny coz from windows all my games/3d-apps work fine.
the card doesn*t seem to work for glx/compiz/beryl.
been trying to solve the problem for a while now. i have yet to come across something that works.

---

### Post by ringmaster on 2007-02-02
> **rhapsody2000 said:**
> :-k 
Any news my friend ?

i've also a Sis630 video card and it's  very  slow on ubunto.
It' s a shame because it's a well spread card around here.

Also my Linsys wifi card wasn't properly handled, so i've installed ndiswrapper and xp drivers. Now it's ok.

But wasn't it 15 years ago when an OS needed the drivers to be installed by hand ? hum linux haven't progress so much. :confused: 

but let's be positive, any one have a working Sis630 that isn't slow on Linux ?

thx

Well... I have a sis630 and I CAN play games... (3C games) like pool 3D and even window's ones with wine (yes, 3D games but very simple ones in a window). My only problem is that with certain games/screensavers (open gl ones) at fullscreen the image is displaced half to the top, I will try linspire and edgy to see if this is solved... (excuse me; I'm spanish).
I have tried a lot of things too (Thomas is missing in action) without results.
There must be a problem with the driver (or opengl); e.g. sometimes with 3D apps. the computer freezes. I must admit that only 2D acceleration is superb with this card.

regards,
Ringmaster

---

### Post by TuxCrafter on 2007-03-10
Can someone tell me how to get a SiS 3D driver working on linux?
I have a SiS741CX chipset and if you got the SIS 630 working there is a big change it will work for me to. Please help!

---

### Post by TuxCrafter on 2007-03-10
> **ringmaster said:**
> Well... I have a sis630 and I CAN play games... (3C games) like pool 3D and even window's ones with wine (yes, 3D games but very simple ones in a window). My only problem is that with certain games/screensavers (open gl ones) at fullscreen the image is displaced half to the top, I will try linspire and edgy to see if this is solved... (excuse me; I'm spanish).
I have tried a lot of things too (Thomas is missing in action) without results.
There must be a problem with the driver (or opengl); e.g. sometimes with 3D apps. the computer freezes. I must admit that only 2D acceleration is superb with this card.

regards,
Ringmaster

can you run this command and paste the result?

glxinfo
glxgears -printfps

---

### Post by punong_bisyonaryo on 2007-04-10
> **TuxCrafter said:**
> Can someone tell me how to get a SiS 3D driver working on linux?
I have a SiS741CX chipset and if you got the SIS 630 working there is a big change it will work for me to. Please help!

Like Laurentgo, I also have a Sis 650. Based on this page [http://www.winischhofer.eu/linuxsispart1.shtml#21](http://www.winischhofer.eu/linuxsispart1.shtml#21), we owners of 650s and 741s, among others, are out of luck with 3D. I'm still waiting for any development, because it will still be some time before I can retire my laptop.

I was wondering if there was a way to reverse engineer the official Sis Drivers [http://www.sis.com/download](http://www.sis.com/download). It's for Redhat though, and I don't know if it has 3D support either.

---

### Post by TuxCrafter on 2007-04-10
I had a AMD geode system with SIS741CX chipset for testing. I could not get any 3D drivers for de SIS and the 2D drivers are buggy. The SIS741CX chipset is NOT Linux compatible you can find my report here:

[http://ubuntuforums.org/showthread.php?t=394589&highlight=SIS741CX](http://ubuntuforums.org/showthread.php?t=394589&highlight=SIS741CX)

If you get 3D working by some miracle please contact me and tell me how!

---

### Post by ringmaster on 2007-04-10
> **TuxCrafter said:**
> can you run this command and paste the result?

glxinfo
glxgears -printfps
Glxinfo:
```
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Eric Anholt
OpenGL renderer string: Mesa DRI SiS 20060710 AGP 1x
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_OES_read_format, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
```
glxgears -printfps does not run for me. But glxgears -info:
```
GL_RENDERER   = Mesa DRI SiS 20060710 AGP 1x
GL_VERSION    = 1.2 Mesa 6.5.1
GL_VENDOR     = Eric Anholt
GL_EXTENSIONS = GL_ARB_multisample GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_mirrored_repeat GL_ARB_transpose_matrix GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_APPLE_packed_pixels GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_OES_read_format GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod
562 frames in 5.0 seconds = 111.364 FPS
593 frames in 5.0 seconds = 118.571 FPS
551 frames in 5.0 seconds = 110.075 FPS
578 frames in 5.0 seconds = 115.557 FPS
587 frames in 5.0 seconds = 117.106 FPS

```
My kernel is an optimised one, with only drivers needed compiled in, but with default kernel I get similar results. And excuse me for being so late; I was not subscribed to this topic (my fault).

Ringmaster

---

### Post by az on 2007-04-10
> **ropers said:**
> If true, does anyone have any ideas how hardware "accelerated" 3D could end up being totally dog slow? And when I say "slow" I don't mean "low framerate", I mean "slideshow". It's not just the admittedly beta Google Earth program. The Chromium game for instance is a hideously bad joke.

The sis driver in Dapper already includes the patches winischhofer wrote, check the dates in the changelogs.  

The reality is that the sis chipset is not at all that powerful.  You have 3d acceleration working as well as it can - it just doesn't do much.  You can't make a miniature poodle pull a horse's carriage!

---

### Post by punong_bisyonaryo on 2007-04-10
> **laurentgo said:**
> With my SiS 650 (which has no 3D support) I have the following lines.

```

direct rendering:No
...
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Did you change anything in your xorg.conf? I have a Sis 650, too. But on the default Sis drivers that come with Edgy, I get

```
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17
```

---

### Post by N0Lif3 on 2007-04-13
I have a SOTEC 3000series laptop, using the SIS 630 driver, and I do not believe that 3d hardware acceleration is in effect. I hope this data will help in getting 3d hardware acceleration working.

results of "glxinfo"
```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4a
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Eric Anholt
OpenGL renderer string: Mesa DRI SiS 20060710 AGP 1x
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection,
    GL_OES_read_format, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 32  0 16 16 16 16  0 0 Slow
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x4a 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

results of "glxgears -printfps"
```
richard@n30lif3:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4a
930 frames in 5.0 seconds = 185.901 FPS
975 frames in 5.0 seconds = 194.950 FPS
980 frames in 5.0 seconds = 195.995 FPS
992 frames in 5.0 seconds = 198.328 FPS
1000 frames in 5.0 seconds = 199.994 FPS
1000 frames in 5.0 seconds = 199.851 FPS
1002 frames in 5.0 seconds = 200.325 FPS
998 frames in 5.0 seconds = 199.587 FPS
998 frames in 5.0 seconds = 199.426 FPS
990 frames in 5.0 seconds = 197.943 FPS
1002 frames in 5.0 seconds = 200.330 FPS
1080 frames in 5.0 seconds = 215.865 FPS
1071 frames in 5.0 seconds = 214.067 FPS
1079 frames in 5.0 seconds = 215.689 FPS
1083 frames in 5.0 seconds = 216.490 FPS
1067 frames in 5.0 seconds = 213.302 FPS
1086 frames in 5.0 seconds = 217.024 FPS
1073 frames in 5.0 seconds = 214.452 FPS
1088 frames in 5.0 seconds = 217.423 FPS
1089 frames in 5.0 seconds = 217.658 FPS
1088 frames in 5.0 seconds = 217.581 FPS
1120 frames in 5.0 seconds = 223.102 FPS
1152 frames in 5.0 seconds = 230.284 FPS
1624 frames in 5.0 seconds = 324.628 FPS
1646 frames in 5.0 seconds = 329.050 FPS
1387 frames in 5.0 seconds = 277.033 FPS
1392 frames in 5.0 seconds = 278.230 FPS
1606 frames in 5.0 seconds = 320.202 FPS
1642 frames in 5.0 seconds = 328.354 FPS
1421 frames in 5.0 seconds = 283.953 FPS
1246 frames in 5.0 seconds = 249.193 FPS
1184 frames in 5.0 seconds = 236.697 FPS
```
(I manually closed down the spinning-gears window to stop the process here)

---

### Post by punong_bisyonaryo on 2007-04-13
Well, whether or not you're 3d acceleration is in effect, at least yours doesn't spew out an error like mine. I can't even get useful information from my glxinfo. Any ideas?

---

