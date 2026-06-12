---
title: "atheros ar9287 on ubuntu"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by bruno9779 on 2012-07-21
I have just installed a wireless pci card with the Atheros 9287 chipset and I need some help getting it to work.

It is not detected by ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:24:1d:8d:b7:d9  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe8d:b7d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5179682 (5.1 MB)  TX bytes:852554 (852.5 KB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

but it is by lspci

```
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
[COLOR="Red"]03:07.0 Unclassified device [0080]: Atheros Communications Inc. AR9287 Wireless Network Adapter (rev 01[/COLOR])
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

also, lsmod shows I have the ath9k module installed:

```
Module                  Size  Used by
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
binfmt_misc            17540  1 
vesafb                 13809  1 
[COLOR="Red"]ath9k                 121335  0 [/COLOR]
mac80211              302141  1 ath9k
[COLOR="Red"]ath9k_common           13839  1 ath9k[/COLOR]
snd_usb_audio         118064  1 
snd_usbmidi_lib        25371  1 snd_usb_audio
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
[COLOR="Red"]ath9k_hw              304840  2 ath9k,ath9k_common[/COLOR]
ath                    23780  2 ath9k,ath9k_hw
psmouse                73882  0 
cfg80211              198044  3 ath9k,mac80211,ath
snd_hda_codec_realtek   330769  1 
ppdev                  17113  0 
snd_hda_intel          33390  4 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96755  4 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
serio_raw              13166  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              10888310  40 
sp5100_tco             13791  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  20 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
edac_core              53746  0 
k10temp                13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_mce_amd           23709  0 
i2c_piix4              13301  0 
wmi                    19256  0 
parport_pc             36962  1 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13164  0 
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0 

```

My kernel is 3.0.0-12-generic and google did not give any relevant results for newer kernels.

Thanks in advance

---

### Post by bakegoodz on 2012-07-21
ar9287 has been supported since kernel 2.6.32. It looks like the driver is not reconizing your device by it's PCI ID. Must be a new model of card.
Give me the output of "lspci -nn" and I reasearch this further

---

### Post by bruno9779 on 2012-07-22
I have dug deep on this issue, when I have realized that I had never used that pci slot in 3 years.

After a careful cleaning of the slot, the card works perfectly.

Never underestimate the crud the piles up in a computer.

---

### Post by bakegoodz on 2012-07-22
That is interesting, I wouldn't have thought of a dirty pci slot throwing off the identification. I may have encountered this same issue with mpci wifi card and Windows before. The inf driver refused to install, said it didn't match the hardware. The exact same card and driver worked in another computer.

---

