---
title: "no Sound in ubuntu inbuilt sound blaster 24bit G1795X motherboard"
date: 2008-09-12
forum: Multimedia Software
---

### Post by fanaticx on 2008-09-12
i am using Ubuntu 8.04 hardy heron,
intel GA-G1795X motherboard its inbuilt 24bit sound blaster,

i could not get any sound from it, having only 3 speakers, one main two sides, and a razer keyboard which has audio input for me to plug in.

i turned on almost everything even 100 volume for all at alsamixer on cli.

i have the motherboard driver for the sound blaster buts its in exe(windows) and i don't know if you can run and install on linux.

on vista and xp i had no problems.

_**lspci**_
> 00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GTX] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
04:05.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:06.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
04:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

fanaticx@fanaticx-Linux:~$ lsmod | grep snd
snd_seq_dummy 4996 0
snd_ca0106 36320 1
snd_ac97_codec 101156 1 snd_ca0106
snd_seq_oss 35456 0
snd_pcm_oss 42528 0
snd_mixer_oss 18048 2 snd_pcm_oss
snd_seq_midi 9504 0
snd_pcm 78852 3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_rawmidi 25888 2 snd_ca0106,snd_seq_midi
snd_seq_midi_event 8576 2 snd_seq_oss,snd_seq_midi
snd_seq 54096 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac97_bus 3200 1 snd_ac97_codec
snd_timer 24964 2 snd_pcm,snd_seq
snd_seq_device 9612 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 57124 11 snd_seq_dummy,snd_ca0106,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,sn d_seq,snd_timer,snd_seq_device
soundcore 8800 2 snd
snd_page_alloc 11656 2 snd_ca0106,snd_pcm

[B][U]
aplay -L[/U][/B]
> fanaticx@fanaticx-Linux:~$ aplay -L
front:CARD=CA0106,DEV=0
CA0106, CA0106
Front speakers
rear:CARD=CA0106,DEV=0
CA0106, CA0106
Rear speakers
center_lfe:CARD=CA0106,DEV=0
CA0106, CA0106
Center and Subwoofer speakers
side:CARD=CA0106,DEV=0
CA0106, CA0106
Side speakers
surround40:CARD=CA0106,DEV=0
CA0106, CA0106
4.0 Surround output to Front and Rear speakers
surround41:CARD=CA0106,DEV=0
CA0106, CA0106
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CA0106,DEV=0
CA0106, CA0106
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CA0106,DEV=0
CA0106, CA0106
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CA0106,DEV=0
CA0106, CA0106
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CA0106,DEV=0
CA0106, CA0106
IEC958 (S/PDIF) Digital Audio Output
null
Discard all samples (playback) or generate zero samples (capture)


---

### Post by fanaticx on 2008-09-12
any help ?

---

### Post by fanaticx on 2008-09-12
anybody can guide me on this sound problem i just need to get sound to work.

---

