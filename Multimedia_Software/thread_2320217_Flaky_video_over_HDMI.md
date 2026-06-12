---
title: "Flaky video over HDMI"
date: 2016-04-11
forum: Multimedia Software
---

### Post by The_Woodpecker on 2016-04-11
If I connect my laptop to my TV or anyother screen with HDMI, the laptop flicks the output  between full HD 1080 single screen and dual screen with the laptops own moniter when I just want the TV to show it and not the laptop.

I want the laptop to keep outputing 1280x720 but it doesn't stay.

What should I do?

MY laptop is a HP Pavilion TS 11

---

### Post by papibe on 2016-04-11
Hi lukewhiting1996.

Could you open a terminal, run these commands and paste back the results? (you can copy/paste the text from the terminal)
```
lsb_release -a

sudo lshw -C display

lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'
```
Regards.

---

### Post by The_Woodpecker on 2016-04-12
```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
```

```
sudo lshw -C display
 *-display               
       description: VGA compatible controller
       product: Kabini [Radeon HD 8210]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:80 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:3000(size=256) memory:f0c00000-f0c3ffff memory:f0c60000-f0c7ffff
```

```
lspci -nnk | grep -iA2 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8210] [1002:9834]
    Subsystem: Hewlett-Packard Company Device [103c:2178]
    Kernel driver in use: fglrx_pci
```

```
lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'
fglrx                7531632  231 
snd_hda_intel          43326  7 
snd_hda_codec         169534  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_pcm                94597  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd                    61270  24 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_seq_midi,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
```

---

