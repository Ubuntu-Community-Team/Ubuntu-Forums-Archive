---
title: "No sound after first boot - works after reboot"
date: 2012-09-29
forum: Multimedia Software
---

### Post by mala88 on 2012-09-29
Hi,

My sound does not work when I first turn on my computer. It works perfectly after I reboot.

I ran the alsa info script and I think the problem is related to the last entry in the dmesg output. Any ideas on why this only happens on the initial boot and goes away on subsequent reboots?

thanks!

Initial boot - no sound
[http://www.alsa-project.org/db/?f=75152cc049be2c121eab64d9fe580876910acd08 ]("http://www.alsa-project.org/db/?f=75152cc049be2c121eab64d9fe580876910acd08")


Second boot  - sound works
[http://www.alsa-project.org/db/?f=9b8f1a1f93d742ff13f198a8f04f410d55940dcd]("http://www.alsa-project.org/db/?f=9b8f1a1f93d742ff13f198a8f04f410d55940dcd")


!!ALSA/HDA dmesg
!!--------------

[    0.000000] DMI 2.5 present.
[    0.000000] DMI: NVIDIA MCP73   /NF77-HDMI, BIOS 6.00 PG 11/26/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
--
[   14.086098] IR LIRC bridge handler initialized
[   14.086795] snd_hda_intel 0000:00:09.0: power state changed by ACPI to D0
[   14.086801] snd_hda_intel 0000:00:09.0: power state changed by ACPI to D0
[   14.086970] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   14.086992] snd_hda_intel 0000:00:09.0: PCI INT A -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[   14.086996] hda_intel: Disabling MSI
[   14.087042] snd_hda_intel 0000:00:09.0: setting latency timer to 64
[   14.114230] hda-intel: no codecs found!
[   14.114287] snd_hda_intel 0000:00:09.0: PCI INT A disabled
[   14.114490] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   14.114496] snd_hda_intel 0000:02:00.1: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[   14.114500] hda_intel: Disabling MSI
[   14.114523] snd_hda_intel 0000:02:00.1: setting latency timer to 64
[   14.229088] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
--
[   14.761924] init: alsa-restore main process (1065) terminated with status 19
[   14.964023] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   14.988043] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   15.012052] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[   15.036063] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   15.036189] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:0b.0/0000:02:00.1/sound/card0/input6
[   15.036320] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:0b.0/0000:02:00.1/sound/card0/input7
[   15.036415] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:0b.0/0000:02:00.1/sound/card0/input8
[   15.036509] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0b.0/0000:02:00.1/sound/card0/input9
[   15.037081] nvidia 0000:02:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
--
[   17.107549] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   17.645554] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   17.652025] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[   17.667735] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   17.672025] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[   18.440012] HDMI: detected monitor Panasonic-TV
[   18.440015]  at connection type HDMI
[   18.440019] HDMI: available speakers: FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
[   18.440024] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16
[   27.664016] eth1: no IPv6 routers present
[COLOR="Red"][   38.065064] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.[/COLOR]

---

### Post by ftella on 2013-05-28
I have the same problem. It would be great to learn the solution.

---

### Post by erik8 on 2014-04-09
I'm also having the same problem, sound works after reboot. I've attached the dmesg output.

[http://www.alsa-project.org/db/?f=4dbb613d3da34e5267655299e7bed5012edf94dc](http://www.alsa-project.org/db/?f=4dbb613d3da34e5267655299e7bed5012edf94dc)

[ATTACH]251864[/ATTACH]

---

