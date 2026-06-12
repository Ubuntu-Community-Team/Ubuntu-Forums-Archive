---
title: "sound issue in jaunty"
date: 2009-10-27
forum: Multimedia Software
---

### Post by Eliot89 on 2009-10-27
I'm new to ubuntu and I'm having problems with my sound. I already completed the comprehensive sound guide without luck. Here's what I know so far:

the computer recognizes my sound card:

```
eliot89@smash:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


I checked the Audio Settings Management button in system->administration->services (attachment 1)


and none of the combinations of "default mixer tracks" (attachment 3) and "sound playback" devices for music and movies (attachment 2) give any sound when I hit test. 

everything is unmuted and turned all the way up using both the graphical controls as well as alsamixer inside of the terminal.

there is a possibility that the sound card or it's connection is bad but I don't know how to test that. any ideas?

---

### Post by Eliot89 on 2009-10-27
Just talked to the previous owner and they said that the sound card was fine.

---

### Post by Eliot89 on 2009-10-30
here is the output of the lspci -v | less command

```


00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-nvidia
        Kernel modules: nvidia-agp

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Device 1400
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Device 1400
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Device 1400
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Device 1400
        Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Device 1400
        Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
        Subsystem: Biostar Microtech Int'l Corp Device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Device 3400
        Flags: 66MHz, fast devsel, IRQ 3
        I/O ports at d000 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: nForce2_smbus
        Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
        Subsystem: Biostar Microtech Int'l Corp Device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at ef003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
        Subsystem: Biostar Microtech Int'l Corp Device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at ef004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ohci_hcd

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20)
        Subsystem: Biostar Microtech Int'l Corp Device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at ef005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
        Subsystem: Biostar Microtech Int'l Corp Device 2301
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at ef000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d400 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: forcedeth
        Kernel modules: forcedeth

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: Biostar Microtech Int'l Corp Device 8201
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at d800 [size=256]
        I/O ports at dc00 [size=128]
        Memory at ef001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: ee000000-eeffffff
        Kernel modules: shpchp

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Device f565:3400
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_amd

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: ec000000-edffffff
        Prefetchable memory behind bridge: e4000000-ebffffff
        Kernel modules: shpchp

01:07.0 Communication controller: Intel Corporation 536EP Data Fax Modem
        Subsystem: Intel Corporation Device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 3
        Memory at ee000000 (32-bit, non-prefetchable) [size=4M]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
        Subsystem: Biostar Microtech Int'l Corp Device 1400
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Memory at e8000000 (32-bit, prefetchable) [size=512K]
        [virtual] Expansion ROM at e8080000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb, rivafb


```

I'm not sure if there is anything wrong with that but just for kicks I unplugged what seemed to be my sound card (the card with the audio output) and typed in the same command and there wasn't any change in what the command line said. I'm at a real loss here.

---

### Post by Eliot89 on 2009-10-30
Oh and I also checked whether audio was enabled in bios and it is and I also made sure that the user privilege allowed me to use audio devices. I clicked yes but there wasn't any change.

---

