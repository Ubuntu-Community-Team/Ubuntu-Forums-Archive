---
title: "ati radeon 7000 driver for ubuntu studio"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by linucksrox on 2007-10-08
Hi all, I have tried using the guides to find the right driver or module for my ati radeon 7000 card. I'm running ubuntu studio, and all I want to do is get compiz fusion to work. It's installed, but it says it can't run under a vesa driver. I know the new fglrx driver isn't compatible with my old ati card, but I don't know where to find an older version that will work. Any ideas? Thanks.

---

### Post by overdrank on 2007-10-09
> **linucksrox said:**
> Hi all, I have tried using the guides to find the right driver or module for my ati radeon 7000 card. I'm running ubuntu studio, and all I want to do is get compiz fusion to work. It's installed, but it says it can't run under a vesa driver. I know the new fglrx driver isn't compatible with my old ati card, but I don't know where to find an older version that will work. Any ideas? Thanks.

Hi and this "how to" has helped me with a ATI 7500
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Hope this helps and good luck!

---

### Post by smacfarl on 2007-10-10
So I also have a radeon 7000.

Seems like OpenGL is not supported in the driver? 

What do I have to do to fix this? ATI is now very open source friendly. Can we expect they will get a driver out for this card? Will they at least release specs so that we could possibly try writing a driver. Who is an expert on this in the Ubuntu world?

---

### Post by smacfarl on 2007-10-10
** Gives the thread a nudge **

---

### Post by smacfarl on 2007-10-11
*** Gives the thread a nudge ***

---

### Post by nzadLithium on 2007-10-11
There was a guide posted above. did you follow it?

as long as you havent already installed the ati propriety drivers then I think all you really need to is change the device section in etc/X11/xorg.conf so the line saying driver looks like this
        Driver                "ati"

to edit it do sudo gedit /etc/X11/xorg.cong

---

### Post by smacfarl on 2007-10-13
So I already did the corg.conf change.

when I run glxinfo I get

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x5f 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Looks to me like the ati driver is not running opengl on my system. Now since I run the Radeon 7000, this is a different architecture than the 7500. Since ATI is now open source friendly is there any chance they will supply a working driver or specifications so that one can be written for this card?

---

### Post by nzadLithium on 2007-10-13
backup your xorg.conf then try changing your driver to radeon. Make sure you take a backup because on another thread they didnt have the radeon drivers. I dont know what version of ubuntu they were using so if you dont have them it will cause x to crash (on startup).

---

### Post by smacfarl on 2007-10-13
the install set up the radeon drivers. Didn't work. Changed to ati. Didn't work.

I think the problem is that this Radeon 7000 boards, chipset is not fully supported in the linux ati driver. So what I would like to do is see if I can get a hold of the group or people responsible for it to find out what has to be done and if I can help somehow, even if it's just testing.

I was hoping there was a point person in the Ubuntu community working on graphics driver issues that would be able to educate me more on this issue.

---

### Post by nzadLithium on 2007-10-13
try this:

[https://help.ubuntu.com/community/RadeonDriver#head-7e2283943de094f4c373154f2e8178bfa9374050](https://help.ubuntu.com/community/RadeonDriver#head-7e2283943de094f4c373154f2e8178bfa9374050)

The open source drivers for ati radeon 7000 cards have complete support(meaning they fully support opengl and 3d acceleration) so as long as you setup the driver properly there is no reason why it should not work.

---

### Post by smacfarl on 2007-10-13
So when I type

```
$lspci
```

I get

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] 
```

Which according to the Will it Work section indicates I should get full 3D support.

Next step

```
$ glxinfo |grep vendor
```

I get

```
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: www.mesa3d.org
```

which means I am using the proprietary driver somehow. Though I never installed it.

So I went to Synaptic package manager rather than using sudo to remove the xorg-driver-fglrx package. And I am now going to restart my window manager.

My question is how did I install this? I think it was installed during the install. Since my card is supported in full, the default ubuntu setup should automatically get this configuration correct, it didn't identifying the radeon driver as my default, and worse installing the fglrx driver that actually causes problems. How do I work with the people who do the install of ubuntu OS to make sure this doesn't happen to other people? Assuming everything works on re-login.

---

### Post by smacfarl on 2007-10-13
So bad news. It didn't work. So while

```
$ glxinfo | grep "vendor"
```

now yields

```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org
```

sadly 

```
$ glxinfo | grep "direct rendering"
```

yields

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

also attempting to set LIBGL_DEBUG="verbose", seems to have no effect on this.

```
$ LIBGL_DEBUG="verbose"
$ echo $LIBGL_DEBUG
verbose
$ glxinfo | grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

