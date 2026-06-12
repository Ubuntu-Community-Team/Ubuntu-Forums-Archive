---
title: "[ProLiant MicroServer, ATI R6xx HDMI, Digital Out, HDMI] No HDMI sound at all"
date: 2012-08-06
forum: Multimedia Software
---

### Post by vnatius on 2012-08-06
Hi guys,

Doing well?
I've been Googling for a month now without luck. This sound card is the HDMI sound on a Asus Radeon HD 5430 Series VGA card. I've installed the latest driver from AMD (after some time of struggling on the original driver) without luck. The sound card shows up in lshw and looks fine in alsamixer (not muted) but the friggen thing does not show in "All Settings -> Sound -> Play Sound Through" and subsequently does not play sound with my xbmc movies.

It's probably going to be something stupid and I will apologise profusely however at this time I'm at my wits end.

Some outputs:

lsb_release -a; uname -a

No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 12.04 LTS
Release: 12.04
Codename: precise
Linux MediaServer 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$lshw:

product: Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:AA68]
vendor: Hynix Semiconductor (Hyundai Electronics)
bus info: pci@0000:01:00.1
version: 00
width: 64 bits
clock: 33MHz
capabilities:
 Power Management,
 PCI Express,
 Message Signalled Interrupts,
 bus mastering,
 PCI capabilities listing
configuration:
 driver: snd_hda_intel
 latency: 0
resources:
 irq: 43
 memory: fe8bc000-fe8bffff

$dmesg |grep Audio

[ 14.068772] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input4

$lsmod | grep snd

snd_hda_codec_hdmi 32474 1
snd_hda_intel 33773 3
snd_hda_codec 127706 2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep 13668 1 snd_hda_codec
snd_pcm 97188 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi 13324 0
snd_rawmidi 30748 1 snd_seq_midi
snd_seq_midi_event 14899 1 snd_seq_midi
snd_seq 61896 2 snd_seq_midi,snd_seq_midi_event
snd_timer 29990 2 snd_pcm,snd_seq
snd_seq_device 14540 3 snd_seq_midi,snd_rawmidi,snd_seq
snd 78855 15 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 15091 1 snd
snd_page_alloc 18529 2 snd_hda_intel,snd_pcm

Now comes the weird part... :

lspci

........ omitted 
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5430 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe (rev 10)

then: 
aplay -l

aplay: device_list:252: no soundcards found...

What the??

Driver installed:

AMD Catalyst™ 12.6 Proprietary Linux x86 Display Driver	 v12.6	6/28/2012
from
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

From what I've since figured out the VGA driver is loaded but not sound; do I need to separately load a sound driver even though its one card and one HDMI port?

What else do you need to figure this one out?
Thanks in advance.

---

