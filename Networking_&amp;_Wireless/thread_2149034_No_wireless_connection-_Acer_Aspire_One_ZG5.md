---
title: "No wireless connection- Acer Aspire One ZG5"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2013-05-27
I'm running Ubuntu 10.04 netbook on a Acer Aspire One ZG5. It's a new clean installation.(yes, I know 10.04 is out of date).

The wireless connection isn't working.  Ethernet works fine.

Below is the output of the commands;


lspci -nnk | grep -iA2 net lsusb lsmod iwconfig rfkill list


```
$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k
welcome@welcome-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
welcome@welcome-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6523  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203472  1 
fbcon                  35102  72 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_intel          22069  2 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 122927  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              225491  1 ath5k
joydev                  8740  0 
ath                     8041  1 ath5k
i915                  290772  4 
usbhid                 36110  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57438  0 
cfg80211              144682  3 ath5k,mac80211,ath
drm_kms_helper         29329  1 i915
hid                    67288  1 usbhid
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24375  2 i915
psmouse                63677  0 
serio_raw               3978  0 
led_class               2864  1 ath5k
drm                   163779  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
output                  1871  1 video
lp                      7060  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
welcome@welcome-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
welcome@welcome-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```


Any ideas how to fix this?

---

### Post by PDA1 on 2013-05-27
When the computer is shut down, the battery removed, then replaced, and  re-booted the wireless icon shows that the computer is connected to the  wireless net work. But, Firefox says the the computer isn't  connected....and no web page loads.

Here's the report from the commands;


lspci -nnk | grep -iA2 net lsusb lsmod iwconfig rfkill list




```
$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k
welcome@welcome-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
welcome@welcome-laptop:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_conntrack           61615  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc             6523  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203472  1 
arc4                    1153  2 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
joydev                  8740  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 122927  0 
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  290772  4 
uvcvideo               57438  0 
usbhid                 36110  0 
mac80211              225491  1 ath5k
ath                     8041  1 ath5k
drm_kms_helper         29329  1 i915
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
hid                    67288  1 usbhid
intel_agp              24375  2 i915
soundcore               6620  1 snd
cfg80211              144682  3 ath5k,mac80211,ath
psmouse                63677  0 
serio_raw               3978  0 
drm                   163779  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
led_class               2864  1 ath5k
agpgart                31724  2 intel_agp,drm
output                  1871  1 video
lp                      7060  0 
parport                32635  2 ppdev,lp
r8169                  34140  0 
mii                     4381  1 r8169
welcome@welcome-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"PA7V5"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:90:BA:C3:9C   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

welcome@welcome-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

