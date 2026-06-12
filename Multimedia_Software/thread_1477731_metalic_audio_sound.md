---
title: "metalic audio sound"
date: 2010-05-09
forum: Multimedia Software
---

### Post by msknight on 2010-05-09
I've had a lot of problems with my audio since upgrading to 10.04. I finally did a fresh installation but since updating this morning, the problems are back.

Rhythmbox lost all its codecs, npviewer is now outputting nothing, I had to reset the settings in the "sound" panel ... audio is now just a mess.

Here is my hardware...

H/W path           Device       Class       Description
=======================================================
                                system      GA-MA785GMT-UD2H
/0                              bus         GA-MA785GMT-UD2H
/0/0                            memory      128KiB BIOS
/0/4                            processor   AMD Phenom(tm) II X4 905e Processor
/0/4/a                          memory      128KiB L1 cache
/0/4/c                          memory      512KiB L3 cache
/0/b                            memory      128KiB L1 cache
/0/26                           memory      4GiB System Memory
/0/26/0                         memory      2GiB DIMM 1333 MHz (0.8 ns)
/0/26/1                         memory      2GiB DIMM 1333 MHz (0.8 ns)
/0/26/2                         memory      DIMM 1333 MHz (0.8 ns) [empty]
/0/26/3                         memory      DIMM 1333 MHz (0.8 ns) [empty]
/0/100                          bridge      RS780 Host Bridge Alternate
/0/100/2                        bridge      RS780 PCI to PCI bridge (ext gfx port 0)
/0/100/2/0                      display     GT218 [GeForce 210]
/0/100/2/0.1                    multimedia  High Definition Audio Controller
/0/100/a                        bridge      RS780 PCI to PCI bridge (PCIE port 5)
/0/100/a/0         eth0         network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/11          scsi2        storage     SB700/SB800 SATA Controller [IDE mode]
/0/100/11/0        /dev/sda     disk        500GB SAMSUNG HD502HJ
/0/100/11/0/1      /dev/sda1    volume      46GiB EXT4 volume
/0/100/11/0/2      /dev/sda2    volume      419GiB Extended partition
/0/100/11/0/2/5    /dev/sda5    volume      4761MiB Linux swap / Solaris partition
/0/100/11/0/2/6    /dev/sda6    volume      46GiB Linux filesystem partition
/0/100/11/0/2/7    /dev/sda7    volume      367GiB Linux filesystem partition
/0/100/11/1        /dev/cdrom   disk        CDDVDW SH-S223B
/0/100/12                       bus         SB700/SB800 USB OHCI0 Controller
/0/100/12.1                     bus         SB700 USB OHCI1 Controller
/0/100/12.2                     bus         SB700/SB800 USB EHCI Controller
/0/100/13                       bus         SB700/SB800 USB OHCI0 Controller
/0/100/13.1                     bus         SB700 USB OHCI1 Controller
/0/100/13.2                     bus         SB700/SB800 USB EHCI Controller
/0/100/14                       bus         SBx00 SMBus Controller
/0/100/14.1        scsi0        storage     SB700/SB800 IDE Controller
/0/100/14.1/0.0.0  /dev/cdrom1  disk        DVD-RAM writer
/0/100/14.2                     multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                     bridge      SB700/SB800 LPC host controller
/0/100/14.4                     bridge      SBx00 PCI to PCI Bridge
/0/100/14.4/e                   bus         TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
/0/100/14.5                     bus         SB700/SB800 USB OHCI2 Controller
/0/101                          bridge      K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
/0/102                          bridge      K10 [Opteron, Athlon64, Sempron] Address Map
/0/103                          bridge      K10 [Opteron, Athlon64, Sempron] DRAM Controller
/0/104                          bridge      K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
/0/105                          bridge      K10 [Opteron, Athlon64, Sempron] Link Control


michelle@michelle-desktop:/var/log$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


michelle@michelle-desktop:/var/log$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889A


michelle@michelle-desktop:/var/log$ sudo lshw -c multimedia
  *-multimedia            
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:18 memory:fcffc000-fcffffff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=32
       resources: irq:16 memory:fe024000-fe027fff

...and I've checked the Sound panel, it has only one hardware device listed, "Internal Audio 1Output/1Input" and I had to tell it again that it has 5.1 Analogue output and an Analogue stereo input.  Yes, it has a digital output but I'm not using it.

There is one oddity, though.

The alsamixer lists an "HDA Nvidea" sound card also, but this card has no controls. I'm wondering if it is a hang up from the previous installation and I'm not sure how to get it out of the system if it is. (I'm not sure if this is actually the hardware for the digital out)

alsamixer seems to be returning to a "default" sound card, but I'm not sure how to set that default. I'm wondering whether the default is going to the incorrect HDA Nvidea device, but I don't know how to check.

---

