---
title: "Sound Card Stopped Working"
date: 2009-10-23
forum: Multimedia Software
---

### Post by Man with Hat on 2009-10-23
Hi, I'm still somewhat new to Ubuntu.

I had my sound card (creative Xfi) working just fine and doing its job. I had a go at Freedoom and as my screen saver decided to take control of my screen (wouldn't mind knowing how to stop that either without having to move screensaver slider to over an hour). My whole keyboard and mouse get hijacked, so I pressed Ctrl+Alt+f1 as I read that somewhere expecting to make a kill command. I couldn't do that and found myself unable to get out of that screen. I pressed the reboot button on the computer and when it had booted, I had no sound. 

When I go to system>preferences>sound, my driver now says:

**Creative ALSA Driver X-Fi WaveOut/WaveIn (ALSA) (not connected)**

I can't seem to find any solutions that make sense. Any help? Please....

---

### Post by Man with Hat on 2009-10-23
Oh and I'm using  Ubuntu 9.04 - Jaunty Jackalope

---

### Post by Lord_ on 2009-10-23
What do you get when you do an `lspci -v` ?  it should tell you what you have onboard

---

### Post by Man with Hat on 2009-10-23
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: 66MHz, fast devsel, IRQ 5
    I/O ports at e400 [size=32]
    I/O ports at 4c00 [size=64]
    I/O ports at 4c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at d5004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at feb00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 812a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 12
    I/O ports at dc00 [size=256]
    I/O ports at e000 [size=256]
    Memory at d5003000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. (Wrong ID) Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at f000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at d800 [size=16]
    Memory at d5002000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 815a
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at c400 [size=16]
    Memory at d5001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=128
    I/O behind bridge: 00008000-00009fff
    Memory behind bridge: d3000000-d4ffffff
    Prefetchable memory behind bridge: 50000000-500fffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
    Subsystem: ASUSTeK Computer Inc. Device 8141
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at d5000000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b000 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: d0000000-d2ffffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
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

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)
    Subsystem: XFX Pine Group Inc. Device 2180
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d1000000 (64-bit, non-prefetchable) [size=16M]
    I/O ports at a000 [size=128]
    [virtual] Expansion ROM at d2000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

[B]05:07.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 0021
    Flags: bus master, medium devsel, latency 32, IRQ 3
    I/O ports at 8000 [size=32]
    Memory at d4200000 (64-bit, non-prefetchable) [size=2M]
    Memory at d4000000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>[/B]

05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8167
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at 8400 [size=8]
    I/O ports at 8800 [size=4]
    I/O ports at 8c00 [size=8]
    I/O ports at 9000 [size=4]
    I/O ports at 9400 [size=16]
    Memory at d4408000 (32-bit, non-prefetchable) [size=1K]
    [virtual] Expansion ROM at 50000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: sata_sil

05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 808b
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at d4409000 (32-bit, non-prefetchable) [size=2K]
    Memory at d4400000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
    Subsystem: ASUSTeK Computer Inc. Device 811a
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at d4404000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at 9800 [size=256]
    [virtual] Expansion ROM at 50080000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: skge
    Kernel modules: skge

---

### Post by Man with Hat on 2009-10-24
Never mind, all fixed now. Worked it out

---

### Post by TimJ on 2009-10-25
Glad you got it fixed, would you mind saying how? I've got the same problem and you could help me short circuit working out the solution.

---

### Post by Man with Hat on 2009-10-25
I first disabled the onboard sound in BIOS (which probably did nothing, but seemed to help other people). Then I followed this guide
[http://www.moobash.com/Blog/?p=611](http://www.moobash.com/Blog/?p=611)
to install the ALSA drivers again. They are the same as the ones I got from creative (but seem a little more sophisticated). I had trouble with this where I was getting a message about the file not existing. If you get this, I got around it by unpacking the file in the GUI (just click on it and press extract) and letting TAB auto finish the command for me. The file name was a tiny bit different to the guide (it didn't have "snapshot" in it)

Hope that helps

---

### Post by Man with Hat on 2009-10-25
Just thought I'd add too, that when you type "lspci -v" into terminal and you can see your sound card there (like in my thread) but the drivers state "not connected" you really just need to re-install your driver. If your sound card isn't shown there, then I'd say your problem is more likely something else.

---

### Post by TimJ on 2009-10-25
Thanks, problem solved here too using [this thread]("http://ubuntuforums.org/showthread.php?t=870001") when I remembered I haven't yet as I haven't upgraded to 9.10 yet.

---

### Post by Man with Hat on 2009-10-25
No worries

---

