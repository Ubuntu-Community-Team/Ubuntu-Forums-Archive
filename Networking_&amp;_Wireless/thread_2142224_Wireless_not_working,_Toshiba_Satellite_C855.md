---
title: "Wireless not working, Toshiba Satellite C855"
date: 2013-05-05
forum: Networking &amp; Wireless
---

### Post by PunchALunch on 2013-05-05
All the info you may need.

Toshiba Satellite c855, Linux Ubuntu 11.10

$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211]
    Kernel driver in use: rtl8192ce
dillon@dillon-Satellite-C855:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a43 Importek 
dillon@dillon-Satellite-C855:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166150  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330815  1 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_intel          33390  2 
snd_hda_codec         104968  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96756  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
rtl8192ce              84775  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               110972  1 rtl8192ce
mac80211              462046  3 rtl8192ce,rtl8192c_common,rtlwifi
i915                  575577  3 
uvcvideo               72711  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               93004  1 uvcvideo
psmouse                73882  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
v4l2_compat_ioctl32    17083  1 videodev
serio_raw              13166  0 
video                  19652  1 i915
lp                     17799  0 
snd                    68452  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199630  2 rtlwifi,mac80211
rts5139               351143  0 
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               87235  0 
dillon@dillon-Satellite-C855:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dillon@dillon-Satellite-C855:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"4RDXD"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:63:5D:D4:6F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by praseodym on 2013-05-05
Hi,

you know that 11.10 is outdated? I recommend an Upgrade/Installation of 12.04 or newer.

Please show:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
sudo iwlist scan
```

---

