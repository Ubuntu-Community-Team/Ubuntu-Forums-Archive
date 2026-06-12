---
title: "Asus G75VW no proprietary wireless driver in Ubuntu 12.10"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by cjhoward on 2013-02-14
I was able to successfully install Ubuntu 12.10 alongside Windows 8 on my Asus G75VW.  Everything on the Ubuntu side seems to be working **aside from the wireless driver**. There is no proprietary wireless driver listed in Software Sources. Wireless networks show up but none will connect (given correct password, SSID, security protocol, etc). The Unity wireless icon continually fades in and out like it's trying to connect, and using the ethernet jack is the only way to connect. After hard-wiring my internet connection, I was able to download and install updates but still no proprietary wireless driver.

Anyone else getting this same issue? I'm running Ubuntu 12.10 64-bit with the default graphics driver (non-Nvidia).

UPDATE: [This post]("http://ubuntuforums.org/showthread.php?p=12509635#post12509635") did not help, unfortunately.

---

### Post by praseodym on 2013-02-14
Hi,

please show the terminal (CTRL+ALT+T) outputs of these commands:
```

uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by cjhoward on 2013-02-14
Thanks for the quick response!  Here's the output for the requested terminal commands:

**uname -a**
Linux cjhoward-linux 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

**lspci -nnk**
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM77 Express Chipset LPC Controller [8086:1e57] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1213] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:2119]
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c] (rev a1)
	Subsystem: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave Device [1a3b:2c97]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1487]
	Kernel driver in use: atl1c
	Kernel modules: atl1c

**lsusb**
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 1bcf:2885 Sunplus Innovation Technology Inc.

**lsmod**
Module                  Size  Used by
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
joydev                 17458  0 
rfcomm                 46620  0 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
parport_pc             32689  0 
ppdev                  17074  0 
snd_hda_codec_hdmi     32049  4 
nls_iso8859_1          12714  1 
hid_logitech_dj        18605  0 
usbhid                 46987  1 hid_logitech_dj
hid                   100411  2 hid_logitech_dj,usbhid
nouveau               896008  4 
ttm                    83596  1 nouveau
drm_kms_helper         49113  1 nouveau
drm                   288721  6 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13414  1 nouveau
mxm_wmi                13022  1 nouveau
asus_nb_wmi            12711  0 
asus_wmi               24089  1 asus_nb_wmi
sparse_keymap          13891  1 asus_wmi
snd_hda_codec_via      46676  1 
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51038  1 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
microcode              22804  0 
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12530  2 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
psmouse                95595  0 
ath9k                 131355  0 
serio_raw              13216  0 
mac80211              539958  1 ath9k
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           14056  1 ath9k
ath9k_hw              395264  2 ath9k,ath9k_common
ath                    23828  3 ath9k,ath9k_common,ath9k_hw
lpc_ich                17062  0 
cfg80211              206797  3 ath9k,mac80211,ath
snd_timer              29426  2 snd_pcm,snd_seq
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer
mei                    40691  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
wmi                    19071  3 nouveau,mxm_wmi,asus_wmi
video                  19336  1 nouveau
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
atl1c                  41102  0

**iwconfig**
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Howard"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:76:00:57:D0:04   
          Bit Rate:52 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

**rfkill list**
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2013-02-14
Deactivate the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by cjhoward on 2013-02-14
Worked like a charm!  Thank you so much!

---

