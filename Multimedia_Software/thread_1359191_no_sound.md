---
title: "no sound"
date: 2009-12-19
forum: Multimedia Software
---

### Post by azertyh on 2009-12-19
hi,
what's wrong with my setup? the sound works under windows xp. here some commands :

```
                                        lspci -v
    [LEFT]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX[/LEFT]
    [LEFT]    Subsystem: ASUSTeK Computer Inc. Device 82c9[/LEFT]
    [LEFT]    Flags: bus master, medium devsel, latency 64[/LEFT]
    [LEFT]    Kernel modules: sis-agp[/LEFT]
        [LEFT]00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge[/LEFT]
    [LEFT]    Flags: bus master, fast devsel, latency 0[/LEFT]
    [LEFT]    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0[/LEFT]
    [LEFT]    I/O behind bridge: 0000e000-0000efff[/LEFT]
    [LEFT]    Memory behind bridge: feb00000-febfffff[/LEFT]
    [LEFT]    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff[/LEFT]
    [LEFT]    Capabilities: <access denied>[/LEFT]
    [LEFT]    Kernel driver in use: pcieport-driver[/LEFT]
    [LEFT]    Kernel modules: shpchp[/LEFT]
        [LEFT]00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)[/LEFT]
    [LEFT]    Flags: bus master, medium devsel, latency 0[/LEFT]
        [LEFT]00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])[/LEFT]
    [LEFT]    Subsystem: ASUSTeK Computer Inc. Device 825e[/LEFT]
    [LEFT]    Flags: bus master, medium devsel, latency 128[/LEFT]
    [LEFT]    I/O ports at 01f0 [size=8][/LEFT]
    [LEFT]    I/O ports at 03f4 [size=1][/LEFT]
    [LEFT]    I/O ports at 0170 [size=8][/LEFT]
    [LEFT]    I/O ports at 0374 [size=1][/LEFT]
    [LEFT]    I/O ports at ffe0 [size=16][/LEFT]
    [LEFT]    Capabilities: <access denied>[/LEFT]
    [LEFT]    Kernel driver in use: pata_sis[/LEFT]
        [LEFT]00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)[/LEFT]
    [LEFT]    Subsystem: ASUSTeK Computer Inc. Device 825e[/LEFT]
    [LEFT]    Flags: bus master, medium devsel, latency 64, IRQ 20[/LEFT]
    [LEFT]    Memory at feaff000 (32-bit, non-prefetchable) [size=4K][/LEFT]
    [LEFT]    Kernel driver in use: ohci_hcd[/LEFT]
        [LEFT]00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)[/LEFT]
    [LEFT]    Subsystem: ASUSTeK Computer Inc. Device 825e[/LEFT]
    [LEFT]    Flags: bus master, medium devsel, latency 64, IRQ 21[/LEFT]
    [LEFT]    Memory at feafe000 (32-bit, non-prefetchable) [size=4K][/LEFT]
    [LEFT]    Kernel driver in use: ohci_hcd[/LEFT]
        [LEFT]00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)[/LEFT]
    [LEFT]    Subsystem: ASUSTeK Computer Inc. Device 825e[/LEFT]
    [LEFT]    Flags: bus master, medium devsel, latency 64, IRQ 22[/LEFT]
    [LEFT]    Memory at feafd000 (32-bit, non-prefetchable) [size=4K][/LEFT]
    [LEFT]    Capabilities: <access denied>[/LEFT]
    [LEFT]    Kernel driver in use: ehci_hcd[/LEFT]
        [LEFT]00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)[/LEFT]
    [LEFT]    Subsystem: ASUSTeK Computer Inc. Device 825e[/LEFT]
    [LEFT]    Flags: bus master, medium devsel, latency 0, IRQ 19[/LEFT]
    [LEFT]    Memory at feafcc00 (32-bit, non-prefetchable) [size=128][/LEFT]
    [LEFT]    I/O ports at dc00 [size=128][/LEFT]
    [LEFT]    Capabilities: <access denied>[/LEFT]
    [LEFT]    Kernel driver in use: sis190[/LEFT]
    [LEFT]    Kernel modules: sis190[/LEFT]
        [LEFT]00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) (prog-if 85 [Master SecO PriO])[/LEFT]
    [LEFT]    Subsystem: ASUSTeK Computer Inc. Device 825e[/LEFT]
    [LEFT]    Flags: bus master, medium devsel, latency 64, IRQ 17[/LEFT]
    [LEFT]    I/O ports at d800 [size=8][/LEFT]
    [LEFT]    I/O ports at d400 [size=4][/LEFT]
    [LEFT]    I/O ports at d000 [size=8][/LEFT]
    [LEFT]    I/O ports at cc00 [size=4][/LEFT]
    [LEFT]    I/O ports at c800 [size=16][/LEFT]
    [LEFT]    I/O ports at c400 [size=128][/LEFT]
    [LEFT]    Capabilities: <access denied>[/LEFT]
    [LEFT]    Kernel driver in use: sata_sis[/LEFT]
        [LEFT]00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge[/LEFT]
    [LEFT]    Flags: bus master, fast devsel, latency 0[/LEFT]
    [LEFT]    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0[/LEFT]
    [LEFT]    Capabilities: <access denied>[/LEFT]
    [LEFT]    Kernel driver in use: pcieport-driver[/LEFT]
    [LEFT]    Kernel modules: shpchp[/LEFT]
        [LEFT]00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge[/LEFT]
    [LEFT]    Flags: bus master, fast devsel, latency 0[/LEFT]
    [LEFT]    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0[/LEFT]
    [LEFT]    Capabilities: <access denied>[/LEFT]
    [LEFT]    Kernel driver in use: pcieport-driver[/LEFT]
    [LEFT]    Kernel modules: shpchp[/LEFT]
        [LEFT]**00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller**[/LEFT]
    [LEFT]**    Subsystem: ASUSTeK Computer Inc. Device 8290**[/LEFT]
    [LEFT]**    Flags: bus master, medium devsel, latency 0, IRQ 18**[/LEFT]
    [LEFT]**    Memory at feaf4000 (32-bit, non-prefetchable) [size=16K]**[/LEFT]
    [LEFT]**    Capabilities: <access denied>**[/LEFT]
    [LEFT]**    Kernel driver in use: HDA Intel**[/LEFT]
    [LEFT]**    Kernel modules: snd-hda-intel**[/LEFT]
        [LEFT]01:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650][/LEFT]
    [LEFT]    Subsystem: PC Partner Limited Device e930[/LEFT]
    [LEFT]    Flags: bus master, fast devsel, latency 0, IRQ 16[/LEFT]
    [LEFT]    Memory at d0000000 (64-bit, prefetchable) [size=256M][/LEFT]
    [LEFT]    Memory at febf0000 (64-bit, non-prefetchable) [size=64K][/LEFT]
    [LEFT]    I/O ports at ec00 [size=256][/LEFT]
    [LEFT]    Expansion ROM at febc0000 [disabled] [size=128K][/LEFT]
    [LEFT]    Capabilities: <access denied>[/LEFT]
    [LEFT]    Kernel modules: radeon[/LEFT]
        [LEFT]**01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]**[/LEFT]
    [LEFT]**    Subsystem: PC Partner Limited Device aa38**[/LEFT]
    [LEFT]**    Flags: bus master, fast devsel, latency 0, IRQ 16**[/LEFT]
    [LEFT]**    Memory at febec000 (64-bit, non-prefetchable) [size=16K]**[/LEFT]
    [LEFT]**    Capabilities: <access denied>**[/LEFT]
    [LEFT]**    Kernel driver in use: HDA Intel**[/LEFT]
    [LEFT]**    Kernel modules: snd-hda-intel**[/LEFT]
   
  
``````
                                        aplay -l
    [LEFT]**** Liste des PLAYBACK périphériques ****[/LEFT]
    [LEFT]carte  0: SIS966 [HDA SIS966], périphérique 0 : ALC662 rev1 Analog [ALC662 rev1 Analog][/LEFT]
    [LEFT]  Sous-périphériques: 0/1[/LEFT]
    [LEFT]  Sous-périphérique: #0: subdevice #0[/LEFT]
    [LEFT]carte  0: SIS966 [HDA SIS966], périphérique 1 : ALC662 rev1 Digital [ALC662 rev1 Digital][/LEFT]
    [LEFT]  Sous-périphériques: 1/1[/LEFT]
    [LEFT]  Sous-périphérique: #0: subdevice #0[/LEFT]
    [LEFT]carte  1: HDMI [HDA ATI HDMI], périphérique 3 : ATI HDMI [ATI HDMI][/LEFT]
    [LEFT]  Sous-périphériques: 1/1[/LEFT]
    [LEFT]  Sous-périphérique: #0: subdevice #0[/LEFT]
   
  
``````
                                        cat /proc/asound/modules
    [LEFT] 0 snd_hda_intel[/LEFT]
    [LEFT] 1 snd_hda_intel[/LEFT]
   
  
```                                       [FONT=FreeSerif]i dont know if it can help but i read in the motherboard user guide, at specifications summary :[/FONT]
    [FONT=FreeSerif]audio : realtek alc 662 6-channel high definition audio codec[/FONT]
    [FONT=FreeSerif]    support jack-detect and spidf-out interface[/FONT]
    
    [FONT=FreeSerif]i type alsamixer on terminal and i see :[/FONT]
    [FONT=FreeSerif]card : HDA SIS966[/FONT]
    [LEFT][FONT=FreeSerif]chip : Realtek ALC662 rev1[/FONT][/LEFT]
    [LEFT][FONT=FreeSerif]view : [Playback] Capture all

[/FONT][/LEFT]
        [LEFT][FONT=FreeSerif]and when i click on the volume button, i can choose the sound card. my choice are :[/FONT][/LEFT]
    [LEFT][FONT=FreeSerif]Realtek ALC662 rev1 (OSS Mixer)[/FONT][/LEFT]
    [LEFT][FONT=FreeSerif]HDA SIS966 (Alsa mixer)[/FONT][/LEFT]
    [LEFT][FONT=FreeSerif]HDA ATI HDMI (Alsa mixer)[/FONT][/LEFT]
    [LEFT][FONT=FreeSerif]which one i must select? i have already chosen all the three but i have not yet the sound.[/FONT]


[FONT=FreeSerif]thanks for your advice.
[/FONT][/LEFT]

---

### Post by Tricity on 2009-12-19
Looks like your Alsa system recognizes the sound card all right.
If you look at the mixer (Alsa), is there anything muted or the sound level at zero?

Does the device /dev/dsp exist?
Are you a member of the group "audio"? (check /etc/group)

Can you send something directly to the sound device, like

$ cat /var/log/kern.log > /dev/dsp

which you should hear as a scratching noise.

---

