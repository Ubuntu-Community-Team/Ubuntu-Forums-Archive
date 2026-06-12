---
title: "Yet another sound problem (VIA 8237)"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by swarog on 2006-08-18
Hi everybody!
I've just made an upgrade from Breezy to Dapper and now my sound is broken, i can hear it, but it sounds very strange. When gdm is loaded and asking for login/pass, i hear a series of short-time signals that sounds for 10 sec. or so. Xmms plays spotty sound in both alsa and oss, writing strange 'alsa mixer timed out' message to the console. Mplayer behaves the same way with audio and video streams writing this:
> 
alsa-play: xrun of at least 0.052 msecs. resetting stream 2.9% 0 0
alsa-space: xrun of at least 0.138 msecs. resetting stream2.8% 5 0

Same thing when played with -ao oss option except that no '... resetting stream ...' messages is written.
I've installed ubuntu-base and ubuntu-desktop as it's said in upgrade notes. The following sound modules are loaded in my system:
> $ lsmod|grep snd
snd_via82xx            28824  0
gameport               15496  1 snd_via82xx
snd_ac97_codec         93088  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_mpu401_uart         7808  1 snd_via82xx
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_rawmidi            25504  2 snd_mpu401_uart,snd_seq_midi
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55268  11 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd

And lspci shows the following:
> 0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
I'm not sure but it might be that something is wrong with interrupts, here is a part of /var/log/message:
> 
$ grep PCI /var/log/messages
Aug 19 01:23:53 localhost kernel: [17179570.540000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
Aug 19 01:23:53 localhost kernel: [17179570.544000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12)
Aug 19 01:23:53 localhost kernel: [17179570.544000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
Aug 19 01:23:53 localhost kernel: [17179570.544000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 01:23:53 localhost kernel: [17179570.544000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 01:23:53 localhost kernel: [17179570.544000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 01:23:53 localhost kernel: [17179570.544000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 01:23:53 localhost kernel: [17179570.544000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
Aug 19 01:23:53 localhost kernel: [17179570.544000] ACPI: PCI Interrupt Link [ALKA] (IRQs *20), disabled.
Aug 19 01:23:53 localhost kernel: [17179570.548000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
Aug 19 01:23:53 localhost kernel: [17179570.548000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
Aug 19 01:23:53 localhost kernel: [17179570.548000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
Aug 19 01:23:53 localhost kernel: [17179570.556000] PCI: Using ACPI for IRQ routing
Aug 19 01:23:53 localhost kernel: [17179570.556000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 19 01:23:53 localhost kernel: [17179570.584000] PCI: Bridge: 0000:00:01.0
Aug 19 01:23:53 localhost kernel: [17179570.584000] PCI: Bypassing VIA 8237 APIC De-Assert Message
Aug 19 01:23:53 localhost kernel: [17179570.992000] PCI0 USB3 USB4 USB5 USB6 USB7 LAN0 AC97 UAR1
Aug 19 01:23:53 localhost kernel: [17179572.920000] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
Aug 19 01:23:53 localhost kernel: [17179572.920000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Aug 19 01:23:53 localhost kernel: [17179572.920000] PCI: setting IRQ 11 as level-triggered
Aug 19 01:23:53 localhost kernel: [17179572.920000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 19 01:23:53 localhost kernel: [17179572.920000] PCI: VIA IRQ fixup for 0000:00:0f.0, from 255 to 11
Aug 19 01:23:53 localhost kernel: [17179576.240000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 19 01:23:53 localhost kernel: [17179576.348000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 19 01:23:53 localhost kernel: [17179576.452000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
Aug 19 01:23:53 localhost kernel: [17179576.452000] PCI: setting IRQ 10 as level-triggered
Aug 19 01:23:53 localhost kernel: [17179576.452000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Aug 19 01:23:53 localhost kernel: [17179576.556000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Aug 19 01:23:53 localhost kernel: [17179576.660000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Aug 19 01:23:53 localhost kernel: [17179576.660000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Aug 19 01:23:53 localhost kernel: [17179584.204000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Aug 19 01:23:53 localhost kernel: [17179584.220000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Aug 19 01:23:53 localhost kernel: [17179584.404000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 19 01:23:53 localhost kernel: [17179584.408000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 19 01:23:53 localhost kernel: [17179585.056000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 19 01:23:53 localhost kernel: [17179585.188000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug 19 01:23:53 localhost kernel: [17179585.364000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Aug 19 01:23:53 localhost kernel: [17179587.800000] Intel ISA PCIC probe: not found.
Aug 19 01:24:47 localhost kernel: [17179650.652000] ACPI: PCI interrupt for device 0000:00:10.4 disabled

And there is one strange thing: HDD LED blinks every 2 seconds, even if system is idle.
I've been struggling for 2 days trying to solve this problem, but still no results. So any help would be appreciated.

---