So what's the next thing to do?

---

### Post by nzadLithium on 2007-10-14
when you had this:

server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

you should have had full 3d accelleration. when you restarted it seems you lost it. go throught the instructions again and try to find out which one makes client glx vendor string: ATI 

also while you have client glx vendor string: SGI can you post the results of lsmod? It could be it loaded the wrong driver. which lsmod should tell us whether it is that or not.

---

### Post by smacfarl on 2007-10-14
"you should have had full 3d accelleration. when you restarted it seems you lost it."

I never had full 3d acceleration at any point. My initial configuration was ATI as the client. This did not work, this was your first recommendation change the xorg.conf from radeon to ATI.

The direct rendor was "no".

I was then told in this thread to follow a guide. The guide said to uninstall fglrx package entirely, which i did.

I already had the two mesa driver packages installed, so restarting the window manager created the SGI client and server situation which is what the guide you recommended clearly suggests.



But my point still remains, if my card is actually completely supported why didn't the setup program fro the ubuntu OS configure it correctly..

What is ismod? Do you mean insmod? What would you like me to do with this command?

What are my next steps?

---

### Post by nzadLithium on 2007-10-14
lol im sry i didnt really read the guide i gave you i just looked over it quickly and it looked like it would help :D I just read the whole thing now and i don't see why it wouldn't work. One thing i do wonder whether it would cause problems is the sudo modprobe -r fglrx i'm thinking it would probably load that module again on reboot.

I'm not sure why ubuntu didnt set it up itself i think it should as well. Xorg comes packaged with the driver you need so it shouldn't be a liscensing problem or anything. (like all the mpeg stuff :S)

no i don't mean insmod. insmod is a program that loads up modules for you. (modules are the same thing as drivers pretty much)

i mean lsmod this command lists all your current drivers.

you shouldn't need to use insmod anyway. Modprobe works a lot better.

anyway post the output of lsmod then we can see what its loading and what its not hopefully. It might be hard to see what that command is so i'll write it in caps too. make sure you write it in lower case in terminal though LSMOD

and if you ever want to see what a command does you can usually type man (command) in the terminal and it will give you a very in depth guide to the command :) also if it doesnt show then just try doing the same thing in a google search :)

---

### Post by smacfarl on 2007-10-15
snd_rtctimer            4384  0 
ipv6                  273892  10 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
radeon                125472  0 
drm                    83348  1 radeon
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
button                  8976  0 
video                  18060  0 
ac                      6148  0 
battery                11012  0 
sbp2                   24072  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
serio_raw               8068  0 
intel_agp              25620  0 
agpgart                35016  2 drm,intel_agp
psmouse                39952  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i82875p_edac            7172  0 
edac_mc                25808  1 i82875p_edac
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
sd_mod                 30336  6 
cdrom                  37536  1 sr_mod
ata_piix               17540  4 
usbhid                 29536  0 
hid                    28928  1 usbhid
skge                   43152  0 
ata_generic             8452  0 
sata_promise           13956  0 
libata                125168  3 ata_piix,ata_generic,sata_promise
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36108  0 
uhci_hcd               26640  0 
usbcore               138248  4 usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor


Am I right in thinking that radeon, indicates the wrong driver is loading?

I didn't do the modprobe step.

I just used synaptic to completely remove the fglrx package. And then logged out to restart my window manager.

---

### Post by nzadLithium on 2007-10-15
its still loading the radeon driver. check your xorg make sure its 'ati'

---

### Post by smacfarl on 2007-10-15
Here's my xorg.conf

#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-180
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by smacfarl on 2007-10-15
So what are the steps to do a full diagnostic?

What should it say "ati" instead of radeon in the lsmod list?

Can I watch it during boot or something to figure out who's loading the wrong module?

---

