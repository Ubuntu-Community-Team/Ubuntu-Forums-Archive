---
title: "slow wireless"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by mailc on 2012-07-21
A Samsung laptop came with 4 logigal partitions : boot, Windows1, Windows 2,  and Reinstallation. I deleted the first 3 partitions and installed Ubuntu 12.04 ver 32. which worked fine for a while but soon it became very slow and the mouse was not responding well. I thought that must have made some error and deleted the ver 32 and installed Precise 64 bit

But again, it became slow and he mouse can hardly be used (touchpad works however).

I remember that at installation the suggestion was for a wireless driver and its update. But it did now download for me.  So I installed b43 .

Any help appreciated

---

### Post by mailc on 2012-07-21
```

**cat /etc/lsb-release; uname -a**

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux xxxx  3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

**lspci -nnk | grep -iA2 net**

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c624]
    Kernel driver in use: r8169
--
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4101]
    Kernel driver in use: ath9k

**lsusb**

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 002 Device 002: ID 2232:1020

**iwconfig**

lo        no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:"AirLink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:969  Invalid misc:46   Missed beacon:0
eth0      no wireless extensions.

**rfkill list all**

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**lsmod**

~$ lsmod
Module                  Size  Used by
bnep                   18281  2 
parport_pc             32866  0 
vesafb                 13844  1 
rfcomm                 47604  0 
ppdev                  17113  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_realtek   223867  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
ath9k                 132390  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17693  0 
v4l2_compat_ioctl32    17128  1 videodev
fglrx                3263886  114 
mac80211              506816  1 ath9k
i2c_piix4              13301  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
snd                    78855  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19596  0 
lp                     17799  0 
soundcore              15091  1 snd
parport                46562  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k10temp                13166  0 
cfg80211              205544  3 ath9k,mac80211,ath
psmouse                87692  0 
serio_raw              13211  0 
mac_hid                13253  0 
usbhid                 47199  0 
hid                    99559  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci




```

---

### Post by wildmanne39 on 2012-07-21
Hi, copy and paste the following commands for accuracy:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
does that help?
Thanks

---

### Post by mailc on 2012-07-22
Thanks [[COLOR=#DD4814]**wildmanne39**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533") ,

that certainly helped .

You are the best!

---

