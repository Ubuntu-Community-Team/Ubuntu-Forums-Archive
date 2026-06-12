---
title: "Acer 5570Z No Sound from headphone jack"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by JacksSmolderingServer on 2007-07-08
Hi,

Helping a friend tackle a rather perplexing issue here. Trying to get an Intel HDA device to perform as designed. We get sound from the laptop speakers, but none from the headphone jack. NOTE: This did work properly in Edgy. No clue as to what could have changed, other than kernels...

think this may be some kind of IRQ issue (see dmesg output below)

Here's whats been tried so far, (to avoid any redundancy)

1.) [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) - Now using latest alsa drivers, etc as the howto suggests, and from the uboto response in #ubuntu IRC channel

2.) Various slider/ switch settings in both alsamixer and gnome alsa mixer

3.) added "options snd-intel-hda model=3stack" to /etc/modprobe.d/alsa-base (tried also: auto, and other various models, not sure which model i need to put here, as the lspci output is vague)

4.) alsaconf and dpkg-reconfigure alsa-source to try and get this back to "stock"

Thats a generalization of the effort, but I think I have covered the steps taken so far.

here is some output stuff for peeps to peruse as well.

lspci -v |grep Audio

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0110
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

 lsmod |grep snd
snd_hda_intel         244632  3
snd_pcm_oss            44672  0
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  3 snd_hda_intel,snd_pcm_oss
snd_seq_oss            35200  0
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56324  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm


wally@beelzebubba:~$ grep 00:1b.0 /var/log/messages
Jul  5 02:48:26 beelzebubba kernel: [   19.388000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  5 07:37:33 beelzebubba kernel: [   19.264000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  6 09:38:41 beelzebubba kernel: [   19.416000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  7 00:25:49 beelzebubba kernel: [   19.364000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  7 03:24:40 beelzebubba kernel: [   19.372000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  7 17:09:06 beelzebubba kernel: [   19.568000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  7 22:33:08 beelzebubba kernel: [   49.480000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  7 23:35:22 beelzebubba kernel: [   19.664000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 03:02:47 beelzebubba kernel: [   19.456000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 03:56:14 beelzebubba kernel: [   19.428000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 04:11:31 beelzebubba kernel: [   19.460000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 13:57:42 beelzebubba kernel: [   19.736000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 14:01:29 beelzebubba kernel: [   20.448000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 14:09:53 beelzebubba kernel: [   19.528000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 14:28:14 beelzebubba kernel: [   19.456000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 14:46:58 beelzebubba kernel: [   19.480000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 15:45:36 beelzebubba kernel: [   19.688000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 16:24:05 beelzebubba kernel: [   19.732000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 16:27:37 beelzebubba kernel: [  237.752000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Jul  8 16:28:52 beelzebubba kernel: [  312.868000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 16:33:15 beelzebubba kernel: [  576.420000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Jul  8 16:33:23 beelzebubba kernel: [  583.912000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 16:35:35 beelzebubba kernel: [   19.552000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Jul  8 16:47:49 beelzebubba kernel: [   19.776000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22

I can post more upon request. Please, if anyone has some insight as to what i may have missed, enlighten me, I am trying to avoid anything involving the W word.

S

---

