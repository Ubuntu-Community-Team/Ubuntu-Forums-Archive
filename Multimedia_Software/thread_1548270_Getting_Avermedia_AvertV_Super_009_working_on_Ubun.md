---
title: "Getting Avermedia AvertV Super 009 working on Ubuntu"
date: 2010-08-08
forum: Multimedia Software
---

### Post by neosrix on 2010-08-08
I had purchased an Avermedia Avertv Super 009 card in India. Afaik, This is an analogue card and doesn't support DVB. I am trying to install it in Ubuntu 10.04. The card was auto detected as UNKNOWN/GENERIC . So I setup the modprobe options as card=117 tuner =54 . I choose card=117 because that corresponds to Avermedia Avertv Super 007 model which, I felt may be the closest match. Chose tuner=54 because [this site]("http://mandrivausers.org/index.php?/topic/43596-card-and-tuner-list/") listed " tuner=54 - Philips/NXP TDA 8290/8295 + 8275/8275A/18271" and my card has NXP TDA18271HDC2 chip .

However when I scan for channels using scantv -a -c /dev/video0 -C /dev/vbi0 , it is not finding any channel. Tvtime also fails to find any channels. My RF feed is actually RF out of Tata sky Set top box. A regular TV can auto tune and display the video properly. What am I missing here? Please advice.

I am listing some logs for reference. All these were captured after setting card=117 tuner=54 settings

lsmod:
--------------------------------------------------------------------
Module                  Size  Used by
binfmt_misc             6587  1 
snd_wavefront          33066  0 
snd_cs4236             25514  0 
snd_wss_lib            23410  2 snd_wavefront,snd_cs4236
snd_intel8x0           25588  2 
snd_opl3_lib            8966  2 snd_wavefront,snd_cs4236
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_hwdep               5412  2 snd_wavefront,snd_opl3_lib
saa7134_alsa           10380  1 
snd_mpu401              5123  0 
snd_pcm_oss            35308  0 
snd_mpu401_uart         5617  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_mixer_oss          13746  1 snd_pcm_oss
tda8290                12092  0 
snd_seq_dummy           1338  0 
snd_pcm                70662  6 snd_cs4236,snd_wss_lib,snd_intel8x0,snd_ac97_codec,saa7134_alsa,snd_pcm_oss
tea5767                 5950  0 
snd_seq_oss            26726  0 
nfsd                  238967  13 
exportfs                3437  1 nfsd
snd_seq_midi            4557  0 
tuner                  20412  1 
snd_rawmidi            19056  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
nfs                   264813  0 
saa7134               143391  1 saa7134_alsa
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
lockd                  64849  2 nfsd,nfs
arc4                    1153  2 
nfs_acl                 2245  2 nfsd,nfs
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ir_common              38875  1 saa7134
auth_rpcgss            33735  2 nfsd,nfs
v4l2_common            15431  2 tuner,saa7134
zd1211rw               42217  0 
snd_timer              19098  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
videodev               34361  3 tuner,saa7134,v4l2_common
v4l1_compat            13251  1 videodev
snd_seq_device          5700  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dma_sg        10782  2 saa7134_alsa,saa7134
mac80211              205146  1 zd1211rw
sunrpc                193085  12 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
snd                    54148  24 snd_wavefront,snd_cs4236,snd_wss_lib,snd_intel8x0,snd_opl3_lib,snd_ac97_codec,snd_hwdep,saa7134_alsa,snd_mpu401,snd_pcm_oss,snd_mpu401_uart,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          16356  2 saa7134,videobuf_dma_sg
nvidia               4701243  32 
ppdev                   5259  0 
ns558                   3056  0 
tveeprom               11102  1 saa7134
intel_agp              24119  1 
cfg80211              126517  2 zd1211rw,mac80211
serio_raw               3978  0 
snd_page_alloc          7076  3 snd_wss_lib,snd_intel8x0,snd_pcm
gameport                9089  2 ns558
soundcore               6620  1 snd
parport_pc             25962  1 
agpgart                31724  2 nvidia,intel_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
8139too                18545  0 
8139cp                 16186  0 
floppy                 53016  0 
mii                     4381  2 8139too,8139cp
usbhid                 36110  0 
hid                    67032  1 usbhid

