---
title: "ew-7728in pci wireless slow connection, Ubuntu 12.04"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by richterbg on 2013-02-08
I have the Edimax ew-7728in pci wireless module installed in my pc. It works, it is stable, but the connection is slow. I know this card is a beast, yet the download speed is 600-700Kb/s max. I'm testing this with a popular local torrent site. When I'm using an alternative USB wireless card (Atheros chipset), the download speed goes up to 5MB/s. 

Now, Google shows that the chipset for Edimax card is RT2860. The loaded module in the kernel is rt2800pci:

```
>lsmod
Module                  Size  Used by
vesafb                 13844  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
nvidia              11283521  42 
edac_core              53746  0 
k8temp                 13057  0 
serio_raw              13211  0 
edac_mce_amd           23709  0 
uvcvideo               72627  0 
snd_usb_audio         122982  1 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hda_codec_realtek   224173  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  2 snd_usb_audio,snd_hda_codec
snd_pcm                97275  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ppdev                  17113  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
**rt2800pci              18715  0** 
snd_timer              29990  2 snd_pcm,snd_seq
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              55326  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              205774  2 rt2x00lib,mac80211
snd                    79041  19 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6           12767  1 rt2800pci
soundcore              15091  1 snd
i2c_nforce2            13058  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             32866  1 
joydev                 17693  0 
usblp                  18307  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
floppy                 70207  0 
forcedeth              63460  0 
pata_amd               14118  0 
sata_nv                32286  4 

```

```
>lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Giga-byte Technology Device [1458:e000]
	Kernel driver in use: forcedeth
--
01:07.0 Network controller [0280]: **Ralink corp. RT2800 802.11n PCI** [1814:0601]
	Subsystem: Ralink corp. **Device [1814:2860]**
	Kernel driver in use: rt2800pci
```

So, what are my options here to make this card work faster? I'm not quite an experienced user, so, most likely I would need step-by-step instructions. 

Any help would be welcome.

---

