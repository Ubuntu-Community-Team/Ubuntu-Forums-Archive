---
title: "SB Audigy 2 no sound in 9.04"
date: 2009-05-02
forum: Multimedia Software
---

### Post by ciaovos on 2009-05-02
After a clean install of 9.04 (2.6.28-11-generic kernel), I do not have any sound. I added packages and played around quite a bit (following e.g. markbuntu's thread) but nothing has worked yet.

I know there are plenty of threads with this same theme, however, I have scoured them and tried everything I can think of. Now I wonder if in all my tinkering I messed something up. Can anyone help?

Some outputs:

~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
05:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)

~$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
Subsystem: Dell Device 01d1
Flags: bus master, fast devsel, latency 0
Capabilities: [e0] Vendor Specific Information <?>
Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: efd00000-efefffff
Prefetchable memory behind bridge: 00000000e0000000-00000000e7ffffff
Capabilities: [88] Subsystem: Intel Corporation Device 0000
Capabilities: [80] Power Management version 2
Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Capabilities: [a0] Express Root Port (Slot+), MSI 00
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Subsystem: Dell Device 01d1
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
Memory behind bridge: efc00000-efcfffff
Capabilities: [40] Express Root Port (Slot+), MSI 00
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
Capabilities: [a0] Power Management version 2
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
Capabilities: [40] Express Root Port (Slot+), MSI 00
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
Capabilities: [a0] Power Management version 2
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
I/O behind bridge: 0000c000-0000cfff
Memory behind bridge: ef700000-efbfffff
Capabilities: [40] Express Root Port (Slot+), MSI 00
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
Capabilities: [a0] Power Management version 2
Kernel driver in use: pcieport-driver
Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
Subsystem: Dell Device 01d1
Flags: bus master, medium devsel, latency 0, IRQ 21
I/O ports at ff80 [size=32]
Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
Subsystem: Dell Device 01d1
Flags: bus master, medium devsel, latency 0, IRQ 22
I/O ports at ff60 [size=32]
Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
Subsystem: Dell Device 01d1
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at ff40 [size=32]
Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
Subsystem: Dell Device 01d1
Flags: bus master, medium devsel, latency 0, IRQ 23
I/O ports at ff20 [size=32]
Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
Subsystem: Dell Device 01d1
Flags: bus master, medium devsel, latency 0, IRQ 21
Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
Capabilities: [50] Power Management version 2
Capabilities: [58] Debug port: BAR=1 offset=00a0
Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
I/O behind bridge: 0000b000-0000bfff
Memory behind bridge: ef600000-ef6fffff
Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
Flags: bus master, medium devsel, latency 0
Capabilities: [e0] Vendor Specific Information <?>
Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
Subsystem: Dell Device 01d1
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at ffa0 [size=16]
Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
Subsystem: Dell Device 01d1
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
I/O ports at fe00 [size=8]
I/O ports at fe10 [size=4]
I/O ports at fe20 [size=8]
I/O ports at fe30 [size=4]
I/O ports at fea0 [size=16]
Memory at efffbc00 (32-bit, non-prefetchable) [size=1K]
Capabilities: [70] Power Management version 2
Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
Subsystem: Dell Device 01d1
Flags: medium devsel, IRQ 10
I/O ports at ece0 [size=32]
Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
Subsystem: ATI Technologies Inc Device 0602
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at e0000000 (64-bit, prefetchable) [size=128M]
Memory at efde0000 (64-bit, non-prefetchable) [size=64K]
I/O ports at dc00 [size=256]
Expansion ROM at efe00000 [disabled] [size=128K]
Capabilities: [50] Power Management version 2
Capabilities: [58] Express Endpoint, MSI 00
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Kernel modules: radeonfb

01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
Subsystem: ATI Technologies Inc Device 0603
Flags: bus master, fast devsel, latency 0
Memory at efdf0000 (64-bit, non-prefetchable) [size=64K]
Capabilities: [50] Power Management version 2
Capabilities: [58] Express Endpoint, MSI 00