### Post by nzadLithium on 2007-10-15
i wouldnt try to watch it at boot up. it goes to fast. Someone may know a way of pausing the screen during boot or something but i dont know of it. If you want to see what happened in boot i would wait till you login then do sudo dmesg in the terminal. It gives you all the system messages that have happened (including the ones during boot)

I think i may have found your problem though.

You haven't done any of this:
> 
Finalizing
      
Then check the "ServerLayout" section:

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


That stuff is in the guide but i dont see any of that is your xorg file.
You NEED Option "AIGLX" "true"
that is the option to enable 3d accelleration!

Just put the Option "AIGLX" "true" on the next line after serverlayout. You don't need to change anything below it.

You won't need the option composite bit that was in the tutorial (just so if you take another look at it you don't put that in) because from what ati shows on the website you don't have a tv connector on your card.

---

### Post by smacfarl on 2007-10-15
Sorry glxinfo still says No.

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-180
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


lsmod still says radeon.

What can I do to debug this?

---

### Post by nzadLithium on 2007-10-15
have you done this?

sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
If your missing any of those thats probably your problem so let it install them and then restart x. 

If you still don't get direct rendering then try these I dont see how these would help but a guide suggested it so its worth a try.

try adding this after bus id in device
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"

in modules add
Load        "dbe"
after load "vbe"

try adding this at the end of your xorg. I don't see why this would do anything for 3d accelleration as i am pretty sure you dont need it but try it anyway.

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by smacfarl on 2007-10-16
I did all those things none work, while I was waiting for your next response. I've been searching through the forums and the web for RV100 related info. It seems from the postings all around there's two classes of people, those who get everything to work right off and those of us who have very difficult times. 

By doing export LIBGL_DEBUG=verbose I get

name of display: :0.0
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0  screen: 0

So this looks like some kind of error in the libgl somewhere, What causes it, or what I can do about it I don't know.

Is there someone someone somwhere in ubuntu land that has more knowledge of these problems? I mean according to all the wikis my card is supposed be completely supported. Why the heck is it this hard to get it working?

I would like to know what exactly the xorg.conf does? And I would like to know what the drivers are doing so that I could debug what's happening more closely..

 Is there like an ATI Ubuntu wizard hanging out somewhere I could talk to? Do you know of anyone who's really good with this stuff?

---

### Post by nzadLithium on 2007-10-16
everyone i know that uses linux won't touch ati cards because its either get an older card (like you have) or use the ati binaries which are crap.

The most likely reason for this i think is that you still have the fglrx module installed. Running the ati open source driver while the propriety driver is still installed is supposed to cause this problem. 

I'm pretty sure with Nvidia cards that if you have some specific module loaded with another specific module that you lose 3d accelleration as well. That could be another possibility? I wouldn't go playing with the modules though :)

The xorg.conf is the xorg (xserver) configuration file. It tells the xorg process what to load when it starts. It does all the stuff to do with mouse keyboard graphics and tablets (if you have one).

You might be able to get more help at the xorg mailing list.

click system, administration, system log.
on the left click xorg.0.log

post the contents here hopefully we can go through and find out where its failing.

---

### Post by smacfarl on 2007-10-16
here goes.

I notice two things.

1. It says it loads the ati and then the radeon driver,

2. Then later on it says it fails to initiate AGP.

Here are the relevant changes to my xorg.conf

Section "Module"
	Load	"i2c"
	Load	"bitmap"
        Load    "dbe"
 	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

dbe place after bitmap

Section "Device"
	Option		"AGPMode"		"4"
	Option		"AGPSize"		"128"
	Option		"GARTSize"		"64"
	Option 		"ColorTiling" 		"true"
	Option 		"EnablePageFlip"	"true"
	Option 		"AccelMethod" 		"XAA"
	Option 		"XAANoOffScreenPixmaps" "true"
	Option 		"AGPFastWrite" 		"true"
	Option 		"BackingStore" 		"true"
	Option 		"SubPixelOrder" 	"NONE"
	Option 		"DynamicClocks"		"true"
	Option		"RenderAccel"		"true"

        Identifier        "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Driver            "ati"
        BusID             "PCI:1:0:0"
EndSection

Whole bunch of options I got from a ubuntu post here. Don't know if any matter.

