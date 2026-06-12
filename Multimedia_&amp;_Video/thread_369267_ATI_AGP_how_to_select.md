---
title: "ATI AGP how to select"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by StarLog on 2007-02-24
Running Edgy 6.10 on a GBox like a Shuttle. I have tried to follow the instructions here:
[https://help.ubuntu.com/community/BinaryDriverHowto/AT](https://help.ubuntu.com/community/BinaryDriverHowto/AT)

When I run lspci It shows:
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 USB Controller: NEC Corporation USB (rev 41)
00:08.1 USB Controller: NEC Corporation USB (rev 41)
00:08.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

The Display controller is (Secondary), I have change the system bios to select the AGP first.
Is there something I need to modify in order for the R350 Radeon 9800 to be the main video.?

Thanks

---

