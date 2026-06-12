---
title: "Wireless Card not working in Ubuntu 10.10"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by openfoam on 2011-03-05
Hi, 
I installed Ubuntu 10.10 on my Dell Inspiron 1525 (Vista Home Basic) using Wubi easy installer. Everything is perfect except for internet. It doesnt connect. My wireless card is Dell Wireless 1395 WLAN Mini-Card and the ethernet controller is Marvell Yukon 88E8040 PCI-E. I have used the commands: lshw, lsmod, iwconfig, rfkill list; to get an idea of the problem. The results of these commands are shown below if u need to refer to them. How should I get around this problem?

THANK YOU,
SAVINDU 

******//"sudo lshw -C network" returns,//********
"*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e8:1c:66
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:69:94:b9:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

*********//"sudo lsmod" returns,//************
"Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_idt      64667  1 
snd_hda_codec_intelhdmi    11032  1 
rfcomm                 40755  4 
binfmt_misc             7984  1 
sco                     9954  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
joydev                 11363  0 
arc4                    1497  2 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
i915                  330089  3 
b43                   187931  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              266657  1 b43
drm_kms_helper         32836  1 i915
uvcvideo               62379  0 
btusb                  12929  2 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12646  1 videodev
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              170293  2 b43,mac80211
dell_laptop             6722  0 
dell_wmi                3372  0 
bluetooth              59213  9 rfcomm,sco,bnep,l2cap,btusb
r852                   11348  0 
sm_common               4441  1 r852
nand                   38430  2 r852,sm_common
nand_ids                4443  1 nand
nand_ecc                4406  1 nand
dcdbas                  6910  1 dell_laptop
mtd                    21479  2 sm_common,nand
drm                   206161  4 i915,drm_kms_helper
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
output                  2527  1 video
intel_agp              32080  2 i915
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   21857  0 
firewire_ohci          24679  0 
sky2                   53371  0 
firewire_core          54327  1 firewire_ohci
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  2 b43,sdhci
libahci                26167  2 ahci
ssb                    46169  1 b43
crc_itu_t               1739  1 firewire_core"

*******//"sudo iwconfig" returns,//**********
"lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off"

**********//"rfkill list" returns,//***************
"0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no"

---