04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
Subsystem: Dell Device 01d1
Flags: bus master, fast devsel, latency 0, IRQ 2299
Memory at ef7e0000 (32-bit, non-prefetchable) [size=128K]
Memory at ef800000 (32-bit, non-prefetchable) [size=4M]
I/O ports at cce0 [size=32]
Capabilities: [c8] Power Management version 2
Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
Capabilities: [e0] Express Endpoint, MSI 00
Kernel driver in use: e1000e
Kernel modules: e1000e

05:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
Subsystem: Creative Labs Device 2006
Flags: bus master, medium devsel, latency 64, IRQ 16
I/O ports at b8c0 [size=64]
Capabilities: [dc] Power Management version 2
Kernel driver in use: EMU10K1_Audigy
Kernel modules: snd-emu10k1

05:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
Subsystem: Creative Labs Device 0040
Flags: bus master, medium devsel, latency 64
I/O ports at b8b8 [size=8]
Capabilities: [dc] Power Management version 2
Kernel driver in use: Emu10k1_gameport
Kernel modules: emu10k1-gp

05:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10)
Subsystem: Creative Labs Device 0010
Flags: bus master, medium devsel, latency 64, IRQ 17
Memory at ef6fa800 (32-bit, non-prefetchable) [size=2K]
Memory at ef6fc000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [44] Power Management version 2
Kernel driver in use: ohci1394
Kernel modules: firewire-ohci, ohci1394

05:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
Subsystem: Dell Device 1000
Flags: bus master, stepping, medium devsel, latency 64, IRQ 17
Memory at ef6fb000 (32-bit, non-prefetchable) [size=4K]
I/O ports at bc00 [size=256]
Capabilities: [80] Power Management version 2
Kernel driver in use: serial

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 [SB0350b]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy2 [Audigy 2 [SB0350b]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
Subdevices: 8/8
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
Subdevice #2: subdevice #2
Subdevice #3: subdevice #3
Subdevice #4: subdevice #4
Subdevice #5: subdevice #5
Subdevice #6: subdevice #6
Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 [SB0350b]], device 3: emu10k1 [Multichannel Playback]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 [SB0350b]], device 4: p16v [p16v]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

~$ lsmod | grep snd
snd_hda_intel 435636 2 
snd_emu10k1_synth 14336 0 
snd_emu10k1 144288 4 snd_emu10k1_synth
snd_ac97_codec 112292 1 snd_emu10k1
ac97_bus 9856 1 snd_ac97_codec
snd_pcm_oss 46336 0 
snd_mixer_oss 22656 1 snd_pcm_oss
snd_pcm 82948 4 snd_hda_intel,snd_emu10k1,snd_ac97_codec,snd_pcm_o ss
snd_page_alloc 16904 3 snd_hda_intel,snd_emu10k1,snd_pcm
snd_emux_synth 40832 1 snd_emu10k1_synth
snd_seq_virmidi 13440 1 snd_emux_synth
snd_seq_midi_emul 14592 1 snd_emux_synth
snd_hwdep 15108 2 snd_emu10k1,snd_emux_synth
snd_seq_dummy 10756 0 
snd_seq_oss 37760 0 
snd_seq_midi 14336 0 
snd_rawmidi 29696 3 snd_emu10k1,snd_seq_virmidi,snd_seq_midi
snd_seq_midi_event 15104 3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq 56880 9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,s nd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi _event
snd_timer 29704 3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device 14988 8 snd_emu10k1_synth,snd_emu10k1,snd_emux_synth,snd_s eq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_ seq
snd 62628 24 snd_hda_intel,snd_emu10k1,snd_ac97_codec,snd_pcm_o ss,snd_mixer_oss,snd_pcm,snd_emux_synth,snd_seq_vi rmidi,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,sn d_timer,snd_seq_device
soundcore 15200 1 snd
snd_util_mem 12288 2 snd_emu10k1,snd_emux_synth

~$ cat /proc/asound/cards
0 [Audigy2 ]: Audigy2 - Audigy 2 [SB0350b]
Audigy 2 [SB0350b] (rev.4, serial:0x20061102) at 0xb8c0, irq 16
1 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xefffc000 irq 16

