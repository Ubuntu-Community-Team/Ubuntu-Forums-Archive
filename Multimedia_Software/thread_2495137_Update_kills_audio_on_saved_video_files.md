---
title: "Update kills audio on saved video files"
date: 2024-02-07
forum: Multimedia Software
---

### Post by dkolars on 2024-02-07
Just did a regular update yesterday when it popped up, and now I find that, while my audio is working fine for the internet, YouTube, etc, NONE of my saved audio and video files have audio!  Using VLC, but have tried others, and no sound while the video plays or the bar moves on audio files.  Have NO clue why this would happen.  All settings are as they were before the update.
Ran this:
```
hwinfo --sound

20: PCI 2c00.4: 0403 Audio device                               
  [Created at pci.386]
  Unique ID: 0wB7.W_bpw7d2tl3
  Parent ID: JZZT.YJhZDzGYdS4
  SysFS ID: /devices/pci0000:00/0000:00:08.1/0000:2c:00.4
  SysFS BusID: 0000:2c:00.4
  Hardware Class: sound
  Device Name: "Realtek ALC1220"
  Model: "AMD Starship/Matisse HD Audio Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1487 "Starship/Matisse HD Audio Controller"
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd. [MSI]"
  SubDevice: pci 0x9c56 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfcf00000-0xfcf07fff (rw,non-prefetchable)
  IRQ: 62 (63637 events)
  Module Alias: "pci:v00001022d00001487sv00001462sd00009C56bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #23 (PCI bridge)


42: PCI 600.1: 0403 Audio device
  [Created at pci.386]
  Unique ID: moNa.b0tOCU4_vDC
  Parent ID: Ddhb.CS5kfnTSviA
  SysFS ID: /devices/pci0000:00/0000:00:01.2/0000:02:00.2/0000:03:00.0/0000:04:00.0/0000:05:00.0/0000:06:00.1
  SysFS BusID: 0000:06:00.1
  Hardware Class: sound
  Model: "ATI Audio device"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0xab28 
  SubVendor: pci 0x1002 "ATI Technologies Inc"
  SubDevice: pci 0xab28 
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfc920000-0xfc923fff (rw,non-prefetchable)
  IRQ: 60 (3759 events)
  Module Alias: "pci:v00001002d0000AB28sv00001002sd0000AB28bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #30 (PCI bridge)

```

Running Ubuntu 22.04.3.

Just checked the Audio page in Settings, and the "Test" played no sound.  The Alert sounds work, but not the Test.  Using the Starship/Matisse audio, btw.

TIA

SOLUTION:  did "sudo apt update && sudo apt upgrade" and voila'...  updates had not completed, apparently.  Sheesh.

---

