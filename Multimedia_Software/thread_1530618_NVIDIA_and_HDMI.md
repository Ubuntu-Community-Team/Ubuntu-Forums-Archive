---
title: "NVIDIA and HDMI"
date: 2010-07-13
forum: Multimedia Software
---

### Post by misfit815 on 2010-07-13
Like everyone else who posts here, I'm trying to get my video working properly. The problem I'm facing is that I get this at boot:

"Screen(s) found, but none have a usable configuration."

I'm then forced to a low-res display. It seems that my card is not properly getting my TV's EDID info. I'm trying to find a way around that, but haven't been successful yet. One avenue is apparently to provide a CustomEDID using read-edid (actually, get-edid), but that gives me:

"The EDID data should not be trusted as the VBE call failed"

Anyway, here are my details. Any insight is appreciated, of course.


Running Lucid Lynx (10.04)


Hardware:
- MSI GEForce 9500 GT
- Toshiba 46HM84 DLP television


Latest xorg.conf:

```

Section "ServerLayout"
  Identifier "Default Layout"
  Screen 0 "HDMI"
EndSection

Section "Files"
EndSection

Section "Module"
  Load "glx"
EndSection

Section "Monitor"
  Identifier "HDMI"
EndSection

Section "Device"
  Identifier "MSI GEForce 9500 GT"
  Driver "nvidia"
  BusID "PCI:2:0:0"
  VendorName "NVIDIA Corporation"
EndSection

Section "Screen"
  Identifier "HDMI"
  Device "MSI GEForce 9500 GT"
  Monitor "HDMI"
  DefaultDepth 24
  Option "IgnoreEDID" "True"
  Option "ConnectedMonitor" "DFP-1"
  Option "UseDisplayDevice" "DFP-1"
  SubSection "Display"
    Depth 24
    #Modes "1920x1080_60"
    Modes "1280x720_60"
  EndSubSection
EndSection

```

---

