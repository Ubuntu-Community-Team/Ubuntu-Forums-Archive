---
title: "Ubuntu 10.4 doesn't recognise sound card or onboard sound!"
date: 2010-09-23
forum: Multimedia Software
---

### Post by deafpanda on 2010-09-23
Hello!

My fresh install of Ubuntu 10.4 will not recognise either my Audiophile 2496 sound card or my on-board sound.  No devices are shown in sound preferences.  They do however appear when I do lspci.  I'm pretty new to Ubuntu.  Can anyone help me?

Thanks

---

### Post by cchhrriiss121212 on 2010-09-23
Hello,
The 2496 will not show up due to a bug with Pulse Audio [see here]("http://ubuntuforums.org/showthread.php?t=1578759") for a fix.
Could you post the output of aplay -l?

---

### Post by deafpanda on 2010-09-23
aplay -l gives:
> device_list:223: no soundcards found...

Thanks!

---

### Post by cchhrriiss121212 on 2010-09-23
Could you post what sound devices you have listed under lspci -v?

---

### Post by deafpanda on 2010-09-23
lspci gives:
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Ethernet Adapter
00:05.0 IDE interface: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)


---

### Post by deafpanda on 2010-09-23
The VIA technologies entry is the 2496, I think.

---

### Post by cchhrriiss121212 on 2010-09-23
> **deafpanda said:**
> The VIA technologies entry is the 2496, I think.
Yes thats right, but you need to put **lspci -v**, the -v is important as it displays extra details.

---

### Post by deafpanda on 2010-09-23
Thanks, here's the output of lspci -v:

> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8159
    Flags: bus master, medium devsel, latency 64
    Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64
    Kernel modules: sis-agp, amd64-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: faf00000-fbffffff
    Prefetchable memory behind bridge: e8000000-f3ffffff
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
    Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
    Subsystem: ASUSTeK Computer Inc. Device 8139
    Flags: bus master, medium devsel, latency 128
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_sis

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
    Subsystem: ASUSTeK Computer Inc. Device 810d
    Flags: bus master, medium devsel, latency 64, IRQ 11
    I/O ports at d800 [size=256]
    I/O ports at d400 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 8139
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at faefc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 8139
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at faefd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 8139
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at faefe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 8139
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at faeff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Ethernet Adapter
    Subsystem: ASUSTeK Computer Inc. Device 8139
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at faefbc00 (32-bit, non-prefetchable) [size=128]
    I/O ports at d000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: sis190
    Kernel modules: sis190

00:05.0 IDE interface: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8139
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at c800 [size=8]
    I/O ports at c400 [size=4]
    I/O ports at c000 [size=8]
    I/O ports at b800 [size=4]
    I/O ports at b400 [size=16]
    I/O ports at b000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: sata_sis
    Kernel modules: sata_sis

00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 808a
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at faefb000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at a800 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

00:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: VIA Technologies Inc. Device d634
    Flags: bus master, medium devsel, latency 64, IRQ 5
    I/O ports at a400 [size=32]
    I/O ports at a000 [size=16]
    I/O ports at 9800 [size=16]
    I/O ports at 9400 [size=64]
    Capabilities: <access denied>
    Kernel modules: snd-ice1712

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

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
    Subsystem: ASUSTeK Computer Inc. Device 403d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Expansion ROM at faff0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, rivafb, nouveau


Sorry it's so long!  Didn't know which bits I didn't need to show you...

THanks

---

### Post by cchhrriiss121212 on 2010-09-24
Thanks,
So the output for the both audio cards shows that the kernel module is not loaded. Normally this is done by default, so I don't know why this has happened, did you do an alternate install or something?

To get the module loaded, try this:
sudo modprobe snd-ice1712

If it works then try aplay -l again, and you should see your 24/96 listed.

---

### Post by LLMB0611 on 2010-09-24
hi.
i also have big sound problems in ubuntu 10.04 LTS.
i used to listen to music in exaile an if i opened a youtube video or any other video in chrome or firefox the sound just stoped working. it was noise that you couldn't listen to (sorry, i don't know how to explain that in english). then that started to happened when i was just listening to music in audacious an i changed to next song. it was really annoying so i tried to reinstall pulse, and now my sound card is not listed in system-preferences-sound-hardware. exaile,audacious or any other program works ok, it doesn't say that there is no sound card, but the sound just isn't there. the sound card is on my motherboard, i'm not sure what kind of sound card. i have dual boot and everything works ok in win, so it's not hardware related, because i was thinking about buying a new sound card. i have also my old ubuntu 9.10 on a small disk that i haven't cleaned and the sound works ok there.

---

### Post by LLMB0611 on 2010-09-24
aplay -l
[QUOTE=]aplay: device_list:223: no soundcards found...[/QUOTE]

lspci -v

[QUOTE=]02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: XFX Pine Group Inc. Device 2941
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at fbe7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device 81e7
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fbffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
[/QUOTE]

ok, now you have my sound card :P
what do i do now??

---

### Post by cchhrriiss121212 on 2010-09-24
Hi LLMB0611
You need to do the same as the OP, open a terminal and try:
sudo modprobe snd-hda-intel

Which should load the module and give you an aplay -l result. Further steps are shown [here]("http://ubuntuforums.org/showthread.php?t=205449"), you are at step 4.

---

### Post by LLMB0611 on 2010-09-24
thank you very much, i got my sound back. :-\"=D>

---

### Post by lkjoel on 2010-09-24
> **deafpanda said:**
> Hello!

My fresh install of Ubuntu 10.4 will not recognise either my Audiophile 2496 sound card or my on-board sound.  No devices are shown in sound preferences.  They do however appear when I do lspci.  I'm pretty new to Ubuntu.  Can anyone help me?

Thanks
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by LLMB0611 on 2010-09-25
i'm back. everything worked great, but after restart had no sound again :confused::confused::confused:
i had to do that 
[quote=]sudo modprobe snd-hda-intel[/quote]
in othe words, load the kernell again. why is that?? why won't it load?:confused::confused:
will i have to do that every time i start ubuntu? :confused:

---

### Post by cchhrriiss121212 on 2010-09-25
Did you check the link I posted? It has the further instructions on how to get it loaded every time, just do this:
sudo gedit /etc/modules
then paste snd-hda-intel. Save and reboot to test it out.

---

### Post by LLMB0611 on 2010-09-25
Sorry I was in a bit of a hurry so I didn't. but this helped now. thanks! ;)

---

