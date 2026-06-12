---
title: "How to watch tv on Ati Radeon AIW 9800SE"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by aldolat on 2007-03-17
Hi to all!

I have an Ati Radeon All-In-Wonder 9800 SE video card, with Video-In Video-Out technology, and a tv-tuner built-in.
The tuner is a Philips FQ1216ME.

Chip image:
[[IMG]http://img292.imageshack.us/img292/5929/chipyt0.th.jpg[/IMG]]("http://img292.imageshack.us/my.php?image=chipyt0.jpg")

Tuner image:
[[IMG]http://img131.imageshack.us/img131/3783/tunerev5.th.jpg[/IMG]]("http://img131.imageshack.us/my.php?image=tunerev5.jpg")

[B]How can I watch TV on my Ubuntu Edgy?
[/B]I live in Italy.

This is my lspci output:
> aldo@edgy:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc R350 AH [Radeon 9800]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800] (Secondary)
02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0a.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0a.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:0a.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
02:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:0b.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
02:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

and this is modprobe output:
> aldo@edgy:~$ sudo modprobe -l | grep ati
/lib/modules/2.6.17-11-generic/kernel/sound/pci/snd-atiixp.ko
/lib/modules/2.6.17-11-generic/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/usb/input/ati_remote2.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/usb/input/ati_remote.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/pcmcia/rsrc_nonstatic.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/ide/pci/atiixp.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/cpufreq/cpufreq_conservative.ko
/lib/modules/2.6.17-11-generic/kernel/drivers/char/agp/ati-agp.ko
/lib/modules/2.6.17-11-generic/volatile/ath_hal.ko
/lib/modules/2.6.17-11-generic/volatile/fcdsl.ko
/lib/modules/2.6.17-11-generic/volatile/fcdsl2.ko
/lib/modules/2.6.17-11-generic/volatile/fcdslsl.ko
/lib/modules/2.6.17-11-generic/volatile/fcdslslusb.ko
/lib/modules/2.6.17-11-generic/volatile/fcdslusb.ko
/lib/modules/2.6.17-11-generic/volatile/fcdslusb2.ko
/lib/modules/2.6.17-11-generic/volatile/fcdslusba.ko
/lib/modules/2.6.17-11-generic/volatile/fcpci.ko
/lib/modules/2.6.17-11-generic/volatile/fcusb.ko
/lib/modules/2.6.17-11-generic/volatile/fglrx.ko
/lib/modules/2.6.17-11-generic/volatile/fxusb.ko
/lib/modules/2.6.17-11-generic/volatile/nvidia.ko
/lib/modules/2.6.17-11-generic/volatile/nvidia_legacy.ko

---

