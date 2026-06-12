---
title: "Help enabling power saving on my video card"
date: 2012-05-01
forum: Multimedia Software
---

### Post by Benjamindaines on 2012-05-01
I am using an ATI Mobility X1600 with the open source driver (Gallium .4 RV530) with 12.04 and can't seem to enable power saving.  I'm following these directions [http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options](http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options) but /sys/class/drm/card0/device/power_profile doesn't exist.  Anyone have any idea how to get this working?  thanks.

---

### Post by brainwash on 2012-05-01
Please attach the result of this command:
```
dmesg | grep drm
```

---

### Post by Benjamindaines on 2012-05-01
> **brainwash said:**
> Please attach the result of this command:
```
dmesg | grep drm
```
```

[   10.752670] [drm] Initialized drm 1.1.0 20060810
[   13.796429] [drm] radeon defaulting to kernel modesetting.
[   13.796432] [drm] radeon kernel modesetting enabled.
[   13.796716] [drm] initializing kernel modesetting (RV530 0x1002:0x71C5 0x106B:0x0080).
[   13.796743] [drm] register mmio base: 0xD8300000
[   13.796745] [drm] register mmio size: 65536
[   13.796896] [drm] Generation 2 PCI interface, using max accessible memory
[   13.796924] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.796926] [drm] Driver supports precise vblank timestamp query.
[   13.796995] [drm] radeon: irq initialized.
[   13.798643] [drm] Detected VRAM RAM=256M, BAR=256M
[   13.798646] [drm] RAM width 128bits DDR
[   13.798790] [drm] radeon: 256M of VRAM memory ready
[   13.798792] [drm] radeon: 512M of GTT memory ready.
[   13.798816] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.800541] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[   13.801369] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   13.801483] [drm] Loading R500 Microcode
[   14.063302] [drm] radeon: ring at 0x0000000010001000
[   14.063335] [drm] ring test succeeded in 9 usecs
[   14.063448] [drm] radeon: ib pool ready.
[   14.063541] [drm] ib test succeeded in 0 usecs
[   14.063873] [drm] Radeon Display Connectors
[   14.063875] [drm] Connector 0:
[   14.063877] [drm]   LVDS
[   14.063879] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[   14.063880] [drm]   Encoders:
[   14.063882] [drm]     LCD1: INTERNAL_LVTM1
[   14.063884] [drm] Connector 1:
[   14.063885] [drm]   S-video
[   14.063886] [drm]   Encoders:
[   14.063887] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   14.063889] [drm] Connector 2:
[   14.063890] [drm]   DVI-I
[   14.063891] [drm]   HPD1
[   14.063893] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   14.063895] [drm]   Encoders:
[   14.063896] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   14.063898] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   14.220201] [drm] fb mappable at 0xC00C0000
[   14.220204] [drm] vram apper at 0xC0000000
[   14.220206] [drm] size 7258112
[   14.220207] [drm] fb depth is 24
[   14.220209] [drm]    pitch is 6912
[   14.220333] fbcon: radeondrmfb (fb0) is primary device
[   14.220527] fb0: radeondrmfb frame buffer device
[   14.220529] drm: registered panic notifier
[   14.220536] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[ 3702.861421] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[ 3702.864782] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[ 3702.864840] [drm] radeon: ring at 0x0000000010001000
[ 3702.864872] [drm] ring test succeeded in 9 usecs
[ 3702.864883] [drm] ib test succeeded in 0 usecs
[ 8008.657656] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[ 8008.661207] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[ 8008.661310] [drm] radeon: ring at 0x0000000010001000
[ 8008.661341] [drm] ring test succeeded in 9 usecs
[ 8008.661354] [drm] ib test succeeded in 0 usecs
[ 8155.301554] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[ 8155.305668] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[ 8155.305794] [drm] radeon: ring at 0x0000000010001000
[ 8155.305859] [drm] ring test succeeded in 0 usecs
[ 8155.305918] [drm] ib test succeeded in 0 usecs

```

---

### Post by brainwash on 2012-05-02
Well, the radeon power managment hasn't been initialized. The specific log entry is missing.

Are you using a MacBook Pro?

---

### Post by Benjamindaines on 2012-05-02
> **brainwash said:**
> Well, the radeon power managment hasn't been initialized. The specific log entry is missing.

Are you using a MacBook Pro?

Yes. MacBook Pro 2,1. Unfortunately this model has no documentation.

---

### Post by brainwash on 2012-05-02
I'm not sure, if we can find a solution to enable power managment on your X1600. You can only use the open source driver (radeon), because the proprietary one (catalyst) does not support your GPU anymore.

There are some instructions on this site which might be helpful:

[https://wiki.archlinux.org/index.php/ATI#Powersaving](https://wiki.archlinux.org/index.php/ATI#Powersaving)


BUT if there is no way to read the power state tables (vbios), reducing the frequency won't be possible.

---

### Post by Benjamindaines on 2012-05-02
> **brainwash said:**
> I'm not sure, if we can find a solution to enable power managment on your X1600. You can only use the open source driver (radeon), because the proprietary one (catalyst) does not support your GPU anymore.

There are some instructions on this site which might be helpful:

[https://wiki.archlinux.org/index.php/ATI#Powersaving](https://wiki.archlinux.org/index.php/ATI#Powersaving)


BUT if there is no way to read the power state tables (vbios), reducing the frequency won't be possible.

Is there any way to check what's being reported in the vbios?  I have a feeling that the power state not being reported is the issue.  Would that have something to do with refit?  If the vbios values can be checked and the power state is not being reported, would there be anyway to correct it (short of using my non-existent coding abilities to rework the driver)?  Thanks so much for your help!

---

