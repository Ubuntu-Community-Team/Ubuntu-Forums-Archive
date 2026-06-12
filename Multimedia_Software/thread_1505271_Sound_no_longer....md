---
title: "Sound no longer..."
date: 2010-06-08
forum: Multimedia Software
---

### Post by ignisuti on 2010-06-08
I initially had sound on my system, but seem to have lost it somewhere along the way.

I've been trying to diagnosis, but got lost in the infinite loop of trouble-shooting info I found online. Here are a couple commands I tried and the output of each. Please let me know if you see a problem.

```

joe@data:~$ lsmod | grep snd
snd_usb_audio          84224  0 
snd_usb_lib            16284  1 snd_usb_audio
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  1 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_usb_audio,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

```

```

joe@data:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at cc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at c880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at c800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f9ffbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at b880 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7379
	Flags: medium devsel, IRQ 3
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [disabled] [size=128]
	[virtual] Expansion ROM at fea80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 379c
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at e800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169


```

---

### Post by Jinger on 2010-06-09
Have you tried installing a new version of ALSA?

---

### Post by ignisuti on 2010-06-09
> **Jinger said:**
> Have you tried installing a new version of ALSA?

I'm a noob. So, you'll have to hold my hand a little bit. How do I do that?

---

### Post by Jinger on 2010-06-09
Let's start seeing what version of Alsa you have.
Write in terminal this code:
```
dpkg -l | grep "alsa"

```

Would you mind posting here the results?

---

### Post by ignisuti on 2010-06-09
I'll have to give this a try later tonight. In order to save time, could you please post the correct version and what I should do next if I already have the correct version?

---

### Post by lidex on 2010-06-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by ignisuti on 2010-06-09
> **Jinger said:**
> Let's start seeing what version of Alsa you have.
Write in terminal this code:
```
dpkg -l | grep "alsa"

```

Would you mind posting here the results?

```
joe@data:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.20+dfsg-1ubuntu5                       ALSA driver configuration files
ii  alsa-utils                                     1.0.20-2ubuntu6                            ALSA utilities
ii  bluez-alsa                                     4.51-0ubuntu2                              Bluetooth audio support
ii  gstreamer0.10-alsa                             0.10.25-2ubuntu1.2                         GStreamer plugin for ALSA
ii  libesd-alsa0                                   0.2.41-5                                   Enlightened Sound Daemon (ALSA) - Shared lib
ii  libsdl1.2debian-alsa                           1.2.13-4ubuntu4                            Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                                14.3.0-1build1                             SoX alsa format I/O library
iF  linux-alsa-driver-modules-2.6.31-20-generic    2.6.31-20.201005060600                     Ubuntu-supplied Linux modules for version 2.
iF  linux-backports-modules-alsa-2.6.31-22-generic 2.6.31-22.24                               Ubuntu supplied Linux modules for version 2.
iU  linux-backports-modules-alsa-karmic-generic    2.6.31.22.35                               Backported drivers for alsa-driver snapshot.
```

---

### Post by ignisuti on 2010-06-09
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

It's a home-built PC: New Intel Core 2 Quad LGA775 Q6600 CPU Retail Box (B3). 
I'm using the motherboard's sound.

```
joe@data:~$ uname -a
Linux data 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
joe@data:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
joe@data:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May  6 2010 for kernel 2.6.31-20-generic (SMP).
joe@data:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC888

```

---

### Post by ignisuti on 2010-06-09
Just a random shot in the dark, but I bought a little device that outputs sound via USB. I bought this b/c I have a multi-seat setup and wanted the second seat to have sound. I'm pretty sure sound was working before I tried it. I never got the thing working, but I'm wondering if it was around that time when my sound on the motherboard stopped working.

---

### Post by lidex on 2010-06-09
You do have some mismatched alsa componeents. I would suggest uninstalling the backports and rebooting followed by a full alsa upgrade via the upgrade link in my sig.

---

### Post by ignisuti on 2010-06-10
> **lidex said:**
> You do have some mismatched alsa componeents. I would suggest uninstalling the backports and rebooting followed by a full alsa upgrade via the upgrade link in my sig.

Well, the uninstall, reboot, and then the full alsa upgrade ran without errors. Now I can't reboot.  :confused:

Some of the seemingly more important messages are as follows:
No filesystem could mount root
Kernal panic
Call Trace: Kernal_thread_helper+0x7/0x10

Please help!

---

### Post by ignisuti on 2010-06-10
Please don't leave me hanging. '

I'm going to reinstall Ubuntu (or just go back to Windows) here in about 30 minutes if I havn't heard of a way to fix this problem.

---

### Post by lidex on 2010-06-13
> **Jinger said:**
> Let's start seeing what version of Alsa you have.
Write in terminal this code:
```
dpkg -l | grep "alsa"

```

Would you mind posting here the results?

Very nice. I can use that! Thanks.

---

