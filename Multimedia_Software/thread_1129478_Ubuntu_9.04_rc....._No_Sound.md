---
title: "Ubuntu 9.04 rc..... No Sound"
date: 2009-04-18
forum: Multimedia Software
---

### Post by underdog512 on 2009-04-18
When I had intrepid on my system, my sound worked just fine.  I have just installed Ubuntu 9.04 RC and everything seems to be working fine except for sound.  I am not getting any output at all.  It looks like Ubuntu is detecting the both of my card. 



Here is the output for lspci 


```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
01:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
04:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

```


Here is the output for aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
adam@adam-desktop:~$ alsamixer

adam@adam-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 64
	Memory at dc000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-amd64
	Kernel modules: amd64-agp

00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
	Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: faa00000-feafffff
	Prefetchable memory behind bridge: b7f00000-d7efffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 2301
	I/O ports at e000 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at d880 [size=8]
	I/O ports at d800 [size=4]
	I/O ports at d480 [size=16]
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 81b5
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
	Subsystem: ASUSTeK Computer Inc. Device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at ec00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
	Subsystem: ASUSTeK Computer Inc. Device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at e480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
	Subsystem: ASUSTeK Computer Inc. Device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at e400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
	Subsystem: ASUSTeK Computer Inc. Device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 23
	I/O ports at e080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 81b5
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at febff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
	Subsystem: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
	Flags: medium devsel
	Capabilities: <access denied>
	Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
	Subsystem: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
	Flags: bus master, medium devsel, latency 128
	Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 64, IRQ 23
	I/O ports at e800 [size=256]
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine

00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=03, sec-latency=0
	Kernel modules: shpchp

00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa900000-fa9fffff
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
	Flags: bus master, fast devsel, latency 0
	Bus: primary=01, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

01:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
	Flags: bus master, fast devsel, latency 0
	Bus: primary=01, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

04:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at cc00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

04:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10)
	Subsystem: Creative Labs Device 0010
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at fa9ff800 (32-bit, non-prefetchable) [size=2K]
	Memory at fa9f8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

05:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
	Subsystem: eVga.com. Corp. Device a341
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at feae0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

adam@adam-desktop:~$ 
adam@adam-desktop:~$ alsamixer

adam@adam-desktop:~$ cls
bash: cls: command not found
adam@adam-desktop:~$ clr
bash: clr: command not found
adam@adam-desktop:~$ clear

adam@adam-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Royle on 2009-04-18
I'm having a the same problem with an Audigy 2 and Kubuntu 9.04.

---

### Post by underdog512 on 2009-04-18
by the way I have checked and nothing is muted.

---

### Post by underdog512 on 2009-04-18
I installed gnome-alsa mixer and found that "Audigy Analog/digital output jack" was unchecked.  I put a check in this and it is working fine now.  

I still think this may be a bug in 9.04.  The average user is not going to know to install gnome-alsa to get this working.  

I think I head over to Ubuntu Brainstorm and recommend gnome-alsa be added as the default volume control.

---

### Post by devosion on 2009-04-18
Thanks for the heads up on this. Im using ubuntu 9.04 and an audigy 2, and am experiencing the same problem. When I get home i'll try your fix.

---

### Post by rockstarrem on 2009-04-18
Same problem happens in 8.10, it's the Analog/Digital switch or whatever.

---

### Post by rothgar on 2009-04-19
> **underdog512 said:**
> I installed gnome-alsa mixer and found that "Audigy Analog/digital output jack" was unchecked.  I put a check in this and it is working fine now.  

I still think this may be a bug in 9.04.  The average user is not going to know to install gnome-alsa to get this working.  

I think I head over to Ubuntu Brainstorm and recommend gnome-alsa be added as the default volume control.
I appear to be having the same problem on my HP 8510p. I installed gnome-alsa mixer but when I start it i don't see any checkboxes. I just see the edit menu but when I click on "sound card properties" the window just closes and nothing happens.
Any other tips on where I should look to fix this?

---

### Post by sfainb on 2009-04-19
Same problem here. Sound worked fine in the previous version before I updated to 9.04rc. If anyone fixed this could you walk a newbie through what exactly you did?