Section "Monitor"
	Identifier	"A70"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"A70"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Simplified moniter and screen setup


Section "ServerLayout"
        Option          "AIGLX"         "true
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

The other options that most how-tos reccommend don't know if any are really necessary.

---

### Post by nzadLithium on 2007-10-16
k i spent a few minutes searching. Found this bug report.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684)
The errors you are getting seem to be specific to feisty and it will work fine using edgy. People have said doing this gets it going in feisty

> As a soft workaround, blacklisting the modules has worked perfectly.
=> add the following two lines at the beginning of /etc/modprobe.d/blacklist:
blacklist i82875p_edac
blacklist edac_mc

Now desktop effects (wobbly+cube) work like a charm with the open source RADEON driver.

try that see what happens.

If it still doesn't work it is possible that you may have to change module loading order as well.
> I solved the problem simply blacklisting e7xxx_edac and edac_mc, then putting this lines in this exact order in /etc/modules:

agpgart
intel_agp
drm

---

### Post by smacfarl on 2007-10-16
Doing those things and rebooting has got the direct render to say Yes.

Thanks.

however I am not convinced that things are working the way they should. glxgears for example now flashes, when it runs though the gear turns are actually smooth.

I installed Armagedatron Advanced which runs smoothly but suddenly crashes to a halt with an caught exception.

GL Billards has a white flash in the background around half the table.

I am unable to determine if the 3d chess games work or if they are hard to use.

Is there a good set of sample apps I can run to test this stuff? Is there somewhere I could go to learn more about what the xserver is doing? Also I think this should be an Ubuntu bug that needs attention. If my card is supposed to be natively supported why do I have to go blacklisting modules and adding other ones. Who do I talk to help the install crew make this work out of the box.

---

### Post by nzadLithium on 2007-10-16
if you are refering to the 3d chess game packaged with ubuntu then it is just hard to get to work. there is a library you need for the 3d acceleration for that game that was not available in synaptic last time i checked.

You could go to that bug report above and say it happened to you as well and you used same fix.

can you post some pics or vids of all that stuff thats not working?

---

### Post by smacfarl on 2007-10-16
So with Armagedatron Advanced the game just plain crashes, particularly near crash explosion time. Literally the whole application just shuts down and goes away.

With BIlliards GL the text does a lot of flickering, just like glxgears, It's like intermittant bands of black with lots of redraws. 

I tried Dream Chess 3d, and Brutal Chess. Brutal Chess it was very hard to select a piece and when a piece was finally selected it jumped all around the board no matter how I moved the mouse. Dream Chess 3d it was very hard to select a piece and then it's destination.

Not that I really care about any of these games, I just wanted to see the 3d working.

So i think I need to tweak some more setting to get this to work flawlessly. Is there like a default application for OpenGL that we can test and evaluate to determine if everything is working. I know with Direct X on windows there's a whole test suite to determine what works and what doesn't and how fast, etc. It would be nice if Ubuntu had the same sort of thing.

One of the things that motivated me to get OpenGL working was SDL support. I'm going to look into how that's working now. Any word from the ubuntu collective on getting this fixed out of the box with Gutsy or a Gutsy update?

Also I am getting annoying little bright green rectangles trails whenever I move the mouse over the drawing area in GIMP. I have attached a screenshot of these trails. Over drawing the application with another window erases them, but creates little blocks of the background. Also minimizing and restoring completely cleans up the trails.

I have reported to the launchpad thread you recommend above.

---

### Post by nzadLithium on 2007-10-16
Im thinking you should delete that composite bit now. (see if it still loads 3d) then see if it gets rid of it. 

Then if that dont work try deleting those options lines in device. (see if it still loads 3d and it gets rid of those problems).

Those are the only things we have done different to a default install i think. (part from the blacklisting thing which we still need)

See if its any of those.

---

### Post by dj_deef on 2007-10-17
(I come from [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684))

You have to remove all the useless options you set in your xorg.conf and restore it as it was after feisty installation... the only option you want to have is xaanoofscreenpixmaps that you need for compiz (if you want to use it).
Then glxgears will work correctly.

---

### Post by bromix on 2007-10-17
bump

---

