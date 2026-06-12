---
title: "Ethernet works but not wifi -- Help!"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by terenceleejx on 2013-05-23
Hi I've just recently installed Ubuntu on my Windows 8 laptop and while I have no problems with the ethernet connection, the wireless feature does not seem to be able to detect any signals. I've searched the forums and realized many have faced similar issues before. While I've tried all available suggestions, my wifi still doesn't seem to be working :(

Here's some info about what's happening:

terence@terence-ubuntu:~$ iwconfig
eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

terence@terence-ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
Linux terence-ubuntu 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
terence@terence-ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:2126]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: alx

terence@terence-ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0458:00fe KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 003: ID 05ac:1297 Apple, Inc. iPhone 4
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:3402 IMC Networks 
Bus 001 Device 004: ID 1bcf:2883 Sunplus Innovation Technology Inc. 
Bus 001 Device 006: ID 03eb:8807 Atmel Corp. 

terence@terence-ubuntu:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

terence@terence-ubuntu:~$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  12 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_via      51018  1 
ipheth                 13448  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
asus_nb_wmi            12854  0 
asus_wmi               24213  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
joydev                 17377  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
microcode              22881  0 
hid_multitouch         17366  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
arc4                   12615  2 
wmi                    19070  1 asus_wmi
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
mac_hid                13205  0 
i915                  600351  3 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
video                  19390  2 i915,asus_wmi
drm_kms_helper         49394  1 i915
cfg80211              510937  3 ath,ath9k,mac80211
drm                   286313  4 i915,drm_kms_helper
psmouse                95870  0 
serio_raw              13215  0 
alx                    67960  0 
btusb                  22474  0 
mei                    41158  0 
bluetooth             228619  22 bnep,btusb,rfcomm
mdio                   13807  1 alx
i2c_algo_bit           13413  1 i915
lpc_ich                17061  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  1 hid_multitouch
hid                   101002  3 hid_multitouch,hid_generic,usbhid
ahci                   25731  3 
libahci                31364  1 ahci

---