dmesg:
------------------------------------------------------
28.346483] usbcore: registered new interface driver zd1211rw
[   28.445187] saa7130/34: v4l2 driver version 0.2.15 loaded
[   28.445362] saa7134 0000:02:03.0: PCI INT A -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
[   28.445379] saa7133[0]: found at 0000:02:03.0, rev: 209, irq: 5, latency: 32, mmio: 0xdf001000
[   28.445395] saa7133[0]: subsystem: 1461:4055, board: [COLOR=Blue]Avermedia Super 007 [card=117,insmod option][/COLOR]
[   28.445461] saa7133[0]: board init: gpio is 40000
[   28.445496] IRQ 5/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   28.720077] saa7133[0]: i2c eeprom 00: 61 14 55 40 00 00 00 00 00 00 00 00 00 00 00 00
[   28.720107] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   28.720132] saa7133[0]: i2c eeprom 20: 01 40 01 02 ff 01 01 03 ff ff 00 6b ff ff ff ff
[   28.720157] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720182] saa7133[0]: i2c eeprom 40: ff 96 00 c0 84 ff 08 30 ff 15 ff 40 ff 0c 01 ff
[   28.720206] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720231] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720256] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720280] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720305] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720329] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720354] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720378] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720403] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720428] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720452] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   28.720484] i2c i2c-0: Invalid 7-bit address 0x7a
[   28.942748] udev: renamed network interface wlan0 to wlan1
[   28.959093] usb 1-1.1: firmware: requesting zd1211/zd1211b_ub
[   29.038182] usb 1-1.1: firmware: requesting zd1211/zd1211b_uphr
[   29.220781] zd1211rw 1-1.1:1.0: firmware version 4725
[   29.256922] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[   29.282790] zd1211rw 1-1.1:1.0: zd1211b chip 050d:705c v4810 full 00-22-75 AL2230_RF pa0 g--NS
[   29.285783] cfg80211: Calling CRDA for country: US
[   29.302710] Chip ID is not zero. It is not a TEA5767
[   29.303080] tuner 0-0060: chip found @ 0xc0 (saa7133[0])
[   29.333113] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   29.350251] cfg80211: Regulatory domain changed to country: US
[   29.350265]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.350274]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   29.350282]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   29.350289]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.350297]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.350305]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.350312]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   29.683464] [COLOR=Red]tda8290: no gate control were provided![/COLOR]
[   29.683909] [COLOR=Red]tuner 0-0060: Tuner has no way to set tv freq[/COLOR]
[   29.683919] [COLOR=Red]tuner 0-0060: Tuner has no way to set tv freq[/COLOR]
[   29.696518] saa7133[0]: registered device video0 [v4l2]
[   29.696599] saa7133[0]: registered device vbi0
[   29.706021] type=1505 audit(1281323218.572:6):  operation="profile_load" pid=688 name="/usr/share/gdm/guest-session/Xsession"
[   29.841163] saa7134 ALSA driver for DMA sound loaded
[   29.841223] IRQ 5/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   29.841291] saa7133[0]/alsa: saa7133[0] at 0xdf001000 irq 5 registered as card -2
[   29.967972] [COLOR=Red]tuner 0-0060: Tuner has no way to set tv freq[/COLOR]
[   29.970073] [COLOR=Red]tuner 0-0060: Tuner has no way to set tv freq[/COLOR]
[   30.076319] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[   30.076329] PCI: setting IRQ 12 as level-triggered
[   30.076340] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 12 (level, low) -> IRQ 12



lspci:
---------------------------------------------
02:03.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
    Subsystem: Avermedia Technologies Inc Device 4055
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 5
    Region 0: Memory at df001000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

---

### Post by neosrix on 2010-08-09
Any clues? Please help

---

### Post by neosrix on 2010-08-09
following are the chipset information I found on the Avermedia Super 009 card

NXP TDA18271HDC2

NXP TDA8295

NXP SAA7135H/203

Avermedia Super 007 had Saa7134 processor and a different tuner I guess. Am I right? How can I get Super 009 card up?