### Post by smacfarl on 2007-10-17
So far so good.

I removed all the options from the Device section and rebooted. Most 3D app problems went away. No flickering in glxgears. No flashing in Billard gl.

Amegetron still exits unexplainably, And I still get the green trails in GIMP.

So this is what my xorg.conf looks like currently

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
 	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
        Load    "dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
        Identifier        "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Driver            "ati"
        BusID             "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"A70"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"A70"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
        Option          "AIGLX"         "true
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection


So additions to the default are

Load "dbe" in Module Section

Option          "AIGLX"         "true  in Server Layout 

and the DRI and Extensions section.

Would you like me to step back each of these and in which order?

---

### Post by rustybronco on 2007-10-17
I haven't read the thread completely so I don't know if it will help any. 

[http://fractaldimension.org.uk/ubuntu/xorg/xorg.conf.rustybronco.txt](http://fractaldimension.org.uk/ubuntu/xorg/xorg.conf.rustybronco.txt)
and..
[http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml)

It did run compiz and iirc I had at one time compiz-fusion on my 7.04 install.

Section "Device"
	Identifier	"radeon 7000/ve"
	Driver		"ati"

ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]  Ubuntu 7.04 7.2.0 ati "Aiglx" Yes" 1.2 1440x900 24 485 2.6.20-16-generic

yes it does 3-d

---

### Post by rustybronco on 2007-10-17
> **nzadLithium said:**
> 
That stuff is in the guide but i dont see any of that is your xorg file.
You NEED Option "AIGLX" "true"
that is the option to enable 3d accelleration!

Yes...

---

### Post by smacfarl on 2007-10-17
So backing out every change including the DRI section and the Option "AIGLX" "true". And I still have 3d accelleration. The only thing I notice is that when removing AIGLX option my glxgears dropped from 300-310 fps to 280-290 FPS.

My xorg.conf now looks like this.

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
 	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
        Identifier        "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
        Driver            "ati"
        BusID             "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"A70"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"A70"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

So it seems that adding the modules to the modules file was the key thing. Somehow the default setup of Ubuntu does not install the support for free ATI driver correctly. Whether it's that or there is some serious error in the freeware ATI driver itself, who do I report this too? 

BTW I have reported the green trails to the GIMP bugzilla after finding someone on a Fedora list with the same problem. It appears that there is some problem between how GIMP is drawing the cursor and how the ATI driver executes this command.

How do I get on the testing list for this ATI driver?

---

### Post by nzadLithium on 2007-10-17
smacfarl 

put this back in 
option "aiglx" "true" 

And you have deleted your access to the direct rendering interface! 
Thats probably why ur fps is sucking. I'm pretty sure even a 7000 is capable more than 300fps.

add this to the bottom

Section "DRI"
Mode 0666
EndSection

I never told you to delete either of those:confused: who told you to do that??

about your Armagedatron Advanced game can you run it in a terminal and post the last 5 lines here?

and try the gimp again once you stuck those back in and restarted x.

---

### Post by smacfarl on 2007-10-17
So I just backed out all four differences from a vanilla xorg.conf file to see if I could get glxinfo to say no, or otherwise interrupt the 3d support.

What I found out is that none of those four things have any effect. 

So before adding DRI back and the option "aiglx" "true"  I was getting 288.1 FPS.

After adding them back and restarting X I now consistently get 287.5 FPS. Nearly identical results.

Amegedron when run from the terminal crashes pretty reliably within a minute or so and prints

Trying to start sound. Just restart Armagetron Advanced in case of crash.
Segmentation fault (core dumped)

The sound does work. The core dump is after playing the game for a couple turns.

As for the GIMP issue this is definitely a bug that exists between GIMP and the ATI driver, I have already posted this to GIMP bugzilla. By changing my gimprc file I was able to change the color of the mouse trails, so this should be a good clue to where the interaction is buggy.

So in backing out all the changes to xorg.conf, one by one and seeing none of them have any effect, I have conclusively proved that the problem was entirely in the module loading. This indicates a problem with the ATI driver and the Radeon 7000 card. 

At this point it probably makes sense to put me into the test group for development of that driver. Is this possible?

