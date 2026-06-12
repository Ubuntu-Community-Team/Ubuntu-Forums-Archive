---
title: "No sound in Ubuntu 12.10"
date: 2012-11-27
forum: Multimedia Software
---

### Post by chickooiyer on 2012-11-27
Hi All 

After a fresh install of ubuntu 12 .10 i am not having any sound. Please find the out of the alsa-info.sh script. Please help me in getting my sound back.```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.61
!!################################

!!Script ran on: Tue Nov 27 05:37:16 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 12.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu quantal (12.10)"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.
Product Version:   To Be Filled By O.E.M.
Firmware Version:  P2.30


!!Kernel Information
!!------------------

Kernel release:    3.5.0-18-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.25
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:05.0 0403: 10de:03f0 (rev a2)
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: position_fix=1 model=generic


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  1 Nov 27 10:56 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Nov 27 10:56 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:252: no soundcards found...

ARECORD

arecord: device_list:252: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
bnep
ppdev
kvm_amd
kvm
psmouse
serio_raw
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
parport_pc
snd_seq_midi
btusb
bluetooth
snd_rawmidi
snd_seq_midi_event
snd_seq
k8temp
snd_timer
edac_core
edac_mce_amd
snd_seq_device
nouveau
ttm
drm_kms_helper
drm
snd
mac_hid
i2c_algo_bit
mxm_wmi
video
wmi
soundcore
snd_page_alloc
i2c_nforce2
lp
parport
sata_nv
forcedeth
pata_amd


!!ALSA/HDA dmesg
!!--------------

[   19.831786] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   19.831797] hda_intel: Disabling MSI
[   19.831833] snd_hda_intel 0000:00:05.0: setting latency timer to 64
[   19.860040] hda-intel: no codecs found!
[   19.902361] microcode: AMD CPU family 0xf not supported


```

Here is the output of lspci

```
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a2)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
**00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)**
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6100 nForce 405] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```

---

### Post by chickooiyer on 2012-12-10
> **chickooiyer said:**
> Hi All 

After a fresh install of ubuntu 12 .10 i am not having any sound. Please find the out of the alsa-info.sh script. Please help me in getting my sound back.```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.61
!!################################

!!Script ran on: Tue Nov 27 05:37:16 UTC 2012


!!Linux Distribution
!!------------------

Ubuntu 12.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu quantal (12.10)"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.
Product Version:   To Be Filled By O.E.M.
Firmware Version:  P2.30


!!Kernel Information
!!------------------

Kernel release:    3.5.0-18-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.25
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:05.0 0403: 10de:03f0 (rev a2)
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-intel: position_fix=1 model=generic


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  1 Nov 27 10:56 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Nov 27 10:56 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:252: no soundcards found...

ARECORD

arecord: device_list:252: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
bnep
ppdev
kvm_amd
kvm
psmouse
serio_raw
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm
parport_pc
snd_seq_midi
btusb
bluetooth
snd_rawmidi
snd_seq_midi_event
snd_seq
k8temp
snd_timer
edac_core
edac_mce_amd
snd_seq_device
nouveau
ttm
drm_kms_helper
drm
snd
mac_hid
i2c_algo_bit
mxm_wmi
video
wmi
soundcore
snd_page_alloc
i2c_nforce2
lp
parport
sata_nv
forcedeth
pata_amd


!!ALSA/HDA dmesg
!!--------------

[   19.831786] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   19.831797] hda_intel: Disabling MSI
[   19.831833] snd_hda_intel 0000:00:05.0: setting latency timer to 64
[   19.860040] hda-intel: no codecs found!
[   19.902361] microcode: AMD CPU family 0xf not supported


```

Here is the output of lspci

```
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a2)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a2)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
**00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)**
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6100 nForce 405] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

```
I think there is no help available to this issue and this will stay as open for a very long time.

---

