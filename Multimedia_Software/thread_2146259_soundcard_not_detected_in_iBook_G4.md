---
title: "soundcard not detected in iBook G4"
date: 2013-05-17
forum: Multimedia Software
---

### Post by gizmo720 on 2013-05-17
I'm running the power-pc version of Ubuntu 12.04 on an iBook G4. 
On boot (prior to the bootloader), I do hear a chime from the speakers. However, once booted into ubuntu, the sound does not work.

the output of `sudo aplay -l`is:
aplay: device_list:252: no soundcards found...

`uname -a`:
Linux ubuntu 3.2.0-43-powerpc-smp #68-Ubuntu SMP Wed May 15 03:36:02 UTC 2013 ppc ppc ppc GNU/Linux

`lspci` :
```
0000:00:0b.0 Host bridge: Apple Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M11 NV [FireGL Mobility T2e] (rev 80)
0001:10:0b.0 Host bridge: Apple Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Unassigned class [ff00]: Apple Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
```

`find /proc/device-tree/ | grep sound`:
```
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/name
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/linux,phandle
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/platform-tas-codec-ref
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/vendor-id
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/object-model-version
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/layout-id
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/built-in
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/compatible
/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound/device_type
/proc/device-tree/pseudo-sound
/proc/device-tree/pseudo-sound/name
/proc/device-tree/pseudo-sound/linux,phandle
/proc/device-tree/aliases/sound

```

`lsmod | grep snd`:
```
snd_aoa                16220  0 
snd_pcm                88810  0 
snd_page_alloc          7388  1 snd_pcm
snd_seq_midi            5452  0 
snd_rawmidi            23596  1 snd_seq_midi
snd_seq_midi_event      7251  1 snd_seq_midi
snd_seq                61149  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23931  2 snd_pcm,snd_seq
snd_seq_device          6920  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    71227  6 snd_aoa,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7799  1 snd


```

Looking at the files within "/proc/device-tree/pci@f2000000/mac-io@17/i2s@0/i2s-a@10000/sound",
I found that
 'device_type' is "soundchip"
'compatible' is "AOA"

Hexdumping 'vendor-id' gives 0x106b (Apple)
Hexdumping 'layout-id' gives 0x50 (=80 in decimal)

I've installed alsa-source and alsa-firmware-loader.

---

