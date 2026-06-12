---
title: "Making C-Media 9880 Sound Card works in Ubuntu"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by jcylo2000 on 2006-07-26
Hi everyone :KS ,

I just installed Ubuntu June 2006 version on my x86 Pentium 4 PC. I have a HUGH problem configuring the sound / multimedia system.

I have a C-Media 9880 sound card manufactured in Taiwan. Currently the Volume Control can let me choose between:

a) C-Media CMI 9880 (OSS Mixer) or
b) HDA Intel (Alsa Mixer)

#1 Here is my lspci output:

john@john-desktop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 19)
0000:04:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
0000:04:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

#2 When I run gstreamer-properties at command prompt:
Audio Default plug in: autodetect
Default input plug in: ALSA (Advanced Linux Sound Architecture)
but when I press test button, NO SOUND output!!

#3 Aplay -l output:

john@john-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CMI9880 [CMI9880]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: CMI9880 Digital [CMI9880 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

#4 Ubuntu forum suggested changes: [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

I don't how to change file permissions in /etc/esound/ such that I can overrwrite the existing esd.conf with

john@john-desktop:/etc/esound$ chmod u=rwx,g=rwx,o=rwx esd.conf
chmod: changing permissions of `esd.conf': Operation not permitted

john@john-desktop:/etc/esound$ ls -la *
-rw-r--r-- 1 root root 198 2006-07-20 22:23 esd.conf

Desired changes according to Ubuntu forum:
==========================================
# Make /etc/esound/esd.conf look like this:
Code:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100 # default options are used in spawned and non-spawned mode
default_options=

Q>> Can someone please help me to configure my sound card properly as I am a novice in Unix!!

Many thanks, and take care, John! :p (jcylo2000@yahoo.com)

---

### Post by RoarinPenguin on 2008-02-18
Procedure did not work for me.

However, to edit /etc/sound/esd.conf you need to prefix "sudo" to your command.

Before: chmod u=rwx,g=rwx,o=rwx esd.conf
After: **sudo** chmod u=rwx,g=rwx,o=rwx esd.conf

This is a system file and you're not having proper permissions t edit it unless you elevate your permission to root with command sudo.

Hope it helps.

  RP

---

