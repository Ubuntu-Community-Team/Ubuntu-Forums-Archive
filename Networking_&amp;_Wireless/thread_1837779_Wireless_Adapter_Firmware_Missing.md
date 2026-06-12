---
title: "Wireless Adapter Firmware Missing"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by skyline131313 on 2011-09-02
So I've been following a guide to get my wireless adapter to work, I am able to see my adapter but I still can't use it. The guide mentions something about System -> Administration -> Networking, but there isn't anything like that, there is Network Tools but it doesn't seem like that is it.

On the panel where I can view all the networks, it says "device not ready (firmware is missing)". The adapter I am using is the Linksys WMP300N.

This is the guide: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#Give_your_system_a_kick](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#Give_your_system_a_kick).

Thanks for any help.

---

### Post by praseodym on 2011-09-02
Hi,

do you use Ubuntu-Studio 11.04? This works per default with the tool **gnome-network-admin** instead of the **network-manager**. Do you have a wired connection? Then you can install the network-manager via

```
sudo apt-get install --reinstall network-manager network-manager-gnome
```
Please show the following outputs from the terminal:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep ath
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by skyline131313 on 2011-09-02
```
Linux desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

```
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:2a5a]
	Kernel driver in use: forcedeth
--
01:05.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
	Subsystem: Linksys Device [1737:0060]
	Kernel driver in use: b43-pci-bridge
```

```
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336693  1 
arc4                   12529  2 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
nouveau               682322  2 
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
b43                   318638  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
mac80211              294370  1 b43
binfmt_misc            17565  1 
ttm                    76664  1 nouveau
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         42136  1 nouveau
drm                   227495  4 nouveau,ttm,drm_kms_helper
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178528  2 b43,mac80211
psmouse                73535  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17606  0 
i2c_algo_bit           13400  1 nouveau
video                  19438  1 nouveau
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
ndiswrapper           249811  0 
soundcore              12680  1 snd
k8temp                 13016  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  1 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
usbhid                 46956  0 
hid                    91020  1 usbhid
uas                    17996  0 
ssb                    51945  1 b43
crc_itu_t              12707  1 firewire_core
pata_amd               14130  0 
forcedeth              63555  0 
sata_nv                32054  2 
```

```
[    0.800378] device-mapper: multipath: version 1.2.0 loaded
[    0.800381] device-mapper: multipath round-robin: version 1.0.0 loaded

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"masd"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

---

### Post by praseodym on 2011-09-02
Ok: First you have to uninstall ndiswrapper completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

Second: The driver b43 doesnt work with this device (imho), you have to install the "Broadcom-STA-driver" via "Additional drivers". If you want to try the missing firmware first, you can install it with:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by wildmanne39 on 2011-09-02
Hi, with 11.04 it is best to use the b43, the sta driver does not work in 11.04.

---

