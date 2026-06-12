---
title: "After one of the last updates the Sound is lost."
date: 2012-02-15
forum: Multimedia Software
---

### Post by tirant on 2012-02-15
Standard Ubuntu 11.10 64 bits (Xeon Quad Core)
Creative Sound Blaster CA0106 card.(Sound Blaster Audigy SE iirc)

It has been in the last days, when I totally lost my audio. I checked everything in sound-settings and alsamixer. Switched users and tried all my old kernels. Sound is not coming back.

It seems it has also happened to other people, and the common hardware is 64bit + CA0106 Sound Card:

[http://linux.ittoolbox.com/groups/technical-functional/ubuntu-l/no-sound-in-ubuntu-1110-64-bit-4645160](http://linux.ittoolbox.com/groups/technical-functional/ubuntu-l/no-sound-in-ubuntu-1110-64-bit-4645160)

Booting my installation UBUNTU 11.10 Usb stick brings sound back, the same when booting on Windows 7 (64bit).

I am a developer, but have no idea about sound problems (working in embedded systems), and I do not have much time to debug this, so I ask for your help.

Ubuntu also detects another Audio Card on my nvidia GT520 (HDMI connection). I cannot try that, as I dont have any HDMI device available.

Extract of my lspci -v

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
	Subsystem: Hewlett-Packard Company Device 3318
	Flags: fast devsel
	Capabilities: [40] #00 [0000]

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: db000000-dc0fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d9ffffff
	Capabilities: [40] Subsystem: Hewlett-Packard Company Device 3318
	Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot-), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Vendor Specific Information: ID=0000 Rev=0 Len=000 <?>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
	Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
	Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
	Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3118
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at dd202000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: dc100000-dc1fffff
	Prefetchable memory behind bridge: 00000000c0a00000-00000000c0bfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 3318
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1a, subordinate=1a, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: c0600000-c07fffff
	Prefetchable memory behind bridge: 00000000c0800000-00000000c09fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 3318
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1c, subordinate=1c, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: dc300000-dcffffff
	Prefetchable memory behind bridge: 00000000da000000-00000000daffffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 3318
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=1e, subordinate=1e, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc200000-dc2fffff
	Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 3318
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: c0000000-c01fffff
	Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 3318
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3118
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at dd202400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=30, subordinate=30, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Capabilities: [50] Subsystem: Hewlett-Packard Company Device 3318

00:1f.0 ISA bridge: Intel Corporation 3400 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 3118
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=10 <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 3118
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
	I/O ports at 1830 [size=8]
	I/O ports at 1824 [size=4]
	I/O ports at 1828 [size=8]
	I/O ports at 1820 [size=4]
	I/O ports at 1800 [size=32]
	Memory at dd201000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 3318
	Flags: medium devsel, IRQ 10
	Memory at dd202800 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1840 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GT520 [GeForce GT520] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 83a0
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at db000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at d8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	[virtual] Expansion ROM at dc080000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation HDMI Audio stub (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 83a0
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

10:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Atheros Communications Inc. Device 30a1
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
	Capabilities: [170] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

1e:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)
	Subsystem: Hewlett-Packard Company NC107i Integrated PCI Express Gigabit Server Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at dc200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [48] Power Management version 3
	Capabilities: [40] Vital Product Data
	Capabilities: [60] Vendor Specific Information: Len=6c <?>
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [cc] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number d8-d3-85-ff-fe-8e-4f-54
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: tg3
	Kernel modules: tg3

30:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs SB0570 [SB Audigy SE]
	Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 17
	I/O ports at 3000 [size=32]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

