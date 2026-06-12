---
title: "graphics problem"
date: 2011-01-01
forum: Multimedia Software
---

### Post by ice2921 on 2011-01-01
For the past month or so I have been having some issues with  screen crashing and displaying funky colors. Basically it happens at completely random times, doing completely random things. The screen goes to a pink color then freezes the the only way I can gain control again is if I restart the machine or restart gdm via ssh. This is really puzzling me. Perhaps there are some logs I can look at?

A little bit about my system:

```


Processor	2x Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz
Memory	4059MB (1321MB used)
Display
Resolution	1680x1050 pixels
OpenGL Renderer	GeForce 9500 GT/PCI/SSE2
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	HDA-Intel - HDA NVidia
Audio Adapter	USB-Audio - USB camera

Macintosh mouse button emulation	
AT Translated Set 2 keyboard	
PS2++ Logitech MX Mouse	
HDA Digital PCBeep	
Printers (CUPS)
Canon-PIXMA-MP160	Default
	
Operating System

Version
Kernel	Linux 2.6.32-27-generic (x86_64)
Compiled	#49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010
C Library	GNU C Library version 2.11.1 (stable)
Default C Compiler	GNU C Compiler version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)
Distribution	Ubuntu 10.04.1 LTS
Current Session
Desktop Environment	GNOME 2.30.2

Loaded Modules

isofs	
udf	Universal Disk Format Filesystem
crc_itu_t	CRC ITU-T V.41 calculations
binfmt_misc	
ppdev	
vboxnetadp	Oracle VM VirtualBox Network Adapter Driver
vboxnetflt	Oracle VM VirtualBox Network Filter Driver
vboxdrv	Oracle VM VirtualBox Support Driver
snd_hda_codec_realtek	Realtek HD-audio codec
nvidia	
snd_usb_audio	USB Audio
snd_usb_lib	USB Audio/MIDI helper module
snd_hda_intel	Intel HDA driver
snd_hda_codec	HDA codec core
snd_pcm_oss	PCM OSS emulation for ALSA.
snd_mixer_oss	Mixer OSS emulation for ALSA.
snd_pcm	Midlevel PCM code for ALSA.
snd_seq_dummy	ALSA sequencer MIDI-through client
snd_seq_oss	OSS-compatible sequencer module
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_hwdep	Hardware dependent layer
w83627ehf	W83627EHF driver
hwmon_vid	hwmon-vid driver
fbcon	
tileblit	Tile Blitting Operation
font	Console Fonts
bitblit	Bit Blitting Operation
softcursor	Generic software cursor
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
vga16fb	Legacy VGA framebuffer device driver
vgastate	VGA State Save/Restore
coretemp	Intel Core temperature monitor
gspca_sonixj	GSPCA/SONIX JPEG USB Camera Driver
gspca_main	GSPCA USB Camera Driver
videodev	Device registrar for Video4Linux drivers v2
v4l1_compat	v4l(1) compatibility layer for v4l2 drivers.
v4l2_compat_ioctl32	
snd	Advanced Linux Sound Architecture driver for soundcards.
soundcore	Core sound module
snd_page_alloc	Memory allocator for ALSA system.
shpchp	Standard Hot Plug PCI Controller Driver
psmouse	PS/2 mouse driver
serio_raw	Raw serio driver
i2c_nforce2	nForce2/3/4/5xx SMBus driver
lp	
parport	
ohci1394	Driver for PCI OHCI IEEE-1394 controllers
floppy	
ieee1394	
pata_amd	low-level driver for AMD and Nvidia PATA IDE
forcedeth	Reverse Engineered nForce ethernet driver
sata_nv	low-level driver for NVIDIA nForce SATA controller
Display
Display
Resolution	1680x1050 pixels
Vendor	The X.Org Foundation
Version	1.7.6
Monitors
Monitor 0	1680x1050 pixels
Extensions
BIG-REQUESTS	
Composite	
DAMAGE	
DOUBLE-BUFFER	
DPMS	
DRI2	
GLX	
Generic Event Extension	
MIT-SCREEN-SAVER	
MIT-SHM	
NV-CONTROL	
NV-GLX	
RANDR	
RECORD	
RENDER	
SECURITY	
SHAPE	
SYNC	
X-Resource	
XC-MISC	
XFIXES	
XFree86-DGA	
XFree86-VidModeExtension	
XINERAMA	
XINERAMA	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
OpenGL
Vendor	NVIDIA Corporation
Renderer	GeForce 9500 GT/PCI/SSE2
Version	3.3.0 NVIDIA 260.19.29
Direct Rendering	Yes
```

I am currently using the following NVIDIA driver:

```
NVIDIA UNIX x86_64 Kernel Module  260.19.29  Wed Dec  8 12:08:56 PST 2010
```

Let me know if you need any more information. thanks

---

### Post by ice2921 on 2011-01-01
anyone ?

---

