---
title: "ATHEROS AR9285 WLAN not working with LENOVO B570 (with ubuntu 12.04)"
date: 2012-12-24
forum: Networking &amp; Wireless
---

### Post by bvrabete on 2012-12-24
Hi there,

The HW switch for the wireless card in my Lenovo B570 laptop keeps switching off for unknown reasons. Until now I was able to fix the issue by blacklisting acer_wmi module but it no longer helps.

The laptop does not have a physical switch for Wireless, just the Fn+F5 combination. That gets recognized by Ubuntu but has only effect on the software switch.

I have also tried the power button suggestion (remove battery and keep power button pressed for more than 30s) but no luck.

 ```
lspci -nn|grep Ather
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```

```
iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

```
lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:50:46:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-35-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0500000-d050ffff

```

```
lsmod 
Module                  Size  Used by
wmi                    18744  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
microcode              18187  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
rfcomm                 38139  0 
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
bnep                   17830  2 
snd_seq_midi           13132  0 
bluetooth             158479  10 rfcomm,bnep
snd_rawmidi            25424  1 snd_seq_midi
parport_pc             32114  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
rts5139               279659  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
ath9k                 117356  0 
mac80211              436493  1 ath9k
psmouse                86520  0 
ath9k_common           13781  1 ath9k
ath9k_hw              391591  2 ath9k,ath9k_common
serio_raw              13027  0 
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178877  3 ath9k,mac80211,ath
ideapad_laptop         17890  0 
binfmt_misc            17292  1 
sparse_keymap          13658  1 ideapad_laptop
i915                  419297  3 
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
mei                    36570  0 
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0
```

```

rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

---