---

### Post by neosrix on 2010-08-10
Finally I manged to get AVermedia Avertv Super 009 card up. 

The card no. is 180 and it is supported only in latest **2.6.35 kernel**. Check the file [CARDLIST.saa7134 ]("http://www.kernel.org/doc/Documentation/video4linux/CARDLIST.saa7134")in the latest kernel repository. It has an entry called 
> 180 -> Avermedia M733A                          [1461:4155,1461:4255]The [Avermedia site]("http://www.avermedia.com/avertv/product/ProductDetail.aspx?Id=504") refers Avertv Super 009 card as M733/M733A. So i concluded that card=180 refers to Avertv Super 009 card.

However the problem now is that, The 2.6.32 is the latest kernel version supported by Latest Ubuntu (10.4). We cannot update to 2.6.35 using Synaptic by regular update. Luckily this forum [**Installing kernel 2.6.35 from official repositories? **]("http://ubuntuforums.org/showthread.php?p=9687334")explains how to install kernel version 2.6.35 on Ubuntu 10.4

All I did is install the Kernel 2.6.35 and created a file under /etc/modprobe.d/avermedia.conf and added the line 
> options saa7134 card=180When I restarted the system and tried tvtime it was able to scan the channels.

However, I am not able to get any audio. So the problem is only half solved. If I figure that out, will post it here. Alternatively  if somebody had success with audio please share.

