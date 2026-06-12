---
title: "Working Mic stopped"
date: 2009-09-16
forum: Multimedia Software
---

### Post by irate.turtle on 2009-09-16
My mic stopped working abruptly.

The problem started (I think) after I installed skype 2.1 beta. Initially whenever I started skype the capture and amp levels would goto zero, rendering the mic mute. This would fix on raising the corresponding bars.

Then at some point the bars stopped moving via gnome-volume-control. I could move it using alsamixer but now that doesn't help revive the mic (both internal and external mic; both worked earlier).

Sound works fine.

I read through

[https://wiki.ubuntu.com/SndHdaIntelSoundProblems](https://wiki.ubuntu.com/SndHdaIntelSoundProblems)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=418396](http://ubuntuforums.org/showthread.php?t=418396)

but it didn't help.


Some information I collected using the scripts in the aforementioned wiki

!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Thu Sep 17 01:07:15 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer: Dell Inc.
Product Name: Studio 1535


!!Kernel Information
!!------------------

Kernel release: 2.6.28-15-generic
Operating System: GNU/Linux
Architecture: x86_64
Processor: unknown
SMP Enabled: Yes


!!ALSA Version
!!------------

Driver version: 1.0.18rc3
Library version: 1.0.18
Utilities version: 1.0.18


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
Installed - Yes (/usr/bin/pulseaudio)
Running - Yes

ESound Daemon:
Installed - Yes (/usr/bin/esd)
Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xf6ffc000 irq 2297
1 [HDMI ]: HDA-Intel - HDA ATI HDMI
HDA ATI HDMI at 0xf6dec000 irq 2296


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:284b (rev 04)
Subsystem: 1028:0254
--
01:00.1 0403: 1002:aa28
Subsystem: 1028:0254


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: model=dell-m6
snd-hda-intel: enable_msi=1


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y, Y,Y,Y,Y,Y,Y,Y
enable_msi : 1
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,< NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<N ULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NU LL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NUL L>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
model : dell-m6,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL >,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL> ,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>, <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,< NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N

!!Module: snd_hda_intel
bdl_pos_adj : 1,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y, Y,Y,Y,Y,Y,Y,Y
enable_msi : 1
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,< NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<N ULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NU LL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NUL L>,<NULL>,<NULL>,<NULL>
index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
model : dell-m6,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL >,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL> ,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>, <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,< NULL>,<NULL>,<NULL>
position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0, 0,0,0,0,0,0,0
power_save : 0
power_save_controller : Y
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
single_cmd : N
...
------------------------------------------------------------
I have no clue how to fix ..

Please help

---

