---
title: "Broadcom 4303 not connecting"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by Fenix-TX on 2011-10-16
Hello, i have an older computer from my father (HP Pavilion zv5168ea) and i decided to install a Xubuntu distro (tried 11.10, now 11.04) for my personal use, but i can't get a wireless connection to my router (i'm using WPA-personal encryption but tried with open and nothing). The driver is installed, i can see wifi essid but the connection is never carried out. I've installed firmware-b43legacy-installer because it has the driver for this card but nothing...

This is the output of lspci -vnn (only wireless card part)
```

02:02.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:12f3]
	Flags: bus master, fast devsel, latency 64, IRQ 11
	Memory at e0104000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

```

This rfkill list output:
```
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

And finally lsmod:
```
Module                  Size  Used by
b43legacy             127415  0 
ssb                    45942  1 b43legacy
mac80211              257001  1 b43legacy
cfg80211              156212  2 b43legacy,mac80211
snd_intel8x0           33213  3 
arc4                   12473  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
nouveau               621970  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39671  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 nouveau
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 nouveau,ttm,drm_kms_helper
yenta_socket           27230  0 
ppdev                  12849  0 
joydev                 17322  0 
pcmcia_rsrc            18292  1 yenta_socket
i2c_algo_bit           13184  1 nouveau
snd                    55295  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
k8temp                 12872  0 
psmouse                73312  0 
shpchp                 32345  0 
serio_raw              12990  0 
parport_pc             32111  1 
video                  18951  1 nouveau
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
8139too                23208  0 
8139cp                 22497  0 
pata_amd               13762  2 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
```

Forgot to put dmesg output:
```
[ 1491.019304] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 11 (level, low) -> IRQ 11
[ 1491.086827] b43legacy-phy0: Broadcom 4301 WLAN found
[ 1491.108067] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[ 1491.108093] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[ 1491.132056] b43legacy-phy0 debug: Radio initialized
[ 1491.432090] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[ 1491.556324] b43legacy-phy0 debug: Chip initialized
[ 1491.556589] b43legacy-phy0 debug: 30-bit DMA initialized
[ 1491.558904] Registered led device: b43legacy-phy0::tx
[ 1491.558943] Registered led device: b43legacy-phy0::rx
[ 1491.558975] Registered led device: b43legacy-phy0::radio
[ 1491.559001] b43legacy-phy0 debug: Wireless interface started
[ 1491.564107] b43legacy-phy0 debug: Adding Interface type 2
[ 1555.492498] wlan0: direct probe to 20:cf:30:ce:0e:c7 (try 1/3)
[ 1555.692058] wlan0: direct probe to 20:cf:30:ce:0e:c7 (try 2/3)
[ 1555.892059] wlan0: direct probe to 20:cf:30:ce:0e:c7 (try 3/3)
[ 1556.092059] wlan0: direct probe to 20:cf:30:ce:0e:c7 timed out
[ 1882.024387] b43legacy-phy0 warning: Unexpected value for chanstat (0xC00)
```
Any suggestion? Thanks in advance.

---