### Post by Yellow Pasque on 2010-07-13
Your Monitor and Screen are both using 'HDMI' as the identifier. That might cause the "no usable screen" problem (or maybe it's okay, IDK). I think that even if your monitor has an invalid EDID (or you have no monitor plugged in), you shouldn't be forced to low-graphics mode. X might not autodetect the best defaults for resolution, but the driver should still load.

After you change the Monitor identifier (and the monitor line in the screen section), try restarting X. If you still have issue, post /var/log/Xorg.0.log

---

### Post by misfit815 on 2010-07-18
Changed the identifiers - no luck, of course, but I saw the reasoning behind it. Here's my Xorg.0.log contents:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux horse 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=8ecd534a-ae6c-4807-95c1-2ca68f968e77 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 18 21:15:03 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Default Layout"
(**) |-->Screen "HDMI" (0)
(**) |   |-->Monitor "Toshiba 46HM84"
(**) |   |-->Device "MSI GEForce 9500 GT"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI: (0:1:6:0) 14f1:5b7a:0070:7444 Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder rev 0, Mem @ 0xec000000/67108864
(--) PCI:*(0:2:0:0) 10de:0640:1462:133e nVidia Corporation G96 [GeForce 9500 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP-1"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-1"
(**) Jul 18 21:15:03 NVIDIA(0): Enabling RENDER acceleration
(**) Jul 18 21:15:03 NVIDIA(0): ConnectedMonitor string: "DFP-1"
(II) Jul 18 21:15:03 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jul 18 21:15:03 NVIDIA(0):     enabled.
(EE) Jul 18 21:15:03 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) Jul 18 21:15:03 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Jul 18 21:15:03 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Jul 18 21:15:03 NVIDIA(0):     README for additional information.
(EE) Jul 18 21:15:03 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

---

### Post by misfit815 on 2010-07-20
By the way, before anyone asks, here is the important part of lspci's results:

```

02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)

```

So, correct me if I'm wrong, but I believe I have the BusID correct.

A few more tidbits:
- The nouveau driver was also loaded at one point. It bore similar results. I *think* it's completely gone now, but if there's something that I could have easily missed, I'm all ears.
- Once again, a CustomEDID seems to be a possible solution, but I don't know how to get or create one at this point.
- I don't know that it's pertinent to this, but I'm running Xfce and trying to turn this into a MythTV box. Hence the reason I'd *really* like to get the video figured out.

Any help is appreciated.

---

### Post by Yellow Pasque on 2010-07-20
> (EE)Jul 18 21:15:03 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Jul 18 21:15:03 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Jul 18 21:15:03 NVIDIA(0):     README for additional information.

So look at files in /var/log/ (like kern.log) to (hopefully) see exactly what went wrong.

---

### Post by misfit815 on 2010-07-20
So I looked in kern.log and this was the closest thing to an error:

```

Jul 20 20:58:16 horse kernel: [   15.119929] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
Jul 20 20:58:16 horse kernel: [   15.120136] NVRM: failed to map registers!!
Jul 20 20:58:16 horse kernel: [   15.120139] NVRM: RmInitAdapter failed! (0x10:0x32:1310)
Jul 20 20:58:16 horse kernel: [   15.120148] NVRM: rm_init_adapter(0) failed
Jul 20 20:58:16 horse kernel: [   15.441256] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
Jul 20 20:58:16 horse kernel: [   15.441422] NVRM: failed to map registers!!
Jul 20 20:58:16 horse kernel: [   15.441426] NVRM: RmInitAdapter failed! (0x10:0x32:1310)
Jul 20 20:58:16 horse kernel: [   15.441434] NVRM: rm_init_adapter(0) failed
Jul 20 20:58:16 horse kernel: [   15.739369] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
Jul 20 20:58:16 horse kernel: [   15.739535] NVRM: failed to map registers!!
Jul 20 20:58:16 horse kernel: [   15.739538] NVRM: RmInitAdapter failed! (0x10:0x32:1310)
Jul 20 20:58:16 horse kernel: [   15.739546] NVRM: rm_init_adapter(0) failed
Jul 20 20:58:17 horse kernel: [   16.046564] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
Jul 20 20:58:17 horse kernel: [   16.046731] NVRM: failed to map registers!!
Jul 20 20:58:17 horse kernel: [   16.046734] NVRM: RmInitAdapter failed! (0x10:0x32:1310)
Jul 20 20:58:17 horse kernel: [   16.046742] NVRM: rm_init_adapter(0) failed
Jul 20 20:58:17 horse kernel: [   16.361938] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
Jul 20 20:58:17 horse kernel: [   16.362104] NVRM: failed to map registers!!
Jul 20 20:58:17 horse kernel: [   16.362108] NVRM: RmInitAdapter failed! (0x10:0x32:1310)
Jul 20 20:58:17 horse kernel: [   16.362116] NVRM: rm_init_adapter(0) failed
Jul 20 20:58:17 horse kernel: [   16.664415] vmap allocation for size 16781312 failed: use vmalloc=<size> to increase size.
Jul 20 20:58:17 horse kernel: [   16.664582] NVRM: failed to map registers!!
Jul 20 20:58:17 horse kernel: [   16.664585] NVRM: RmInitAdapter failed! (0x10:0x32:1310)
Jul 20 20:58:17 horse kernel: [   16.664593] NVRM: rm_init_adapter(0) failed

```

A little Googling tells me that nouveau is possibly still in the mix. I've --purge'd it, blacklisted it... not sure what else to do with it. I don't know how to determine if any of it is left on the system, either.

Any more suggestions?

---

### Post by Yellow Pasque on 2010-07-20
Might be a framebuffer device interfering: [http://www.nvnews.net/vbulletin/showthread.php?p=81074](http://www.nvnews.net/vbulletin/showthread.php?p=81074)

Can you post output of:
```
lsmod
```

---

### Post by misfit815 on 2010-07-23
Ok, I know enough to have an idea of what you're talking about, but not how to fix it. Potential conflicts might come from the on-board video (which has the choices On and Auto in the BIOS) and my WinTV card. Anyway, here's lsmod:

```

Module                  Size  Used by
mxl5005s               36463  1 
s5h1409                 8258  1 
tuner_simple           13577  1 
tuner_types            14233  1 tuner_simple
binfmt_misc             6587  1 
cs5345                  2546  1 
tda9887                 9589  1 
tda8290                12092  0 
snd_hda_codec_via      27111  1 
cx8800                 27188  0 
cx88xx                 72596  1 cx8800
ivtv                  137807  0 
bttv                  111669  0 
videobuf_dma_sg        10782  3 cx8800,cx88xx,bttv
videobuf_core          16356  4 cx8800,cx88xx,bttv,videobuf_dma_sg
btcx_risc               3624  3 cx8800,cx88xx,bttv
tuner                  20412  2 
lirc_i2c                5845  0 
lirc_dev                8884  1 lirc_i2c
snd_hda_intel          21941  0 
snd_hda_codec          74201  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx18                  104801  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dvb_core               86142  1 cx18
ppdev                   5259  0 
i2c_algo_bit            5028  4 cx88xx,ivtv,bttv,cx18
cx2341x                12469  2 ivtv,cx18
v4l2_common            15431  8 cs5345,cx8800,cx88xx,ivtv,bttv,tuner,cx18,cx2341x
videodev               34361  8 cs5345,cx8800,cx88xx,ivtv,bttv,tuner,cx18,v4l2_common
v4l1_compat            13251  1 videodev
parport_pc             25962  1 
snd                    54148  11 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia              10216432  0 
ir_common              38875  3 cx88xx,bttv,cx18
tveeprom               11102  4 cx88xx,ivtv,bttv,cx18
psmouse                63245  0 
serio_raw               3978  0 
k8temp                  3024  0 
agpgart                31724  1 nvidia
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
floppy                 53016  0 
sata_nv                19440  2 
pata_amd                8766  0 
forcedeth              49556  0 

```

---

### Post by misfit815 on 2010-07-28
The best answer I've found at this point is:

[http://www.slackwiki.org/NVIDIA-Prompted-Kernel-Compile](http://www.slackwiki.org/NVIDIA-Prompted-Kernel-Compile)

And that requires recompiling my kernel. I'm lucky to change the oil properly, and my option is to drop the engine. Not my favorite plan, especially when I don't know for sure that this is my issue. Any suggestions for what to do next?

---

### Post by papibe on 2010-07-28
Do you have a way to connect a Windows machine to the DLP?

It might be possible to get the EDID info (in text format) from Windows using "[Phoenix EDID Designer]("http://www.tucows.com/preview/329441/Phoenix-EDID-Designer?q=Phoenix+EDID+Designer")".

After that you can convert it to a valid binary EDID file using [this]("http://www.nvnews.net/vbulletin/showpost.php?p=1086826&postcount=1") procedure.

Good Luck!

---

### Post by misfit815 on 2010-07-29
I don't have a Windows box with HDMI out. Am I going to get the same information through S-Video?

---

### Post by papibe on 2010-07-29
Sadly, that won't help you. Different TV's input have different resolutions and timings.

I have a EVGA 9500 GT connected to my Sony HDTV. My card doesn't have a hdmi output, so I use a DVI-to-HDMI cable. Though I had customize my EDID to remove the dummy sound signal, now it's working great.

If you look around it may be possible to found the exact modeline. For example here's a Modeline database that includes several Tohiba DLPs.

[http://www.mythtv.org/wiki/Modeline_Database#Toshiba]("http://www.mythtv.org/wiki/Modeline_Database#Toshiba")

Regards.

---

### Post by rubylaser on 2010-07-30
Just follow this tutorial from the XBMC forums.  This has worked great for my TV.
[http://forum.xbmc.org/showpost.php?p=506251&postcount=1]("http://forum.xbmc.org/showpost.php?p=506251&postcount=1")

If that doesn't work, you can always use modelines.
[http://forum.xbmc.org/showthread.php?t=54685]("http://forum.xbmc.org/showthread.php?t=54685")

---

### Post by misfit815 on 2010-07-30
Ok, the Modeline database has an entry that's close to mine, but not quite it. A nice reference that I had not discovered earlier, though. If I ever find mine, I'll add it there.

As for the tutorial and other ways of finding modelines, they keep referencing my xorg.log, which can't detect anything from the monitor, so it's useless.

As for obtaining the EDID via a windows machine, I need to somehow boot this box up with Windows, because no other box I have has an HDMI out. I haven't quite solved that problem yet.

I'm still leaning toward something else interfering with the nvidia card. I do have an onboard video that I can't completely disable in the bios (options are Enabled and Auto), plus the WinTV card, of course (the whole point of this exercise). But the prime candidate based on what I'm finding online is the riva framebuffer device support built into the kernel.

I'm *really* not in the mood to rebuild my kernel, but I'd like to rule out the riva thing. Does anyone know how I can determine whether or not that's part of the problem?

Thanks.

J

---

### Post by misfit815 on 2010-07-31
Removed the HDMI and TV completely. It's plugged into a Samsung SyncMaster 931BF via a VGA cable. I've modified xorg.conf accordingly. Still getting the same "Screen(s) found, but none have a usable configuration." issue.

---

### Post by misfit815 on 2010-09-05
This was solved by adding the following to /etc/default/grub:

GRUB_CMDLINE_LINUX="vmalloc=256m"

Since then, I have had a serious overscan problem. I've been too frustrated and busy to deal with it. Now that I'm trying again, I'll open a new thread. So this one can be closed as solved.

---