~$ cat /proc/asound/modules
0 snd_emu10k1
1 snd_hda_intel

~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Audigy2 [Audigy 2 [SB0350b]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 [SB0350b]], device 1: emu10k1 mic [Mic Capture]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 [SB0350b]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 [SB0350b]], device 4: p16v [p16v]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 2/2
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1

~$ sudo lshw -C multimedia
[sudo] password for ciaovos: 
*-multimedia 
description: Audio device
product: 82801G (ICH7 Family) High Definition Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=HDA Intel latency=0 module=snd_hda_intel
*-multimedia
description: Multimedia audio controller
product: SB Audigy
vendor: Creative Labs
physical id: 4
bus info: pci@0000:05:04.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1

Some installed packages:
aconnectgui 
alsa-oss 
alsaplayer-alsa 
alsa-utils 
asoundconf-gtk 
gnome-alsamixer 
gstreamer0.10-alsa 
xmms2-plugin-alsa 
libasound2 
libasound2-plugins 
libesd-alsa0 
audacious-plugins-extra 
gstreamer0.10-pulseaudio 
padevchooser 
pavucontrol 
pulseaudio
vlc-plugin-pulse 
libsdl1.2debian-pulseaudio

---

### Post by kostkon on 2009-05-03
First of all, right click on your speaker and select *Open Volume Control*. Select the *Switches* tab and make sure that the *Digital/Analog* switch is disabled.

---

### Post by ciaovos on 2009-05-03
I have tried that, unfortunately, it was almost inaudible and what I could hear was very scratchy.

---

### Post by ciaovos on 2009-05-04
Apparently in my tinkering I did add two packages I should not have added: lib64asound2 and lib64asound2-plugins (I confused them somehow with lib32).  After completely removing these packages and rebooting, the sound works perfectly.  

My default sound card is set to PulseAudio, the Audigy Analog/Digital Output Jack is *un*checked (I looked in both Alsamixer and through the Volume Control >> Switches) ~ thanks kostkon!

:)

---

### Post by jrickard on 2009-05-11
Awww,,, come on.  Don't leave me hanging. 

I have exactly the same problem, and almost the same card.  Audigy 2 SB004. 

I entered all those commands, had essentially identical results.  And then you SOLVED it by removing two programs I don't have on my machine....

Does anybody actually know what the problem is?

Jack Rickard

---

### Post by ciaovos on 2009-05-12
> Awww,,,come on.  Don't leave me hanging.All I can suggest is to make sure Audio/Digital Output Jack is *un*checked in Alsamixer (make sure you have the tab of the correct sound card pulled up if you have more than one sound card) *and* through the Volume Control (if you don't see the Audio/Digital Output Jack in Volume Control you will need to select Preferences and then check the Audio/Digital Output Jack switch, but then make sure that once the switch appears in Volume Control that it is unchecked).  Make sure your Default Sound Card is set to "PulseAudio" and not Audigy.  If you change anything, reboot and retry.

Beyond that I cannot help much, but I understand how frustrating it is ... I spent about 25 hours trying to get it going.  I hope you have a better time.

---

### Post by Darth Buh on 2009-05-12
I had the same issues with an Audigy 2 card in Jaunty, mine showed up as a SB0240.  I had to enable the Digital/Analog Jack to make my sound work; but I had so many issues with recording from the microphone, I just wiped my entire machine and did a fresh install of Ibex.

A little tinkering, and everything works perfectly.

DB

---

### Post by ciaovos on 2009-05-13
Update

When I installed the following system updates I subsequently lost quality sound.  I can hear it, but it is again very scratchy.

