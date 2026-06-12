---
title: "USB intermittent WiFi problems"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by legatolemans on 2011-10-25
I have a USB WiFi dongle that works sporadically, usually after I reboot the computer and have to unplug/replug the device a few times.

I have run the following terminal commands:

lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
sudo iwilist scan


But don't know how to decipher them.  If someone could help me understand this and make the wifi connection more reliable, it would be much appreciated.

Here are the results:

lspci -nnk | grep -iA2 net
```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)  
     Subsystem: ASRock Incorporation Device [1849:8136]  
     Kernel driver in use: r8169  
 
```lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter  
 Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305  
 Bus 003 Device 002: ID 047b:0011 Silitek Corp.
 
```lsmod
```

Module                  Size  Used by  
 bnep                   18436  2  
 rfcomm                 47946  0  
 bluetooth             166112  10 bnep,rfcomm  
 arc4                   12529  2  
 snd_hda_codec_realtek   330769  1  
 joydev                 17693  0  
 snd_hda_intel          33390  2  
 snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13668  1 snd_hda_codec  
 ppdev                  17113  0  
 snd_pcm                96755  2 snd_hda_intel,snd_hda_codec  
 binfmt_misc            17540  1  
 snd_seq_midi           13324  0  
 snd_rawmidi            30547  1 snd_seq_midi  
 rtl8187                57035  0  
 mac80211              310872  1 rtl8187 
 cfg80211              199587  2 rtl8187,mac80211  
 usbhid                 47198  0  
 snd_seq_midi_event     14899  1 snd_seq_midi  
 hid                    95463  1 usbhid  
 eeprom_93cx6           12725  1 rtl8187 
 psmouse                73882  0  
 snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event  
 snd_timer              29991  2 snd_pcm,snd_seq  
 snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq  
 serio_raw              13166  0  
 snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 parport_pc             36962  1  
 i915                  566711  3  
 soundcore              12680  1 snd  
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm  
 drm_kms_helper         42558  1 i915  
 drm                   236330  4 i915,drm_kms_helper  
 i2c_algo_bit           13423  1 i915  
 video                  19412  1 i915  
 lp                     17799  0  
 parport                46562  3 ppdev,parport_pc,lp  
 r8169                  52788  0

```rfkill list
```
1: phy1: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no
 
```iwconfig
```
lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:"Home"   
           Mode:Managed  Frequency:2.417 GHz  Access Point: 00:24:B2:11:29:FE    
           Bit Rate=54 Mb/s   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=56/70  Signal level=-54 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:60   Missed beacon:0
 
```sudo iwlist scan
```
lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.

```

---

### Post by legatolemans on 2011-10-25
I'm running Ubuntu 11.10 64-bit, if that makes any difference.

---

