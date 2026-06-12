---
title: "No sound over HDMI (Nvidia videocard + integrated audio)"
date: 2010-10-27
forum: Multimedia Software
---

### Post by hinkus on 2010-10-27
Hello everyone.

Here are my specs:
Ubuntu 10.10 x64 Server
Motherboard: Asus M4A89GTD Pro/USB3 890GX
Graphics: MSI GeForce 9 Series 9800GT 256-bit 1GB GDDR3 PCIE16 (N9800GT-MD1G/PWM)


My problem is with dedicated graphics. When I use integrated ATI chip, everything works as it should (Catalyst installed): I'm able to choose HDMI output in Sound settings. But I really want to use a dedicated NVIDIA video. It has an option to pass audio (S/PDIF out) from motherboard through HDMI. It works perfectly in Windows 7. I just set HDMI as the default device and nothing else. But I can't get it to work in Ubuntu, no matter what I try.:(

The problem seems to be that with NVIDIA installed, the system can't find the HDMI device anymore.

Here are my **default** (and **working**) system settings (without dedicated nvidia card):

```
# uname -r
2.6.35-22-server

# cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC892

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

# cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe4f8000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe6e8000 irq 19

# cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control
  9: [ 1- 3]: digital audio playback
 10: [ 1- 0]: hardware dependent
 11: [ 1]   : control

# cat /proc/asound/oss-devices
cat: /proc/asound/oss-devices: No such file or directory

# cat /proc/asound/timers
G0: system timer : 10000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P1-3-0: PCM playback 1-3-0 : SLAVE

# cat /proc/asound/pcm
00-00: ALC892 Analog : ALC892 Analog : playback 1 : capture 1
00-01: ALC892 Digital : ALC892 Digital : playback 1
01-03: ATI HDMI : ATI HDMI : playback 1

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# lspci -v
(relevant parts only)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: ASUSTeK Computer Inc. Device 8410
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe4f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4290] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8454
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at b000 [size=256]
	Memory at fe6f0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fe500000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
	Subsystem: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fe6e8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

Here are the # alsamixer output and info from Catalyst Control Center (just in case):

[[img]http://thumb.phyrefile.com/h/hi/hinkus/2010/10/27/300/alsamixer_ati.png[/img]](http://www.phyrefile.com/image/view/KicVurItgU6ajcLf) [[img]http://thumb.phyrefile.com/h/hi/hinkus/2010/10/27/300/catalyst__control_center.png[/img]](http://www.phyrefile.com/image/view/OtcWklfuVaaICNIh)


When I install the NVIDIA card, I don't have any audio over HDMI. Analog works though.

Here are the system specs with **nvidia** installed (**no hdmi**):
```
# uname -r
2.6.35-22-server

# cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC892

# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

# cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf9ff8000 irq 16

# cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control

# cat /proc/asound/oss-devices
cat: /proc/asound/oss-devices: No such file or directory

# cat /proc/asound/timers
G0: system timer : 10000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE

# cat /proc/asound/pcm
00-00: ALC892 Analog : ALC892 Analog : playback 1 : capture 1
00-01: ALC892 Digital : ALC892 Digital : playback 1

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# lspci -v
(relevant parts only)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: ASUSTeK Computer Inc. Device 8410
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 1861
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at fe6e0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidia-current, nouveau, nvidiafb
```

And again, the # alsamixer output (identical to default configuration) and NVIDIA X Server info:

[[img]http://thumb.phyrefile.com/h/hi/hinkus/2010/10/27/300/alsamixer_nvidia.png[/img]](http://www.phyrefile.com/image/view/hvZTzGRgKVMDNMpa) [[img]http://thumb.phyrefile.com/h/hi/hinkus/2010/10/27/300/NVIDIA_X_server_settings_a.png[/img]](http://www.phyrefile.com/image/view/lzB6CHoQtElpkh7v)


How should I proceed? What should I do to get the S/PDIF output working with nvidia video card? I have googled, used this forum, tried different solutions and suggestions I could find, but nothing helped me. I have re-installed my system multiple times, tried Ubuntu 10.04, nothing. 

I hope I'm missing something very obvious here, and that someone is able to guide me through it. Can't really believe that it's not possible to send audio over HDMI with dedicated card in Ubuntu.

---

### Post by hinkus on 2010-10-29
Any ideas?

---

### Post by cavalier911 on 2010-10-29
I don't see the ATI video in lspci -v with nvidia installed.

_Disable this:_
```
01:05.0 VGA compatible controller: **ATI Technologies Inc RS880 [Radeon HD 4290**] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8454
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at b000 [size=256]
	Memory at fe6f0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fe500000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon
```
_May disable this:_
```
01:05.1 Audio device: **ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]**
	Subsystem: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fe6e8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

If you disabled the integrated ATI video in the motherboards bios enable it.

---

### Post by bsmith1051 on 2010-10-29
Why did you want the Nvidia 9800GT, gaming?  

P.S. I have no suggestions, I was just searching for clues as to whether or not the ATI 4200 works in Ubuntu, e.g. audio-out over HDMI.  You seem to be saying that it does?

---

### Post by hinkus on 2010-11-01
Thanks for your answers..

> **cavalier911 said:**
> I don't see the ATI video in lspci -v with nvidia installed.

_Disable this:_
```
01:05.0 VGA compatible controller: **ATI Technologies Inc RS880 [Radeon HD 4290**] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8454
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at b000 [size=256]
	Memory at fe6f0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fe500000 (32-bit, non-prefetchable) [size=1M]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon
```
_May disable this:_
```
01:05.1 Audio device: **ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]**
	Subsystem: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fe6e8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

If you disabled the integrated ATI video in the motherboards bios enable it.

How should I disable those? About BIOS, I haven't changed anything in there when I've switched graphics. I simply delete xorg.conf and that allows me to log into gnome-desktop. However, there is an option in the bios to select S/PDIF out (HDMI or SPDIF). I've tried both ways, only HDMI works.



> **bsmith1051 said:**
> Why did you want the Nvidia 9800GT, gaming?  

P.S. I have no suggestions, I was just searching for clues as to whether or not the ATI 4200 works in Ubuntu, e.g. audio-out over HDMI.  You seem to be saying that it does?

I can't believe it doesn't work, still no proof it does. At least in my case. I bought the dedicated nvidia to boost graphics and yes, also to dual-boot to windows for occasional gaming.



I've messed around quite a bit but I can't get # aplay -l to show HDMI device with Nvidia installed. It drives me mad.:mad:

---

### Post by captaintrav on 2010-11-01
That Nvidia card will never show up as an HDMI audio device because it doesn't have one.  The Nvidia card just piggybacks the SPDIF output onto the HDMI cable - I take it you have a cable that connects the card to the SPDIF header on the motherboard?

There might show up an HDMI audio device in Windows because of driver trickery, but there isn't one, not with that card.  Cards that ACTUALLY have an HDMI audio device are most ATi cards and newer NVidia cards.   Nvidia didn't really help themselves here because the 9xxx series are just warmed over 8xxx cards, that's why the features are lacking.

The real issue might be pulseaudio, can you select the "ALC892 Digital" as the output?  If you can't, you might have a similar problem to me where pulseaudio is ignoring some devices, because, well, it sucks.

Mine, to get the HDMI working, I have to manually get pulseaudio to use the right alsa device.  Since you have the digital output of the on-board sound as device 1 of card 0, try adding this to /etc/pulse/default.pa

> load-module module-alsa-sink device=hw:0,1

---

