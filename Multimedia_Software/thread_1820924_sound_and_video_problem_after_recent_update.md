---
title: "sound and video problem after recent update"
date: 2011-08-08
forum: Multimedia Software
---

### Post by adamo_ on 2011-08-08
Hello.
After recent upgrade which contained the newer kernel ( 2.6.35-30-generic). 
I've started to experience problems with sound and video in programs - deadbeef and totem. 

Both of them dont play any sounds and video in totem is skipping every 3-4 seconds (the same applies to flash videos in browser).

As I run deadbeef from the command line I dont get any significant information.

I run ubuntu 10.10 amd 64. I tried to reinstal gstreamer my programs and codecs with no luck. 
Any help is appreciated.

---

### Post by Basher101 on 2011-08-08
Post your system specs pls so we know if it could be a hardware problem that the kernel has

---

### Post by adamo_ on 2011-08-08
Sorry forgot about that
```

Processor	4x AMD Athlon(tm) II X4 640 Processor
Memory	7934MB (5661MB used)
Operating System	Ubuntu 10.10
Display
Resolution	1920x1200 pixels
OpenGL Renderer	Unknown
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	HDA-Intel - HDA ATI SB
Audio Adapter	HDA-Intel - HDA ATI HDMI
Version
Kernel	Linux 2.6.35-30-generic (x86_64)
Loaded Modules
nls_iso8859_1	
nls_cp437	
vfat	VFAT filesystem support
fat	
cryptd	Software async crypto daemon
aes_x86_64	Rijndael (AES) Cipher Algorithm, asm optimized
aes_generic	Rijndael (AES) Cipher Algorithm
binfmt_misc	
vboxnetadp	Oracle VM VirtualBox Network Adapter Driver
vboxnetflt	Oracle VM VirtualBox Network Filter Driver
vboxdrv	Oracle VM VirtualBox Support Driver
snd_hda_codec_atihdmi	ATI HDMI HD-audio codec
snd_hda_codec_via	VIA HD-audio codec
arc4	ARC4 Cipher Algorithm
radeon	ATI Radeon
joydev	Joystick device interfaces
snd_hda_intel	Intel HDA driver
snd_hda_codec	HDA codec core
snd_hwdep	Hardware dependent layer
snd_pcm	Midlevel PCM code for ALSA.
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
ttm	TTM memory manager subsystem (for DRM device)
drm_kms_helper	DRM KMS helper
ath5k	Support for 5xxx series of Atheros 802.11 wireless LAN cards.
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
psmouse	PS/2 mouse driver
mac80211	IEEE 802.11 subsystem
ppdev	
ath	Shared library for Atheros wireless LAN cards.
edac_core	Core library routines for EDAC reporting
serio_raw	Raw serio driver
parport_pc	PC-style parallel port driver
drm	DRM shared core routines
cfg80211	wireless configuration support
asus_atk0110	
i2c_algo_bit	I2C-Bus bit-banging algorithm
snd	Advanced Linux Sound Architecture driver for soundcards.
edac_mce_amd	AMD MCE decoder
k10temp	AMD Family 10h/11h CPU core temperature monitor
i2c_piix4	PIIX4 SMBus driver
led_class	LED Class Interface
soundcore	Core sound module
snd_page_alloc	Memory allocator for ALSA system.
shpchp	Standard Hot Plug PCI Controller Driver
lp	
parport	
usbhid	USB HID core driver
hid	
usb_storage	USB Mass Storage driver for Linux
r8169	RealTek RTL-8169 Gigabit Ethernet driver
pata_atiixp	low-level driver for ATI IXP200/300/400
ahci	AHCI SATA low-level driver
mii	MII hardware support library
libahci	Common AHCI SATA low-level routines
Devices

Processor
Processors
AMD Athlon(tm) II X4 640 Processor	800,00MHz
AMD Athlon(tm) II X4 640 Processor	1800,00MHz
AMD Athlon(tm) II X4 640 Processor	800,00MHz
AMD Athlon(tm) II X4 640 Processor	800,00MHz
Host bridge	Advanced Micro Devices [AMD] RS780 Host Bridge
PCI bridge	ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx) (prog-if 00 [Normal decode])
PCI bridge	Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) (prog-if 00 [Normal decode])
SATA controller	ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01 [AHCI 1.0])
USB Controller	ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
USB Controller	ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
USB Controller	ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
USB Controller	ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
USB Controller	ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10 [OHCI])
USB Controller	ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
SMBus	ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
IDE interface	ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
Audio device	ATI Technologies Inc SBx00 Azalia (Intel HDA)
ISA bridge	ATI Technologies Inc SB700/SB800 LPC host controller
PCI bridge	ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
USB Controller	ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10 [OHCI])
Host bridge	Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
Host bridge	Advanced Micro Devices [AMD] Family 10h Processor Address Map
Host bridge	Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
Host bridge	Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
Host bridge	Advanced Micro Devices [AMD] Family 10h Processor Link Control
VGA compatible controller	ATI Technologies Inc 760G [Radeon 3000] (prog-if 00 [VGA controller])
Audio device	ATI Technologies Inc RS780 Azalia controller
Ethernet controller	Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
Ethernet controller	Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)

```

---

### Post by Basher101 on 2011-08-08
Im fairly new to ubuntu and linux myself, so i can't help you. At least others will have it easier to help you. Oh - did you try to install the drivers? Go to your system administration and check if you have the latest  drivers

---

### Post by adamo_ on 2011-08-08
I've re-installed the video drivers (ati propertiary). So the video dosn't skip anymore. Still trying to resolve the issue with sound. 

I've also narrowed it down - the sound in sound menu works when I try to test it. So I guess it's something with codecs.

Ok so this is what I did (I don't know if all this step are necessary)
- reinstalled kernel+ videodrivers
- reinstalled all gstreamer
- removed config files from .pulse folder

Now I have my sound back

---