My computer also recognizes the sound card.

---

### Post by devosion on 2009-04-19
After you install gnome-alsamixer from terminal with:

> sudo aptitude install gnome-alsamixer

Then click on your applications menu and click over to Sound & Video. Here you should find gnome alsa mixer. When the GUI pops up on the bottom of the window is the checkbox that says 'audigy/analog digital output' check this then try out your sound. You may also have to restart.

---

### Post by nbfkmunich on 2009-04-26
Please fix this problem - the average user does not know how to find and change these settings. This was the ONLY problem I experienced on a new install. Recently I reinstalled windows and it took me hours....

---

### Post by cversion7 on 2009-04-26
I just wanted to add in that I had the same issue with an Audigy 4 card on release version of 9.04 and found this post through a google search. I was able to resolve the issue very simply thanks to the info here, but it would have been nice to not have to go through this on a fresh install. Either way, I'm happy to have sound and yet again another problem solved by the community of ubuntuforums. :)

---

### Post by rhys_rhaven on 2009-04-28
Found this via google, same issue with an Audigy 2 ZS. Thanks much. gnome-aslamixer, check the box that says "I would actually like to output sound, as opposed to ...what?!" I would say bug.

---

### Post by a350z4me on 2009-04-29
I also just upgraded from 8.10 (Xubuntu) to 9.04 and am having sound problems.

Is anyone having problems getting their soundcard recognized? I also have an Audigy 2. It shows up when I use lspci -v, but does not show up when I use aplay -l.

---

### Post by ML07 on 2009-05-01
A newbie's perspective:

I'm experiencing the same problem after a fresh install of Ubuntu 9.04. I have an Audigy2 card. Installed gnome alsa mixer and checked analog/digital output box. Now I can play a song (wav only) for ~ 3 seconds before it loses audio output. Don't get me going on the fact that Ubuntu doesn't come preconfigured to play mp3 files. That's right; that rare file format called mp3.

As a disillusioned MS Windows user, I was hoping Ubuntu would provide me with a user friendly, plug and play experience that simply worked. Instead, I got this headache. Furthermore, my google searches in an attempt to get helpful instructions made it evident that linux is not ready for primetime or for an average user. Way too many hardware incompatibilities, syntax requirements, and way too much hassle.

Even MS Windows is vetted more thoroughly w.r.t. hardware compatibility. The audigy2 card is not legacy hardware.

If ubuntu releases a version that installs w/o the audio problems discussed in this thread, please let me know. As annoyed as I sound above, I really would like to use linux w/o headaches. Thx.

[EMAIL="walterhuntingwood@gmail.com"]walterhuntingwood@gmail.com[/EMAIL]

---

### Post by JFAlugod on 2009-05-14
Hi Guys,

I'm seeking help for the same: A audigy 2 zs not working at all.
I have tried everything in this thread and in what i could fing on the 'net.
Please help me.
This is my lspci output:

```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:0d.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0d.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0d.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)

```

And my aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Hope someone knows how to fix it :P

---

### Post by BrainStorms on 2009-07-07
For anyone researching this, try this post:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7574204](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=7574204)

