---
title: "intel link wifi 5100 connection issues"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by XtachiX on 2012-05-14
hello there, i'm new to this site
i have done my fair amount of research regarding my topic
even tried [this solution]("http://ubuntuforums.org/showthread.php?t=1970820")
```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:ba:75:38:c9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.1.105 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:d5700000-d5703fff ioport:4000(size=256)
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:61:69:36
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=8.83.5.1 build 33692 ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:d4600000-d4601fff
``````
dmesg | grep iwl
[  183.223215] iwlwifi 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  183.223225] iwlwifi 0000:03:00.0: setting latency timer to 64
[  183.223258] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[  183.223260] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900050f8000
[  183.223263] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[  183.223349] iwlwifi 0000:03:00.0: irq 47 for MSI/MSI-X
[  183.223402] iwlwifi 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[  183.223464] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  183.245536] iwlwifi 0000:03:00.0: device EEPROM VER=0x11f, CALIB=0x4
[  183.245540] iwlwifi 0000:03:00.0: Device SKU: 0Xf0
[  183.245921] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  183.258085] iwlwifi 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[  183.264424] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  183.277979] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  183.281012] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  183.397266] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  183.400316] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  192.850440] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 00:0c:f6:64:d8:0d tid = 0

``````
rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


I'm stuck, the wifi is connected to my router, but i cannot access the Internet
i cannot browse the internet, or download any updates, i have to use the cable
the wifi card works in my windows 7
i'm using ubuntu 12.04 64bit

let me know if you need any other information

---

### Post by praseodym on 2012-05-14
Hi,

remove ndiswrapper completely, if you tried it:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
The driver iwlwifi got a bug with the N-mode, deactivate it via:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Check:
```
iwconfig
lsmod
dmesg | grep iwl
sudo iwlist scan
```
What computer is that?

---

### Post by XtachiX on 2012-05-15
laptop model sony vaio VGN-CS320J

here are the outputs
```
 sudo modprobe -v iwlwifi
insmod /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n disable=1
FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
``````
lsmod
Module                  Size  Used by
btusb                  18288  0 
bluetooth             180104  1 btusb
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
r592                   18144  0 
psmouse                87603  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_timer              29990  2 snd_pcm,snd_seq
serio_raw              13211  0 
memstick               16569  1 r592
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            45393  0 
i915                  468651  3 
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k                 132390  0 
drm_kms_helper         46978  1 i915
mac80211              506816  1 ath9k
drm                   242038  4 i915,drm_kms_helper
mac_hid                13253  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
soundcore              15091  1 snd
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
i2c_algo_bit           13423  1 i915
cfg80211              205544  3 ath9k,mac80211,ath
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          41000  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   59043  0 
``````
dmesg | grep iwl
[  260.670252] iwlwifi: Unknown parameter `11n'
[  283.558588] iwlwifi: Unknown parameter `11n'
[  471.073679] iwlwifi: Unknown parameter `11n'
[  490.712445] iwlwifi: Unknown parameter `11n'
[  503.300816] iwlwifi: Unknown parameter `11n'

``````
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```my wifi now disappeared
any ideas?



EDIT: just did a fresh re-install and followed your instructions along with the earlier link i provided in the first post
everything seems to be working like a charm, 
thank you very much

---

### Post by praseodym on 2012-05-15
:guitar:Great

---

### Post by simonbr1970 on 2012-05-17
I was having same problem with this the intel 5100 on Ubuntu 12.04.
Tried this and worked for me as well :P Chuffed

---

### Post by weclark on 2012-10-21
[QUOTE=praseodym;11936019]Hi,


The driver iwlwifi got a bug with the N-mode, deactivate it via:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

This fixed the issue for me! Thanks!
Ubuntu 12.04.1 LTS 64bit, HP laptop w/Intel 5100 AGN

---

### Post by Skullsworth on 2013-01-09
It'll take me a few months to figure out what you just had me do, but I know it fixed my issue.  Thank you.

---

