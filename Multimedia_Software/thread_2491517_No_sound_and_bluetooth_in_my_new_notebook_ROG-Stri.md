---
title: "No sound and bluetooth in my new notebook ROG-Strix-G713PI-G713PI. Need help"
date: 2023-10-11
forum: Multimedia Software
---

### Post by bishwajit93 on 2023-10-11
Dear nice community here,
I am using ubuntu 22.04 for dual boot as there is no sound and Bluetooth in my notebook model ROG-Strix-G713PI-G713PI. Everything works fine in windows boot system but wehn I use ubuntu the bluetooth and sound does not work. I have worked so many stuffs from google, youtube and chatGPT but nothing works. The does not work totally and even the audio port does not work. But as I mentioned, everything works totally fine in windows(The Bluetooth and sound, audio jack). Could anyone please give any solutions: It would be really helpful for me. If you need any further info about this issue then please feel free to ask me and I will be happy to assist.
Kind regards,
Bishwajit Karmaker

uname -r
6.2.0-34-generic


lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 002: ID 0b05:19b6 ASUSTek Computer, Inc. N-KEY Device
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 062a:4c01 MosArt Semiconductor Corp. 2,4Ghz Wireless Transceiver [for Delux M618 Plus Wireless Vertical Mouse]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0489:e0f6 Foxconn / Hon Hai Wireless_Device
Bus 003 Device 002: ID 13d3:5458 IMC Networks USB2.0 HD UVC WebCam
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 17e9:4307 DisplayLink USB 3.0 Dual Video Dock
Bus 002 Device 002: ID 2109:0817 VIA Labs, Inc. USB3.0 Hub             
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 003: ID 062a:4c01 MosArt Semiconductor Corp. 2,4Ghz Wireless Transceiver [for Delux M618 Plus Wireless Vertical Mouse]
Bus 001 Device 002: ID 2109:2817 VIA Labs, Inc. USB2.0 Hub             
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14d8
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 14d9
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db
00:01.6 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db
00:01.7 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14db
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
00:04.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14da
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14dd
00:08.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 14dd
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 71)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 14e7
01:00.0 VGA compatible controller: NVIDIA Corporation Device 2860 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 22bd (rev a1)
02:00.0 Non-Volatile memory controller: Micron Technology Inc Device 5413 (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
04:00.0 Network controller: MEDIATEK Corp. Device 0616
05:00.0 PCI bridge: ASMedia Technology Inc. Device 242a (rev 01)
06:02.0 PCI bridge: ASMedia Technology Inc. Device 242b (rev 01)
07:00.0 USB controller: ASMedia Technology Inc. Device 242c (rev 01)
08:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 164e (rev d8)
08:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] VanGogh PSP/CCP
08:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15b6
08:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15b7
08:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor (rev 62)
08:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
09:00.0 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15b8



aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Dock [USB 3.0 Dual Video Dock], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic [HD-Audio Generic], device 0: ALC294 Analog [ALC294 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



sudo dmesg | grep -i bluetooth
[    3.361169] Bluetooth: Core ver 2.22
[    3.361199] NET: Registered PF_BLUETOOTH protocol family
[    3.361201] Bluetooth: HCI device and connection manager initialized
[    3.361208] Bluetooth: HCI socket layer initialized
[    3.361212] Bluetooth: L2CAP socket layer initialized
[    3.361219] Bluetooth: SCO socket layer initialized
[    4.824455] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.824458] Bluetooth: BNEP filters: protocol multicast
[    4.824462] Bluetooth: BNEP socket layer initialized
[    5.416307] Bluetooth: hci0: Opcode 0x c03 failed: -110

---

### Post by robert-marion-phillips on 2023-10-17
Bumping this, as I am having the same issue with the same hardware: ROG Strix G713PI_G713PI 1.0
Dual boot with Windows 11. No sound or bluetooth on Ubuntu 23.04 or 23.10

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC294 Analog [ALC294 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
lspci -nnk | grep -A2 Audio
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:22bd] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:25dd]
    Kernel driver in use: snd_hda_intel
