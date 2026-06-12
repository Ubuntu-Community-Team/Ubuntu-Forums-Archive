---
title: "Dummy sound 12.04"
date: 2012-12-18
forum: Multimedia Software
---

### Post by SlugSlug on 2012-12-18
A PC using mint rebooted and now has no sound, the volume control shows 'Dummy Sound'

It's an intel motherboard with on-board sound.


Tried booting into older kernel - no luck


Am waiting for a live boot disk to check if it works from that but in the meantime...

```
 aplay -l 
aplay: device_list:252: no soundcards found...

``````
lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7500 LE] (rev a1)
04:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
04:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

```

---

### Post by SlugSlug on 2012-12-20
Sound worked from live cd :(

---

### Post by SlugSlug on 2012-12-21
bump :popcorn:

---

### Post by dannyboy79 on 2012-12-21
have you checked out this thread?
[http://ubuntuforums.org/showthread.php?p=12189749#post12189749](http://ubuntuforums.org/showthread.php?p=12189749#post12189749)

---

### Post by SlugSlug on 2012-12-21
Yea the sound is not disabled in BIOS

---

### Post by BicyclerBoy on 2012-12-21
Try:
sudo aplay -l

If this is successful then add your user to audio group.

Any clues in output of:
dmesg

---