```

Update: I just saw this thread: [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240) I will try to follow the advices listed there as soon as i come back home. I am sorry, but as I said, I was a bit in a hurry :P

---

### Post by tirant on 2012-02-17
Well after following both guides, sound is still not working.

More info:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I tried to play audio through all of the devices and got no sound :(

```
$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
$ aplay -D plughw:1,1 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
$ aplay -D plughw:1,2 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
$ aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
$ aplay -D plughw:1,0 /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```

---

### Post by Yellow Pasque on 2012-02-18
If you haven't remove the 3.0.0-15 kernel, then boot into that until it gets fixed (I've already seen multiple Launchpad bug reports about this hardware/kernel combination).

---

### Post by tirant on 2012-02-20
> **Temüjin said:**
> If you haven't remove the 3.0.0-15 kernel, then boot into that until it gets fixed (I've already seen multiple Launchpad bug reports about this hardware/kernel combination).

I have already booted into all the old kernels i have installed. Nothing. Nada :(

But thanks for the reply.

---

### Post by hbj on 2012-02-28
I am having the same issue

```
ws04:~$ lspci -v | grep -i audio
01:00.1 Audio device: nVidia Corporation Device 0bee (rev a1)
04:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster (rev ff) (prog-if ff)

```

```
ws04:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The system seems to see the Soundblaster, but alsamixer only shows the HDMI sound device and I'm not using HDMI for anything.  The Soundblaster modules are loaded:

```
ws04:~$ lsmod | grep -i ca0106
snd_ca0106             44796  0 
snd_ac97_codec        134826  1 snd_ca0106
snd_pcm                96714  5 snd_hda_codec_hdmi,snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_rawmidi            30547  2 snd_ca0106,snd_seq_midi
snd                    68266  13 snd_hda_codec_hdmi,snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18529  3 snd_ca0106,snd_hda_intel,snd_pcm

```

Update:

Looking at /proc/asound/modules, I see only the hda_intel which I don't want, and the ca106 is missing:

```
ws04:~$ cat /proc/asound/modules
 0 snd_hda_intel
```

Interestingly, another similar workstation has sound working and has:

```
ws05:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_ca0106
```

Where would I look to find out why the module seems to be running from lsmod, but it's not showing up in /proc/asound/modules?  It seems like this might lead to the solution.  Any help much appreciated.

---

### Post by geoffree on 2012-02-28
Maybe this will Help:  When I was trying to adjust the Pulse Audio Volume panel, I saw that the playback was activating the Input indicator bar. Perhaps the circuits got wired backwards. Im using natural language because I dont know what is actually happening except for the visual error.





> **hbj said:**
> I am having the same issue

```
ws04:~$ lspci -v | grep -i audio
01:00.1 Audio device: nVidia Corporation Device 0bee (rev a1)
04:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster (rev ff) (prog-if ff)

```

```
ws04:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The system seems to see the Soundblaster, but alsamixer only shows the HDMI sound device and I'm not using HDMI for anything.  The Soundblaster modules are loaded:

```
ws04:~$ lsmod | grep -i ca0106
snd_ca0106             44796  0 
snd_ac97_codec        134826  1 snd_ca0106
snd_pcm                96714  5 snd_hda_codec_hdmi,snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec
snd_rawmidi            30547  2 snd_ca0106,snd_seq_midi
snd                    68266  13 snd_hda_codec_hdmi,snd_ca0106,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18529  3 snd_ca0106,snd_hda_intel,snd_pcm

```

Update:

Looking at /proc/asound/modules, I see only the hda_intel which I don't want, and the ca106 is missing:

```
ws04:~$ cat /proc/asound/modules
 0 snd_hda_intel
```

Interestingly, another similar workstation has sound working and has:

```
ws05:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_ca0106
```

Where would I look to find out why the module seems to be running from lsmod, but it's not showing up in /proc/asound/modules?  It seems like this might lead to the solution.  Any help much appreciated.

---

### Post by geoffree on 2012-02-28
So it is obvious that there is a problem with the audio on 11.10.
Are there any workarounds?  Any fixes?   From my experimenting with repair it appears that the playback mode is going through the input channels.
I am able to hear audio from news programs or other media.  It's that I can't use my microphone to make calls or record any input from the mic.
So...

Geoffree

---