Here is the dmesg (if somebody needs) for the card=180 on kernel 2.6.35.
```
[   17.839438] nvidia: module license 'NVIDIA' taints kernel.
[   17.839452] Disabling lock debugging due to kernel taint
[   17.924623] IR Sony protocol handler initialized
[   18.651542] saa7130/34: v4l2 driver version 0.2.16 loaded
[   18.651679] saa7134 0000:02:03.0: PCI INT A -> Link[LNKD] -> GSI 5 (level, low) -> IRQ 5
[   18.651696] saa7133[0]: found at 0000:02:03.0, rev: 209, irq: 5, latency: 32, mmio: 0xdf001000
[   18.651712] saa7133[0]: subsystem: 1461:4055, board: Avermedia PCI M733A [card=180,insmod option]
[   18.651749] saa7133[0]: board init: gpio is 40000
[   18.997808] usb 1-1.1: reset full speed USB device using uhci_hcd and address 4
[   19.064148] Registered IR keymap rc-avermedia-m733a-rm-k6
[   19.064430] input: saa7134 IR (Avermedia PCI M733A as /devices/pci0000:00/0000:00:1e.0/0000:02:03.0/rc/rc0/input6
[   19.064614] rc0: saa7134 IR (Avermedia PCI M733A as /devices/pci0000:00/0000:00:1e.0/0000:02:03.0/rc/rc0
[   19.413363] saa7133[0]: i2c eeprom 00: 61 14 55 40 00 00 00 00 00 00 00 00 00 00 00 00
[   19.413393] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   19.413419] saa7133[0]: i2c eeprom 20: 01 40 01 02 ff 01 01 03 ff ff 00 6b ff ff ff ff
[   19.413444] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413470] saa7133[0]: i2c eeprom 40: ff 96 00 c0 84 ff 08 30 ff 15 ff 40 ff 0c 01 ff
[   19.413495] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413520] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413545] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413570] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413595] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413620] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413645] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413670] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413695] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413720] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.413745] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.595778] phy0: Selected rate control algorithm 'minstrel'
[   19.597669] zd1211rw 1-1.1:1.0: phy0
[   19.597741] usbcore: registered new interface driver zd1211rw
[   19.738520] udev: renamed network interface wlan0 to wlan1
[   19.785945] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[   19.785957] PCI: setting IRQ 12 as level-triggered
[   19.785969] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 12 (level, low) -> IRQ 12
[   19.786006] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   19.904924] tuner 0-0042: chip found @ 0x84 (saa7133[0])
[   20.008796] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   20.024096] tda829x 0-0042: setting tuner address to 60
[   20.190535] intel8x0_measure_ac97_clock: measured 108747 usecs (5222 samples)
[   20.190546] intel8x0: clocking to 48000
[   20.320184] tda18271 0-0060: creating new instance
[   20.404124] TDA18271HD/C2 detected @ 0-0060
[   20.580515] RPC: Registered udp transport module.
[   20.580527] RPC: Registered tcp transport module.
[   20.580533] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   21.331598] Slow work thread pool: Starting up
[   21.343793] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   21.352968] Slow work thread pool: Ready
[   21.353258] FS-Cache: Loaded
[   21.891319] zd1211rw 1-1.1:1.0: firmware version 4725
[   21.948595] zd1211rw 1-1.1:1.0: zd1211b chip 050d:705c v4810 full 00-22-75 AL2230_RF pa0 g--NS
[   21.951602] cfg80211: Calling CRDA for country: US
[   21.985515] cfg80211: Regulatory domain changed to country: US
[   21.985530]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.985539]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.985548]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   21.985556]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.985564]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.985572]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.985580]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   21.989721] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   22.246032] FS-Cache: Netfs 'nfs' registered for caching
[   22.393153] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   22.393357] type=1400 audit(1281461255.227:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=508 comm="apparmor_parser"
[   22.394054] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   22.394176] type=1400 audit(1281461255.227:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=508 comm="apparmor_parser"
[   22.394567] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   22.394678] type=1400 audit(1281461255.227:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=508 comm="apparmor_parser"
[   22.430077] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   22.430248] type=1400 audit(1281461255.263:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=785 comm="apparmor_parser"
[   22.452295] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.452323] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.455918] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
[   22.487010] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   22.487163] type=1400 audit(1281461255.319:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=770 comm="apparmor_parser"
[   22.586924] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   22.824073] tda18271: performing RF tracking filter calibration
[   23.051888] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   23.052202] type=1400 audit(1281461255.887:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=789 comm="apparmor_parser"
[   23.053542] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   23.053662] type=1400 audit(1281461255.887:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=789 comm="apparmor_parser"
[   23.053982] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   23.054081] type=1400 audit(1281461255.887:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=789 comm="apparmor_parser"
[   23.079223] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   23.081064] type=1400 audit(1281461255.915:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=795 comm="apparmor_parser"
[   23.101465] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   23.102442] type=1400 audit(1281461255.935:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=795 comm="apparmor_parser"
[   23.114567] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   24.584978] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   24.586172] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   24.599466] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   24.606099] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   24.612972] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   24.620140] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   25.342791] AppArmor DFA next/check upper bounds error fixed, upgrade user space tools 
[   25.599196] svc: failed to register lockdv1 RPC service (errno 97).
[   25.602777] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   25.612272] NFSD: starting 90-second grace period
[   32.016040] eth0: no IPv6 routers present
[   53.536057] tda18271: RF tracking filter calibration complete
[   53.664064] tda829x 0-0042: type set to tda8295+18271
[   58.648639] saa7133[0]: registered device video0 [v4l2]
[   58.648957] saa7133[0]: registered device vbi0
[   58.649295] saa7133[0]: registered device radio0
[   58.692466] saa7134 ALSA driver for DMA sound loaded
[   58.692566] saa7133[0]/alsa: saa7133[0] at 0xdf001000 irq 5 registered as card -2
[   63.739885] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   63.739919] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   63.739955] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
 
```

---

### Post by neosrix on 2010-08-14
Here is some root cause analysis, why the audio is not working. 

After installing the 2.6.35 kernel, there is no OSS (open sound standard) devices like mixer dsp . ie /dev/mixer and /dev/dsp are not created. Actually OSS is deprecated. ALSA is emulating these devices so the OSS compatible applications can be run without any problem. tvtime audio tries to open the /dev/mixer device and fails. 

A little more analysis reveals the /dev/sndstat is symlinked to a file that doesn't exist. and it boils down to the fact the modules snd_seq_oss, snd_pcm_oss, snd_mixer_oss are not loaded. 

Need to find out how to load them. Wondering is this a bug in 2.6.35 kernel. Any help?

---

### Post by dtspl on 2010-08-25
I am working on the same problem, any luck going forward ??

---