BTW Billards GL plays flawlessly and doesn't crash, so I think the Amegedatron problem is entirely with how they use the OpenGL and how the OpenGL makes use of the ATI driver. Like the GIMP issue I think both of these things are specific bugs in the driver.

---

### Post by nzadLithium on 2007-10-18
segmentation fault usually indicates some sort of memory problem. I seriously doubt you would get a segmentation fault just from using ati open source drivers. I think you should try finding a way to contact the whoever is developing Armagedatron Advanced and see if they know whats going on.

On gentoo forums someone said vbe is supposed to slow graphics cards down for some reason
try commenting in modules
load "vbe"
and make sure you add 
load "dbe"

see if that gets your fps up a bit.

can you try a full 3d game like quake or rtcw or something??? see if you get at least 50 fps coz it seems real sad your only getting 287.

people are reporting 800 as a minimum for 9500 cards so im thinking you should be getting at least 500.

---

### Post by nzadLithium on 2007-10-18
oh i just thought ill add some whining. Your getting the same fps im getting with an x1300!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!111

---

### Post by smacfarl on 2007-10-18
So changing from vbe to dbe had no effect on glxgears speed.

I'm still at 287.5 FPS.

going to install rtcw. 

So can I get into the driver test group now that we have established it's not an xorg.conf problem?

---

### Post by smacfarl on 2007-10-18
So where and how do I get quake3 or rtcw for Ubuntu. I thought it would be part of the packages available, but it's not. All Ubuntu seems to have is open arena.

Any recommendations?

---

### Post by nzadLithium on 2007-10-18
lol ok chances are that you dont have actually have a key for those games then :p

get rtcw et instead its free.

i should warn you its fairly large. 260mb for the installer plus about another 10 for patches

installer: [http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408#Download](http://returntocastlewolfenstein.filefront.com/file/Enemy_Territory;14408#Download)

first patch: [http://returntocastlewolfenstein.filefront.com/file/ET_Patch_Linux;18631](http://returntocastlewolfenstein.filefront.com/file/ET_Patch_Linux;18631)

upgraded binaries: [http://returntocastlewolfenstein.filefront.com/file/Wolfenstein_Enemy_Territory_260b_Patch_linux;62010](http://returntocastlewolfenstein.filefront.com/file/Wolfenstein_Enemy_Territory_260b_Patch_linux;62010)

if you can get that installed then get into the game 
open terminal (press ~ key (below escape)) and do write /com_maxfps 76 press enter.
write /cg_drawfps 1 press enter
close consol and see what your fps is. will be in top right portion of screen.

---

### Post by smacfarl on 2007-10-18
So I installed it. had to install gtk1.2 package to make the install happy to run.

when i type /com_maxfps 76 it says cannot write profiles/username/etconfig.cfg

when i run do I have to run as su?

also it says /cg_drawfps 1 is an unknown command.

Also do I have to connect to a game? The terminal comes up on the menu screen.

Is there a terminal command reference somewhere?

---

### Post by nzadLithium on 2007-10-18
[http://www.rtcw.jolt.co.uk/content/enemy_territory/cmdcvarlist/](http://www.rtcw.jolt.co.uk/content/enemy_territory/cmdcvarlist/) 
is a list of commands. 

It seems that you do have to be connected to a server and playing the game for this to work.

Try actually connecting to a server then see if you get the same cannot write profiles thing.
If you still do then its possible that you havent actually set a profile up. Once you get to the main menu click profiles make sure there is actually one listed there and that it says (default) next to it.

If you still get that error after you've checked the profiles then do /fs_homepath
and see what the output is. If it contains your home directory you should be fine but if it doesnt then thats probably what the problem is.

I got my glxgears to up to 1200 now :) my fgl_glxgears ones are still crap though. Im getting 400 :S

with the flgrx drivers you seem to get a greater fps if you add
Load "GLcore"

to the modules section in your xorg.conf you should try it see if it helps you with the open source drivers.

---

### Post by smacfarl on 2007-10-19
GLcore does nothing for me still at 287.5.

Thanks for the tip anyway. When I get some ET numbers I'll post them here.

The GIMP people identified my GIMP issues as a driver problem and now have an active bugzilla bug with xorg. Will keep you posted.

---

### Post by nzadLithium on 2007-10-19
k

---

