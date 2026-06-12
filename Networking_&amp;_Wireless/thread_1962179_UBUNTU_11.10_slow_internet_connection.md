---
title: "UBUNTU 11.10 slow internet connection"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by johnnykaram on 2012-04-20
I have recently installed ubuntu 11.10 on y lenovo desktop. The internet connection is much slower than when I browse on my mac. I have read other threads and tried to solve it the same way however it did not work. I would appreciate if anyone could help me. Thank you in advance.

---

### Post by wildmanne39 on 2012-04-20
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by johnnykaram on 2012-04-21
#johnnykaram@johnnykaram-Lenovo:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux johnnykaram-Lenovo 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
johnnykaram@johnnykaram-Lenovo:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82578DC Gigabit Network Connection [8086:10f0] (rev 06)
	Subsystem: Lenovo Device [17aa:3604]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176]
	Kernel driver in use: rtl8192ce
johnnykaram@johnnykaram-Lenovo:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c06a Logitech, Inc. 
Bus 002 Device 005: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 002 Device 004: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
johnnykaram@johnnykaram-Lenovo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"L.F.P.U"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:10:B8:F6:D4   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

johnnykaram@johnnykaram-Lenovo:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
johnnykaram@johnnykaram-Lenovo:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
parport_pc             36962  0 
ppdev                  17113  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
usb_storage            57901  1 
uas                    18027  0 
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               110972  1 rtl8192ce
mac80211              310872  3 rtl8192ce,rtl8192c_common,rtlwifi
radeon               1015995  3 
mei                    41480  0 
cfg80211              199587  2 rtlwifi,mac80211
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
e1000e                160535  0 
johnnykaram@johnnykaram-Lenovo:~$



--Thank you a lot!

---

### Post by wildmanne39 on 2012-04-21
Hi, I assume it is your wireless connection that is slow.

Set your wireless settings to match the screenshots then please do:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```

A new empty file will open, paste this one line into the file.

```
options rtl8192ce swenc=1
```

Proofread, save and close gedit, then reboot.
Thanks

---

### Post by qichuan on 2012-04-26
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux bai 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
bai@bai:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137d]
    Kernel driver in use: wl
--
06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Lenovo Device [17aa:3861]
    Kernel driver in use: tg3
bai@bai:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
bai@bai:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:194  Noise level:199
          Rx invalid nwid:0  invalid crypt:4897  invalid misc:0

bai@bai:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
bai@bai:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254163  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
r592                   17808  0 
psmouse                73673  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
serio_raw              12990  0 
snd_seq_midi           13132  0 
mtd                    35852  2 sm_common,nand
memstick               15857  1 r592
snd_rawmidi            25241  1 snd_seq_midi
lib80211_crypt_tkip    17240  0 
ideapad_laptop         13575  0 
wl                   2646601  0 
sparse_keymap          13658  1 ideapad_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  509519  3 
lib80211               14570  2 lib80211_crypt_tkip,wl
drm_kms_helper         32889  1 i915
snd                    55902  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   132972  0 


```

---

### Post by qichuan on 2012-04-26
I jumped from 10.04 to 11.04 , 11.10 in 2 weeks, 11.04 is fine, but 11.10 is killing me. I somehow fixed the slow internet one day. But today when I tried to update to 12.04, and cancelled due to long time waiting, I went back to the first place. Any youtube/pandora thing doesn't work. I tried traceroute, which shows also slow connection. I changed from Unity 2D to Gnome Shell, still slow. So thank you very much if you can help me..... what did I do last time? I guess upgrade to 12.04 I would face the same problem, even worse, I now need many hours to finish the upgrading~~

---

### Post by wildmanne39 on 2012-04-26
Hi, first you never upgrade using a wireless connection, also it is better to back up your important data and do a clean install.

From what I see you do not have a wireless connection at all right now I recommend this driver instead of the one you are using.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
unplug wired connection and reboot.
Thanks

---