```
Commit Log for Wed May 13 09:25:16 2009
Upgraded the following packages:
apturl (0.3.3ubuntu1) to 0.3.3ubuntu1.1
ekiga (3.2.0-0ubuntu1) to 3.2.0-0ubuntu2
gnome-about (1:2.26.1-0ubuntu1) to 1:2.26.1-0ubuntu2
gnome-desktop-data (1:2.26.1-0ubuntu1) to 1:2.26.1-0ubuntu2
libasound2 (1.0.19-0ubuntu1~ppa1) to 1.0.19-1ubuntu3~ppa1
libgnome-desktop-2-11 (1:2.26.1-0ubuntu1) to 1:2.26.1-0ubuntu2
libpulse-browse0 (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
libpulse-mainloop-glib0 (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
libpulse0 (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio-esound-compat (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio-module-gconf (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio-module-hal (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio-module-lirc (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio-module-lirc-dbg (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio-module-x11 (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio-module-zeroconf (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1
pulseaudio-utils (1:0.9.15-0ubuntu1~ppa4) to 1:0.9.15-1ubuntu2~ppa1

```So I am basically back to where I started and now less confident I should install upgrades when they become available.

---

### Post by ciaovos on 2009-05-15
kostkon, 

> First of all, right click on your speaker and select *Open Volume Control*. Select the *Switches* tab and make sure that the *Digital/Analog* switch is disabled. 	

I have since re-installed Jaunty.  The sound is still barely audible but very scratchy.  When I selected the Switches tab the Digital/Analog switch was already disabled in both Alsamixer and in the Volume Control.

Any more suggestions?

---

### Post by JoePits on 2009-05-18
> **Darth Buh said:**
> I had the same issues with an Audigy 2 card in Jaunty, mine showed up as a SB0240.  I had to enable the Digital/Analog Jack to make my sound work; but I had so many issues with recording from the microphone, I just wiped my entire machine and did a fresh install of Ibex.

A little tinkering, and everything works perfectly.

DB

that fixed it for me ! im on 8.04.  ):P

---

### Post by ciaovos on 2009-05-20
The only thing that has worked so far is opening Applications >> Sound & Video >> PulseAudio Volume Control and then selecting my HDA Intel - STAC92xx Analog as Default (after I went to the Playback tab and right clicked and then >> Move Stream >> HDA Intel) ~ which is to say I have temporarily given up trying to get the Audigy card working.

---

### Post by pr_ark on 2009-05-23
New user to Linux. I had the same problem and I fixed it like this. Hope it works for other too. 
I clicked on system---administration---update manager which showed that my system is up-to-date
Clicked on setting from there and on the updates tab checked the option pre-released updates(jaunty-proposed).
on ubuntu software tab made sure all the options except for the source code  are checked.
on third party software tab checked unsupported updates and both the archive options.
and clicked close.  This installed a bunch of updates .including the audigy stuff I guess. It asked for a reboot atleast 4 times. After each reboot I checked the sound and it was still not working(It did not do a computer reboot here) . I did a manual restart by selecting the system-shut down-restart computer option and tried the sound again and everything worked fine.
Hope this explanation will help someone.
Cheers

---

### Post by evilbluemako on 2009-06-03
I have just solved this problem in my particular instance (9.04 with Audigy 2)

 right-click the speaker icon to open volume control, select ¨switches¨ tab, and ENABLE ¨Audigy Analog / Digital Output Jack¨. 

 I have found many posts advising to disable this setting to fix various ¨no sound" problems.  Mine was disabled (unchecked) by default.  I have no idea what this setting does but in my instance it restored sound straight away - good luck!

---

### Post by Darth Buh on 2009-06-05
Yeah, that jack switch gave me audio output... I just couldn't get any audio input to function.

DB

---

### Post by m0rbidpercepti0ns on 2009-10-23
I have an Audigy 2 SB0240,it shows up in terminal,and i had LOTS of problems with it,finally checking the digital output box got me sound,with lots of crackling,and yesterday i installed the new updates for the Kernel from the regular system update..and now the sound doesnt work at all again,but i still get crackling,and i cant seem to fix it. Lots of people say raiding the PCM volume takes care of it..but it doesnt seem to affect anything for me.

---

### Post by markbuntu on 2009-10-23
I have a problem with my usb headset on Jaunty. It crackles if the pulseaudio volume control is not open, weird. So I keep it open and minimize it. You could try that.

---

### Post by xDezzx on 2010-02-14
Hey I know this is kind of a dead thread but I'm having the same problem right meow. Same card and everything, just wondering if you ever solved the problem; I could use some help.
Thanks

---

