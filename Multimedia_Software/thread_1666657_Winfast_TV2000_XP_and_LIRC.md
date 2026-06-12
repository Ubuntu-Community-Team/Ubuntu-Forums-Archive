---
title: "Winfast TV2000 XP and LIRC"
date: 2011-01-14
forum: Multimedia Software
---

### Post by Adamal on 2011-01-14
Has anyone out there gotten the remote control for the  Winfast TV2000 XP to work with any latest version of ubuntu.  I've tried all the guides out there and I can't get Ubuntu to work with the CoolCommand remote control.

```
udi = '/org/freedesktop/Hal/devices/temp/132'
  info.ignore = true  (bool)
  info.parent = '/org/freedesktop/Hal/devices/pci_109e_36e'  (string)
  info.product = 'Ignored Device'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ignored-device'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/pci_109e_36e'  (string)
  input.product = 'bttv IR (card=34)'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:10.0/0000:04:08.0/rc/rc0/input4/event3'  (string)

```
```
[ 4336.840766] bttv: driver version 0.9.18 loaded
[ 4336.840776] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 4336.842571] bttv: Bt8xx card found (0).
[ 4336.842604] bttv0: Bt878 (rev 17) at 0000:04:08.0, irq: 16, latency: 32, mmio: 0xfdbff000
[ 4336.842653] bttv0: subsystem: 107d:ff06 (UNKNOWN)
[ 4336.842658] please mail id, board name and the correct card= insmod option to linux-media@vger.kernel.org
[ 4336.842667] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[ 4336.842720] bttv0: gpio: en=00000000, out=00000000 in=00bf7707 [init]
[ 4336.846521] bttv0: tuner type=2
[ 4336.890852] bttv0: audio absent, no audio device found!
[ 4336.928085] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[ 4336.928653] tuner-simple 2-0061: creating new instance
[ 4336.928662] tuner-simple 2-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[ 4336.932713] bttv0: registered device video1
[ 4336.933114] bttv0: registered device vbi0
[ 4336.933387] bttv0: registered device radio0
[ 4336.933409] bttv0: PLL: 28636363 => 35468950 .
[ 4336.945017] bttv0: PLL: 28636363 => 35468950 .
[ 4336.947198] bttv0: PLL: 28636363 => 35468950 . ok
[ 4336.957434] Registered IR keymap rc-winfast
[ 4336.959619] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:10.0/0000:04:08.0/rc/rc0/input4
[ 4336.959747] rc0: bttv IR (card=34) as /devices/pci0000:00/0000:00:10.0/0000:04:08.0/rc/rc0

```

Currently none of the remote keys are working using evtest or irw.

---

