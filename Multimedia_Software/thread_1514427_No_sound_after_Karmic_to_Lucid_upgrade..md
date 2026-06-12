---
title: "No sound after Karmic to Lucid upgrade."
date: 2010-06-21
forum: Multimedia Software
---

### Post by gadbermd on 2010-06-21
Hi everyone,

The title pretty much says it all, the sound on this system was working fine until I ran the upgrade to Lucid. I've tried everything in the standard troubleshooting guide, the sticky threads and plenty of forum searches but so far I've come up with nada. For some reason Ubuntu refuses to see my soundcard, no matter how much I twist and tweak it. It's an Asus M3A78 motherboard with an on-board Realtek ALC1200 chip (snd-hda-intel). Here's most of the relevant output, hopefully someone can easily spot what's going on because I'm getting snow-blind staring at the monitor...

```


mike@sol:~$ aplay -l
aplay: device_list:223: no soundcards found...
mike@sol:~$ sudo lspci -vnn
00:00.0 Host bridge [0600]: ATI Technologies Inc RX780/RX790 Chipset Host Bridge [1002:5957]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: [c4] HyperTransport: Slave or Primary Interface
	Capabilities: [40] HyperTransport: Retry Mode
	Capabilities: [54] HyperTransport: UnitID Clumping
	Capabilities: [9c] HyperTransport: #1a
	Kernel modules: ati-agp

00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:06.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C) [1002:597c]
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Port (Slot-), MSI 00
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device [1043:8353]
	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
	Capabilities: [100] Vendor Specific Information <?>
	Capabilities: [110] Virtual Channel <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at c000 [size=8]
	I/O ports at b000 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=16]
	Memory at f7fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f7ffe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398] (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f7ffd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f7fff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398] (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ffb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f7ffa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [c0] Power Management version 2
	Capabilities: [e4] Debug port: BAR=1 offset=00e0
	Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: 66MHz, medium devsel
	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c] (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8346]
	Flags: slow devsel, IRQ 16
	Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64

00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399] (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82ef]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f7ff9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Flags: fast devsel
	Capabilities: [f0] Secure device <?>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9500 GT] [10de:0640] (rev a1)
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at fbe80000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information <?>
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:82c6]
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at e800 [size=256]
	Memory at fbfff000 (64-bit, non-prefetchable) [size=4K]
	Memory at f6ff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbfc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 81-68-10-ec-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169

mike@sol:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
vboxnetadp              6326  0 
vboxnetflt             15194  0 
vboxdrv               190441  2 vboxnetadp,vboxnetflt
snd_hda_intel          21877  0 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ppdev                   5259  0 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54148  11 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             25962  1 
asus_atk0110            9017  0 
psmouse                63245  0 
i2c_piix4               8335  0 
serio_raw               3978  0 
nvidia               9961216  28 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
k8temp                  3024  0 
ati_agp                 5094  0 
agpgart                31724  2 nvidia,ati_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
hid_logitech            7388  0 
hid_pl                  2427  0 
ff_memless              4093  2 hid_logitech,hid_pl
usbhid                 36110  2 hid_logitech,hid_pl
hid                    67032  3 hid_logitech,hid_pl,usbhid
floppy                 53016  0 
r8169                  33980  0 
mii                     4381  1 r8169
pata_atiixp             3148  0 
ahci                   32008  2 
mike@sol:~$ dmesg|egrep 'hda|HDA'
[   27.480533] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.508039] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   29.512015] hda-intel: Codec #0 probe error; disabling it...
[   30.548014] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x000f0000
[   30.548648] hda-intel: no codecs initialized
[   30.548745] HDA Intel 0000:00:14.2: PCI INT A disabled
mike@sol:~$ cat /tmp/alsa-info.txt.hRyy5Og3k6 
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Jun 21 04:24:07 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.04 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.32-22-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------



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

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
	Subsystem: 1043:8346


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
snd-hda-intel: model=6stack-dig


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 3 Jun 20 23:17 /dev/snd/seq
crw-rw----+ 1 root audio 116, 2 Jun 20 23:17 /dev/snd/timer


!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:223: no soundcards found...

ARECORD

arecord: device_list:223: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
snd_hda_intel
snd_hda_codec
snd_hwdep
snd_pcm_oss
snd_mixer_oss
snd_pcm
ppdev
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
joydev
fbcon
tileblit
font
bitblit
softcursor
snd
parport_pc
asus_atk0110
psmouse
i2c_piix4
serio_raw
nvidia
vga16fb
vgastate
soundcore
snd_page_alloc
k8temp
ati_agp
agpgart
lp
parport
hid_logitech
hid_pl
ff_memless
usbhid
hid
floppy
r8169
mii
pata_atiixp
ahci


!!ALSA/HDA dmesg
!!------------------

[   27.463337] Console: switching to colour frame buffer device 80x30
[   27.480533] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.508039] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[   29.512015] hda-intel: Codec #0 probe error; disabling it...
[   30.548014] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x000f0000
[   30.548648] hda-intel: no codecs initialized
[   30.548745] HDA Intel 0000:00:14.2: PCI INT A disabled
[   31.558903] __ratelimit: 35 callbacks suppressed
```

---

### Post by gadbermd on 2010-06-21
(bump)

Any ideas? I've tried multiple alsa-base.conf configs, modprobe's, apt-get --reinstalls, and running alsaconf, all with no luck. Not sure what the deal is but it sounds like I'm probably going to have to shift back to Karmic.

---

### Post by lkjoel on 2010-06-21
Click on [Fix my sound!]("https://help.ubuntu.com/community/OpenSound") in my sig.
That should fix it.

Let me know if it works!

---

### Post by lidex on 2010-06-22
First undo your fixes. Uninstall alsa-backports (if installed). Remove custom alsa-base options. Update your system and kernel:
```
sudo apt-get update
sudo apt-get upgrade
sudo update grub
```
**Reboot**

Now this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

And this. ```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

Finally. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by lkjoel on 2010-06-22
Lidex, I just want to know, since we have two different approaches of how to fix the sound problems, why do you think my method doesn't work?

I know that OSS does not support as many sound cards as ALSA, but for those whose soundcard is supported by OSS, I don't see why they shouldn't use OSS.
OSS 4.x is not outdated.
OSS also fixes the flash sound.
I did get my sound to work with ALSA, but the flash sound didn't work.

If you know how to make ALSA and Flash sounds work, please tell me.
I am not a sound expert :p
And if you think my approach is wrong, please tell me why!

---

