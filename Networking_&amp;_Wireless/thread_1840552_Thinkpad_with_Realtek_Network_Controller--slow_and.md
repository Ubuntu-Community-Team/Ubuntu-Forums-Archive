---
title: "Thinkpad with Realtek Network Controller--slow and unstable wireless"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by fredlovecdl on 2011-09-07
Problem: I run a Thinkpad T410i under dual boot
with WIN7 and Ubuntu 11.04(2.6.38-11-generic x86_64
). Under WIN7 everything 
works fine, but under Ubuntu wireless connection 
is oftentimes slow and unstable.

I really appreciate any help!!

1. lspci -nn | grep "Wireless"
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)

2. iwconfig wlan0
wlan0     802.11bgn  ESSID:"tuftswireless"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:24:6C:C4:7F:20   
          Bit Rate=135 Mb/s   
          Retry: on   RTS thr: off   Fragment thr: off
          Power Management period:0us  mode:All packets received
          Link Quality=50/100  Signal level=-67 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

3. lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
i915                  515121  8 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72195  0 
r8192se_pci           524220  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         42136  1 i915
videodev               82052  1 uvcvideo
snd_timer              29602  2 snd_pcm,snd_seq
v4l2_compat_ioctl32    17078  1 videodev
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
intel_ips              18097  0 
drm                   227534  4 i915,drm_kms_helper
tpm_tis                18537  0 
cfg80211              178528  1 r8192se_pci
psmouse                73535  0 
serio_raw              13166  0 
thinkpad_acpi          81587  0 
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
tpm                    22267  1 tpm_tis
nvram                  14419  1 thinkpad_acpi
tpm_bios               13684  1 tpm
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
hid_a4tech             12678  0 
usbhid                 46956  0 
hid                    91020  2 hid_a4tech,usbhid
ahci                   25951  6 
libahci                26642  1 ahci
firewire_ohci          40370  0 
sdhci_pci              13989  0 
firewire_core          62646  1 firewire_ohci
e1000e                159096  0 
crc_itu_t              12707  1 firewire_core
sdhci                  27387  1 sdhci_pci

4. dmesg | grep "wlan"
[   20.269490] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.450648] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.073512] wlan0: no IPv6 routers present

5.iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:24:6C:C4:7F:20
                    ESSID:"tuftswireless"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:1
                    Encryption key: off
                    Bit Rates:130 Mb/s
                    Extra: Rates (Mb/s): 2 11 6 9 12 18 24 36 48 54 
                    Quality=70/100  Signal level=-67 dBm  Noise level=-105 dBm
                    Extra: Last beacon: 2ms ago

6.

---

### Post by praseodym on 2011-09-07
Do you really use no encryption? I recommend WPA2-AES encryption, otherwise the network-manager may have problems.

---

### Post by fredlovecdl on 2011-09-07
> **praseodym said:**
> Do you really use no encryption? I recommend WPA2-AES encryption, otherwise the network-manager may have problems.

Hi, 

Is it something I can set using the "edit connections"? There isn't
such an encryption option though.

---

### Post by wildmanne39 on 2011-09-07
Hi, you have to enter something like this 192.168.0.1 into your address bar of your browser to make any changes to your router settings.
Thank you

---

