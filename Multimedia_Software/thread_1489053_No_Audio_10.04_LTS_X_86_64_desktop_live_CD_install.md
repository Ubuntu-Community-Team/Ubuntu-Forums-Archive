---
title: "No Audio 10.04 LTS X_86 64 desktop live CD install"
date: 2010-05-20
forum: Multimedia Software
---

### Post by jfa2214 on 2010-05-20
No sound from ubuntu 10.04 LTS X_86 64 Desktop live CD install. I was able to receive sound on the S/PIDF jack. I was able to set the S/PIDF on the alsa mixer to unmuted. I was not able to set the alsa mixer PCM or Master port to unmuted. I was also unable to find the driver for my Intel HDA audio hardware on the alsa website. I followed the Comprhensive Sound Solutions Users Guide V0.5e. When I was unable to find the alsa device driver I was left with no direction.
My audio device probably is relatively new. Any help, solution or direction will be greatly appreciated.:confused:
Computer- HP G62-144DX Notebook
Processor        : 4x Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
Memory        : 3853MB (918MB used)
Operating System        : Ubuntu 10.04 LTS
User Name        : yesway (wayne)
Date/Time        : Thu 20 May 2010 01:55:06 PM EDT
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel
-Input Devices-
 Power Button
 Lid Switch
 Power Button
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
    Rocketfish Optical Mouse
 Video Bus
 HP Webcam-101
 SynPS/2 Synaptics TouchPad
-Printers-
No printers found
-SCSI Disks-
ATA Hitachi HTS72505
hp CDDVDW TS-L633N
Generic- Multi-Card
MICRONET FANTOM DRIVE

yesway@wayne-laptop:~$ sudo uname -a
[sudo] password for yesway: 
Linux wayne-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
yesway@wayne-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel

yesway@wayne-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
yesway@wayne-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 270

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

---

### Post by race13 on 2010-05-23
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) <-- Maybe this is waht you need. For me and my G62-120EG it was the solution.

---

### Post by double_a on 2011-02-13
[QUOTE=jfa2214;9333688]Same problem:::::::::pls sugget....
No sound from ubuntu 10.04 . I am able to receive sound on the S/PIDF jack. er PCM or Master port to unmuted. I was also unable to find the driver for my Intel HDA audio hardware on the alsa website. I followed the Comprhensive Sound Solutions Users Guide V0.5e. When I was unable to find the alsa device driver I was left with no direction.
  Any help, solution or direction will be greatly appreciated.:confused:
Computer- Compaq Presario CQ62-112TU Notebook
Processor        : Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz

i get following o/p for using:
                               $lscpi -v
Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

i'm new on Linux(Ubuntu) ..... can't get the above sloution

---

