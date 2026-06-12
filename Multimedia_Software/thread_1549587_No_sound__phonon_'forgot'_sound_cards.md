---
title: "No sound / phonon 'forgot' sound cards"
date: 2010-08-10
forum: Multimedia Software
---

### Post by bluedalek on 2010-08-10
Hi all

I recently had a brain cramp and told Phonon to forget my sound card(s). I have an on-board card and I have installed an old-school Sound Blaster CT-4832.

I have followed the steps listed in the comprehensive sound trouble shooting, and still no luck!

```
gentle@Desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live! Value [CT4832]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Live [SB Live! Value [CT4832]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]                                                                                                                                                   
  Subdevices: 8/8                                                                                                                                                                                                                                  
  Subdevice #0: subdevice #0                                                                                                                                                                                                                       
  Subdevice #1: subdevice #1                                                                                                                                                                                                                       
  Subdevice #2: subdevice #2                                                                                                                                                                                                                       
  Subdevice #3: subdevice #3                                                                                                                                                                                                                       
  Subdevice #4: subdevice #4                                                                                                                                                                                                                       
  Subdevice #5: subdevice #5                                                                                                                                                                                                                       
  Subdevice #6: subdevice #6                                                                                                                                                                                                                       
  Subdevice #7: subdevice #7                                                                                                                                                                                                                       
card 1: Live [SB Live! Value [CT4832]], device 3: emu10k1 [Multichannel Playback]                                                                                                                                                                  
  Subdevices: 1/1                                                                                                                                                                                                                                  
  Subdevice #0: subdevice #0 
```

and

```
gentle@Desktop:~$ lspci -v                                                                                                                                                                                                                         
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)                                                                                                                                                            
        Subsystem: nVidia Corporation Device cb84                                                                                                                                                                                                  
        Flags: bus master, 66MHz, fast devsel, latency 0                                                                                                                                                                                           
        Capabilities: <access denied>                                                                                                                                                                                                              
                                                                                                                                                                                                                                                   
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
        Subsystem: nVidia Corporation Device cb84
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 2900 [size=64]
        I/O ports at 2d00 [size=64]
        I/O ports at 2e00 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: nForce2_smbus
        Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
        Subsystem: nVidia Corporation Device cb84
        Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at f9f80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
        Subsystem: nVidia Corporation Device cb84
        Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at f9f7f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at f9f7ec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at f9f7d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at f9f7e800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_amd
        Kernel modules: pata_amd

00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at f9f78000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: nVidia Corporation Device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        I/O ports at b480 [size=8]
        I/O ports at b400 [size=4]
        I/O ports at b080 [size=8]
        I/O ports at b000 [size=4]
        I/O ports at ac00 [size=16]
        Memory at f9f76000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fa000000-feafffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
        Flags: fast devsel
        Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
        Flags: fast devsel

01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs Device 8027
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1

01:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
        Subsystem: Creative Labs Device 0020
        Flags: bus master, medium devsel, latency 32
        I/O ports at c880 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: Emu10k1_gameport
        Kernel modules: emu10k1-gp

02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GS] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. Device 1330
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc00 [size=128]
        [virtual] Expansion ROM at fea80000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nvidiafb, nouveau

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 14)
        Subsystem: J & W Electronics Co., Ltd. Device 7150
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at e800 [size=256]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: sky2
        Kernel modules: sky2

```

Alsa Mixer sees the Sound Blaster, but not the on board card.
See the screen shots.

Any help would be appreciated!

---

### Post by ceterasvasile on 2011-03-03
I have a similar issue.
Can nobody give a hand to solve an issue, even after months from posting the question?

---

