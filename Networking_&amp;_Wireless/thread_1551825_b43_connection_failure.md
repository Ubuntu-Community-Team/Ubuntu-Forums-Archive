---
title: "b43 connection failure"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by snif123 on 2010-08-12
Hi all
I have UBU lucid,after long batte I managed to get b43 driver to work with my bcm4312 card ID4315.I had STA driver before but now its the b43 driver.I connected to internet with it several times and then rebooted and not I can't connect anymore.It detects networks and connects but starting firefox then doesnt load and finally wfi disconnects.This problem started when I turned the card to Monitor MODE.Any help would be much appreciated
Lsmd:
Module                  Size  Used by
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      51978  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
joydev                  8708  0 
b43                   163523  0 
ssb                    38671  1 b43
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              205146  3 rt2x00usb,rt2x00lib,b43
i915                  285076  3 
drm_kms_helper         29297  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              126517  3 rt2x00lib,b43,mac80211
dell_wmi                1793  0 
led_class               2864  2 rt2x00lib,b43
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915

lswh  -C network
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:2f:2f:8a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:24:2c:09:4a:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