Try plugging the speakers into the ***front panel*** sound jack (cabled from the board's J1 connector) -- that seems to work on these ZS cards.

---

### Post by BrainStorms on 2009-07-07
I just found out how to "fix" this...

* Right-click on the speaker icon in the toolbar and select "Open Volume Control".  
* From the pull-down at the top, select "Audigy 2 ZS [SB0353] (Alsa Mixer)".
* Select the "Switches" tab.
* Check the "Audigy Analog/Digital Output Jack" checkbox.

That should route the sound to the rear ports of the card.

Forum thread 843012 notes "Updates seem to reset this switch regularly so keep this in mind."

---

### Post by chosenbeans on 2009-08-05
> **BrainStorms said:**
> I just found out how to "fix" this...

* Right-click on the speaker icon in the toolbar and select "Open Volume Control".  
* From the pull-down at the top, select "Audigy 2 ZS [SB0353] (Alsa Mixer)".
* Select the "Switches" tab.
* Check the "Audigy Analog/Digital Output Jack" checkbox.

That should route the sound to the rear ports of the card.

Forum thread 843012 notes "Updates seem to reset this switch regularly so keep this in mind."

Just here to confirm this solution as a success. Thank you so much.

---

### Post by drbowen on 2009-08-16
I am using an HP 4200+ Media  Center PC
 Dual core AMD 64 processors
 Audigy 2 sound card
 Philips SPC1330NC/17 webcam and microphone combination.
 

 dmesg: The Audigy2 is discovered
 dmesg: The Philips Webcam is discovered
 lspci -v : 02:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04) 
 lsmod: lots of kernal modules are loading including  
 	snd 78920  23 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,
 	snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,
 	snd_hwdep,snd_seq,snd_timer,snd_seq_device 
 aplay -l lists lots of devices 
 **** List of PLAYBACK Hardware Devices **** 
 card 0: Audigy2 [Audigy 2 Platinum [SB0240P]], device 0: emu10k1 [ADC Capture/Standard PCM
 

 # amixer controls  lists lots of devices
 

 The modules appear to be loading in the correct order
 # cat /proc/asound/modules 
  0 snd_emu10k1 
  1 snd_usb_audio 
 

 #cat /proc/asound/Audigy2/emu10k1
 	shows lots of devices (224 for audigy and 2 for the P1330NC) including  
 		state.Audigy2
 		state.P1330NC
 

 I have read as much documentation as I can find.
 I read “**Comprehensive Sound Problem Solutions Guide”**
 I have unmuted and muted the alsamixer (several times out of boredom I guess) I am currently in the unmuted state.  I saved the settings: alsactl store 0
 

 I tried Gentoo (ALSA was fine but I couldn't get the webcam to work)
 I tried Ubuntu (The camera is fine but the sound won't work)
 I installed Debian (couldn't get ALSA or the webcam to work)
 Now I am back on Ubuntu with a clean fresh Jaunty Jackalope 9.0.4 on AMD 64
 and the camera is fine but the sound won't work.
 The microphone on the Philips webcam is working.  At lease the PulseAudio Applet shows a volume bar that jumps and up and down appropriately when I talk.
 

 The only sound I get out of my speakers is a pop when I turn the  
 

 Card: Audigy 2 Platinum [SB0240P]                                                                                                                         
 &#9474; Chip: SigmaTel STAC9721,23                                                                                                                                
 &#9474; View: [Playback] Capture  All                                                                                                                             
 &#9474; Item: Audigy Analog/Digital Output Jack
 

 Audigy Analog / Digital Output Jack on and off in alsamixer.  I have disenabled  this  Analog Output Jack per this thread:   [http://ubuntuforums.org/showthread.php?t=1120178&highlight=audigy](http://ubuntuforums.org/showthread.php?t=1120178&highlight=audigy)
I have turned this on and off and back on again in gnome-alsmixer.

 

 Still no sound.


Hoping somebody can relieve my frustration.


Sam Bowen

---

### Post by drbowen on 2009-08-16
I don't have a "* Right-click on the speaker icon in the toolbar and select "Open Volume Control"."

What I did do is I started sticking my speaker jack into every hole I could find.  I finally found one that worked.  It's not the same output jack I used before.  I would love to tell you which jack worked but there are only small symbols on the jacks that don't mean much to me.  At least I have sound from my speakers again.

Now I am trying to troubleshoot the webcam microphone.  Thanks for this thread.

Sam Bowen

---

### Post by yammer on 2009-08-23
I was having similar troubles to what other people listed:

Audigy 2 ZS, ubuntu 9.04 somehow recently caused sound to stop working.

I'm actually using the digital out from the back of my computer, so I would expect the "Audigy Analog/Digital Output Jack" to need to be on.

However, what I just discovered is that the "IEC958 Optical Raw" switch needs to be OFF for my digital output to be enabled.

I'm not sure why, but now things work, so I thought I'd just point out that messing with both of these switches seems to help.

---