--
09:00.5 Multimedia controller [0480]: Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor [1022:15e2] (rev 62)
    Subsystem: ASUSTeK Computer Inc. ACP/ACP3X/ACP6x Audio Coprocessor [1043:1d1f]
    Kernel driver in use: snd_rpl_pci_acp6x
    Kernel modules: snd_pci_acp3x, snd_rn_pci_acp3x, snd_pci_acp5x, snd_pci_acp6x, snd_acp_pci, snd_rpl_pci_acp6x, snd_pci_ps, snd_sof_amd_renoir, snd_sof_amd_rembrandt
09:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller [1022:15e3]
    DeviceName: Realtek ALC1220
    Subsystem: ASUSTeK Computer Inc. Family 17h/19h HD Audio Controller [1043:1d1f]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
```

I made sure Windows was not using fast boot. Fast boot is also disabled in BIOS.

I also tried various "options snd-hda-intel model=" options in /etc/modprobe.d/alsa-base.conf with no luck.

```

sudo journalctl -k | grep -Ei "ALSA|HDA|sof[-]|HDMI|snd[_-]|sound|hda.codec|hda.intel"
Oct 18 11:22:18 stardock kernel: cs35l41-hda i2c-CSC3551:00-cs35l41-hda.0: Error: ACPI _DSD Properties are missing for HID CSC3551.
Oct 18 11:22:18 stardock kernel: cs35l41-hda i2c-CSC3551:00-cs35l41-hda.0: error -EINVAL: Platform not supported
Oct 18 11:22:18 stardock kernel: cs35l41-hda: probe of i2c-CSC3551:00-cs35l41-hda.0 failed with error -22
Oct 18 11:22:18 stardock kernel: cs35l41-hda i2c-CSC3551:00-cs35l41-hda.1: Error: ACPI _DSD Properties are missing for HID CSC3551.
Oct 18 11:22:18 stardock kernel: cs35l41-hda i2c-CSC3551:00-cs35l41-hda.1: error -EINVAL: Platform not supported
Oct 18 11:22:18 stardock kernel: cs35l41-hda: probe of i2c-CSC3551:00-cs35l41-hda.1 failed with error -22
Oct 18 11:22:18 stardock kernel: snd_rpl_pci_acp6x 0000:09:00.5: enabling device (0000 -> 0002)
Oct 18 11:22:20 stardock kernel: [drm] DP-HDMI FRL PCON supported
Oct 18 11:22:23 stardock kernel: snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
Oct 18 11:22:23 stardock kernel: snd_hda_intel 0000:01:00.1: Disabling MSI
Oct 18 11:22:23 stardock kernel: snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
Oct 18 11:22:23 stardock kernel: input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/0000:01:00.1/sound/card0/input25
Oct 18 11:22:23 stardock kernel: input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.1/0000:01:00.1/sound/card0/input26
Oct 18 11:22:23 stardock kernel: input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.1/0000:01:00.1/sound/card0/input27
Oct 18 11:22:23 stardock kernel: input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.1/0000:01:00.1/sound/card0/input28
Oct 18 11:22:23 stardock kernel: snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC294: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
Oct 18 11:22:23 stardock kernel: snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Oct 18 11:22:23 stardock kernel: snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
Oct 18 11:22:23 stardock kernel: snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
Oct 18 11:22:23 stardock kernel: snd_hda_codec_realtek hdaudioC1D0:    inputs:
Oct 18 11:22:23 stardock kernel: snd_hda_codec_realtek hdaudioC1D0:      Mic=0x12
Oct 18 11:22:24 stardock kernel: input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:08.1/0000:09:00.6/sound/card1/input29

```

---

### Post by robert-marion-phillips on 2023-10-19
Well, this isn't good news: [https://lore.kernel.org/lkml/b4c202b2-ab29-e2aa-b141-0c967b2c1645@opensource.cirrus.com/T/](https://lore.kernel.org/lkml/b4c202b2-ab29-e2aa-b141-0c967b2c1645@opensource.cirrus.com/T/)

---

### Post by jeremy31 on 2023-10-28
I may have a fix for Bluetooth, Secure Boot needs to be disabled, check ```
mokutil --sb
```
Then in terminal
```
sudo apt install git dkms
git clone https://github.com/jeremyb31/bluetooth-6.2.git
sudo dkms add ./bluetooth-6.2
sudo dkms install btusb/4.1
```
Reboot

---