### Post by Hellus on 2010-08-25
[LEFT]This week I have been hanging around with a problem with the Aver Media Super 007,.... Okay, now is that is not yours, but dmsg is very similar, and in that situation I was blocked several days, until they told me to try the following...
     In my travels around the tv tuner I have come to many parts, like any good sailor, but some sites have been interesting, here I leave a short summary of your hardware:
      *Based on an IP developed for  cable modems, the TDA8275 implements the RSSI function, which is a  fast measurement system of a selected channel. This function allows, by S/W control, a fast scanning of the whole TV band, an automatic selection  of a given input power and the elimination of poor or far away transmitters. •  Unwanted channels will be then blanked to blue screen. Thus the installation  process can be drastically shortened (an advantage for portable notebook  based applications). *
   
*The second is a full reference design for PCI card manufacturers.  It combines the TDA8275 and TDA8290 with the SAA7133 video decoder  and PCI bridge IC. This full chipset and reference design allows PCI card manufacturers to go rapidly to market with a single ultra competitive card  able to cope with all analogue TV standards .*
 With what we came to the conclusion you have:
 >>video decoder and IF demodulator (saa7133)
 The firmware is the:
  dvb-fe-tda10045.fw  
 >> and *Single tuner hybrid PCI card reference board Features TDA18271*
 *The firmware is the:*
 *dvb-fe-tda10048-1.0.fw * 
 so you should install these two firmwares, but I think the first you've got it because:
  [   18.651542] saa7130/34: v4l2 driver version 0.2.16 loaded
 Anyway, if you're looking for, use google 'm not having any link to hand, and reinstall the two do not think anything happens. Now for the installation procedure:
 go to the downloads folder:
/home/name/Downloads
 
Then copy:
 Copy the resulting file ( dvb-fe-tda10046.fw ) to /lib/firmware

**sudo cp dvb-fe-tda10045.fw /lib/firmware  **(10046 & 1004)

 Restart the computer

# modprobe saa7133 'ERROR: Module saa7133 is in use by saa7133_alsa,saa7133_dvb '

 used kaffeine
Television-Channel-Start exploration and loads perfectly channels

************* And that's all folks .... good if it helps will be my first good action in linux ... if not ... know that the road will be hard ... but stiffer so my knowledge. A greetings from Spain.;)
 [/LEFT]

---

### Post by neosrix on 2010-09-06
Thank you Hellus for your suggestions.

Unfortunately, My Avermedia card is a analog card and doesn't support DVB. So I guess, that installing DVB firmware might not help me.

I have decided not to waste more time on cracking why the audio is not working, and wait for the official Ubuntu 10.10 with 2.6.35 kernel to be released and hope that they fix it :)

---

### Post by dtspl on 2010-11-08
Hi, I tried with the new Ubuntu, but still no sound ! Any luck at your end, you would like to share ??

---

### Post by neelugaddam on 2010-11-12
I don't know how to get the sound in ubuntu. But got the sound when I execute the following command as root in opensuse:

pactl  load-module module-loopback

Actually I made my tuner to work by using this thread. Thanks for the help.

---

### Post by bkkdaya on 2011-01-01
> **neelugaddam said:**
> I don't know how to get the sound in ubuntu. But got the sound when I execute the following command as root in opensuse:

pactl  load-module module-loopback

Actually I made my tuner to work by using this thread. Thanks for the help.

Thanks Thanks Thanks  =D>. The same is working with Mint 10.

---

### Post by manmath on 2011-04-18
I did, but the result is:

msahu-OptiPlex-360 msahu # pactl load-module module-loopback
Connection failure: Connection refused

What to do in this case?

---

### Post by Shivamd on 2011-08-04
[B] i am using ubuntu 11 ,plese rply me how to set Avermedia AvertV Super 009 tv tuner card on it.
[/B]

---

### Post by yusufbolu on 2012-02-28
I have Avermedia 009. There is no problem with channel scan but there is no sound. When I start Tvtime from terminal with:
```
tvtime | arecord -D hw:1,0 -f S16_LE -c2 -r32000 | aplay -
```
then the sound comes.
P.s. I found the command from another forum.

---

